# Voxgig - Junior Developer Relations Engineer: Application Questionnaire

> Reply by email, writing each answer beneath the relevant question. Paste plain, no markdown.

## 1. Developer events

Tell us about your personal experience organising, attending, promoting, or speaking at a developer event. What would you have done to improve the event?

**Answer:**

Last year I spoke at N-SIDE Connect 2025, the clinical-supply event my company runs for its customers in Belgium. I presented a session called "Leveraging APIs and system integrations to operationalise a supply chain strategy".

The audience was mixed: software engineers, but also managers, supply-chain experts and clinical coordinators. I designed the talk as an hourglass: open broad for the business stakeholders, narrow into the technical for the engineers, then widen back out to the ROI for the decision-makers.

Connecting the business and technical point of view was the real challenge. So rather than just saying "coordinators save four hours a week on data entry", I make the business connection out loud: "by removing four hours of data entry, coordinators can spend that time refining risk thresholds, preventing supply stockouts and cutting drug waste by 15%." One fact, bridged for both halves of the room.

Everyone knows what Excel looks like, so I showed a huge spreadsheet and then showed how it collapses into a small JSON payload a machine can process: technical for the developers, but still familiar for everyone else.

Q&A with a mixed audience is hard: I cannot control what people ask, and a technical question can lose the rest of the room. I set the ground rules up front (questions at the end, technical deep-dives after the session). For business or pricing questions, I never guess without the data; we had the relevant manager and a salesperson on hand for that.

If I ran it again, I would fix the one thing I actually missed: a formal, scheduled post-talk slot for the engineers to ask technical questions. Some of them came over informally afterwards, but that space should have been announced and planned. The best technical questions deserve a room where you can go deep.

## 2. Algorithms and problem-solving

What algorithm have you implemented or invented that you are most happy with? How did you arrive at the working solution, and what problems does it still have?

**Answer:**

### The context

The app is not designed to aggregate large historical data. It is designed to run optimizations on current data, prevent data loss and ease users going back and forth with different combinations of data until they find the optimal.

Then the requirements change. After a while, customers start asking for historical aggregations, and they are willing to pay for them. So it stops being a nice to have and becomes revenue, and we add versioning to a system that has no place for it.

### The data model

> **Note:** I am using Lay's Chips and shipments below instead of the real clinical supply data. Same structure, easier to follow. The table and column names are simplified.

We have two databases: `BusinessDB` (the actual data) and `MetaDataDB` (data about the data). Together they store the full history.

Nothing is ever overwritten. Every time you edit something, you save a new snapshot with a bumped version instead of editing the existing entry. So "Lay's Chips" is never a single row; it is all its snapshots.

`BusinessDB` → `products` table:

```
{id: 123, name: Lays chips, price: 2.00, description: blah}
{id: 252, name: Lays chips, price: 2.20, description: blah blah}
{id: 990, name: Lay's chips, price: 3.00, description: blah blah blah blah}
```

The rows carry no version. It is `MetaDataDB` that knows these three rows are the same product, and that 123 is version 1, 252 is version 2 and 990 is version 3.

`MetaDataDB` → `versions` table:

```
{id: 501, business_row_id: 123, version: 1}
{id: 502, business_row_id: 252, version: 2}
{id: 503, business_row_id: 990, version: 3}
```

The latest version with id 990 is the current Lay's Chips, but the older ones still matter. Why? not only to be able to revert to an older version, it's because of **references**.

Then shipments. Similar to products, they have a date and a destination.

`BusinessDB` → `shipments` table:

```
{id: 9025, date: 2021, destination: Germany}
```

But... what are we shipping? Where is the link between the shipment and the product?

The reference is not stored in that `BusinessDB` row. It lives in `MetaDataDB`.

`MetaDataDB` → `references` table:

```
{id: 9001, from_id: 845, to_id: 502}
```

This reads as "there is a reference between these two ids, and each id represents an entity plus a version."

Here is the awkward part. Those coordinates do not exist in `BusinessDB`. The real row is id 252, and only `MetaDataDB` knows that entity "Lay's Chips" in version 2 equals row 252 in `BusinessDB`. So resolving a single reference is a round trip: read the reference from `MetaDataDB`, resolve entity plus version into a real row id, go back to `BusinessDB`, and only then read the row.

### The problem

List the latest version of every shipment that shipped Lay's Chips to Finland.

Something that would have been straightforward in a relational DB becomes a complex problem with this particular model.

### The algorithm

- Ask `MetaDataDB` for every row id in `BusinessDB` that corresponds to any version of Lay's Chips.
- For each one, find in `MetaDataDB` the references pointing at it.
- Resolve each reference the same way, to get the row ids of the shipments.
- Go back to `BusinessDB` and check whether each shipment goes to Finland.

This is a very simplified version of the real problem. The actual work has many more layers: multiple reference hops, multiple tables, and different constraints on each join.

It is not hard because it is complex. It is hard because we deliberately made "the current version" not exist.

### The outcome

Splitting the databases did not only make reads slower. It also removed the safety net: when two tables live in the same database, the database itself guarantees that a reference points at something real. Across two databases it cannot, so nothing checks it, and my code ended up validating every reference by hand.

I spotted the root cause: two legacy databases doing one job. The algorithm worked, but it was hard to understand, hard to maintain, and a big chunk of code.

With a single database, my Scala code that merged two query results collapsed into a single query, improving both performance and maintainability, and it was easier to back up and deploy.

I explained the problem carefully to my department and convinced management to invest in merging the two databases, which we ended up doing.

## 3. When you visit the website of a SaaS company that has an API, what do you look for? What do you think is missing in most cases?

When I visit a SaaS API, I look for two kinds of dealbreakers: business and technical.

Business: pricing, licensing, ToS, SLA and compliance. If any of these fails our constraints, I stop. It does not matter how good the API is.

Technical: I read the Introduction, Getting Started and FAQ. Not cover to cover. I go straight to authorization, error shapes, rate limits, obvious endpoint URLs, a real OpenAPI spec with examples, and a sandbox with dummy data. If something is missing, that is a bad sign.

I also care about AI:
1. Every page available as Markdown: my-api.com/payments also served as my-api.com/payments.md
2. An MCP server so agents can search efficiently instead of guessing.
3. Skills that encode the integration workflow.

If the spec is good, I generate a client, make a real request and look at the actual response. That is how I can see how this API would be modeled in my app.

What is usually missing is exactly that last part: docs written only for humans, with no markdown, no OpenAPI spec and no MCP server, no sandbox, and errors that just say "something went wrong". The worst one now is docs that drift from the real API, because a stale spec makes an AI confidently write broken code.

## 4. Client types

What is your personal "pop psychology" classification of client types, and what is the best strategy for dealing with each type?

**Answer:**

Off the top of my head, I deal with three types:

- The engineer (nerd). My usual point of contact. We speak the same language, so the conversation is smooth. The small caveat: either of us can lack a piece of business context, and we can't always explain it because we don't own it. The talk stalls until a domain expert unblocks it.
Strategy: talk tech freely, but flag business gaps early and pull in an expert instead of guessing.

- The consultant. They use the app behind the API. Strong on the business, not technical. If I have to explain a technical problem, I always translate it into UI, screens, and business language. If I can't tie it to something visual ("clicking fast here triggers a race condition"), I use a metaphor. They have to be concrete with me too: "I click this button, I want that number; this other number is wrong." I don't need the business meaning, I need to reproduce the error, read the log, and find a workaround. They're pragmatic; they always want to move forward.
Strategy: no jargon; map everything to what they see. Match their pragmatism: reproduce, workaround, then explain.

- The corpo. They care about risk, numbers, efficiency, and legal.
Strategy: lead with impact (time, money, risk). One sentence, no rabbit holes.

## 5. How you work

How do you like to work? What is your process, and what do you need from us to do your best work?

**Answer:**

I like to work written-first and async. I build a small thing, then I explain it. I share drafts early and iterate. I use AI to go faster, but I keep the creative part: what to say, what to show, where the friction is.

My process starts as a confused first-time user.

1. Your website: is it obvious what the product is in 30 seconds?
2. Your docs: I start with a tutorial and reproduce it locally. I write down every bit of friction, and how I would fix it. If the tutorial is not straightforward, easy, and high value, I design a better one.
3. The spec: same bar as question 3. Auth, errors, rate limits, a real OpenAPI spec with examples, a sandbox. If those are missing, that is the work.
4. Your videos: if a developer watches, do they think "ah, so that is it," or is it corporate noise? I want real problems this tool actually solves. Then I sketch better ones: a diagram, a short clip, a worked example.

PearNote is the example. I wanted to understand P2P well enough to explain it, so I learned the concepts first (no server, two phones, deterministic merge), then the Holepunch stack I actually needed: Autopass, Autobase, Hypercore, Corestore, Hyperswarm, BlindPairing. Then I built a serverless Android app: one phone creates a note and an invite, the other joins, both lists stay in sync with no cloud. Then I wrote HOW-IT-WORKS.md and recorded a video walking through the layers. Learn the idea, learn the stack, build the thing, then explain it.

What I need from you: access (repo, staging, a way to run sdkgen), one concrete first problem rather than "go do DevRel," and fast written feedback on drafts. I need a bit of time to learn the product before shipping content, and an honest picture of who the real user is. I do not need a detailed brief.
