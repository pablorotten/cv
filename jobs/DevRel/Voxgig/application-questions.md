# Voxgig - Junior Developer Relations Engineer: Application Questionnaire

> Reply by email, writing each answer beneath the relevant question. Paste plain, no markdown.

## 1. Tell us about your personal experience organising, attending, promoting, or speaking at a developer event. What would you have done to improve the event?

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

The app was not designed to keep history. It was designed to run optimizations on current data, prevent data loss and ease going back and forth with different combinations of data until the customer finds the optimal.

Then the requirements changed. After a while, customers started asking for historical aggregations, and they were willing to pay for them. So it stopped being a nice to have and became revenue, and we had to add versioning to a system that had no place for it. 

### The data model

We had two databases: `BusinessDB` (the actual data) and `MetaDataDB` (data about the data). Together they stored the full history.

Nothing was ever overwritten. Every time you edited something, you saved a new snapshot with a bumped version instead of editing the existing entry. So "Lay's Chips" was never a single row; it was all of its snapshots.

`BusinessDB` → `products` table:

```
{id: 123, name: Lays chips, price: 2.00, description: blah}
{id: 252, name: Lays chips, price: 2.20, description: blah blah}
{id: 990, name: Lay's chips, price: 3.00, description: blah blah blah blah}
```

The rows carry no version. Entity 12 is the logical product, Lay's Chips, and it never changes and has no version of its own. It is the thing that appears as row 123 in v1, row 252 in v2 and row 990 in v3.

`MetaDataDB` → `versions` table:

```
{id: 501, entity_id: 12, business_row_id: 123, version: 1}
{id: 502, entity_id: 12, business_row_id: 252, version: 2}
{id: 503, entity_id: 12, business_row_id: 990, version: 3}
{id: 601, entity_id: 40, business_row_id: 9025, version: 1}
```

Entity 12 is the one that answers "how do I know these three rows are the same product". `entity_id` never changes and has no version of its own; it is the logical product. Each version row binds it to a different snapshot. That column is also why a store cannot be mixed up with another: Lay's Chips in Brussels and Lay's Chips in Lyon are different entity_ids, the same way two studies of the same drug are separate products.

When you created a shipment of Lay's chips to Finland in 2021, the shipment itself was just its own data:

`BusinessDB` → `shipments` table:

```
{id: 9025, date: 2021, destination: Finland}
```

But... what are we shipping? Where is the link between the shipment and the product?

The reference was not stored in that `BusinessDB` row. It lives in another `MetaDataDB` table. A reference is a pair of ids from the `versions` table:

`MetaDataDB` → `references` table:

```
{id: 9001, from_id: 601, to_id: 502}
```

This reads as "there is a reference between these two ids, and each id represents an entity plus a version." Reading `id` 9001 gives you two ids and nothing else: no "Lay's Chips", no "shipment", no "Finland". You look up `from_id` 601 and discover it is shipments v1, business row 9025. You look up `to_id` 502 and discover it is Lay's Chips v2, business row 252. All the meaning comes from the join.

Here is the awkward part. That lookup happens entirely inside `MetaDataDB`, but row 9025 only exists in `BusinessDB`. So resolving a single reference was a round trip: read the reference from `MetaDataDB`, use `versions` to translate it into a real row id, go back to `BusinessDB`, and only then read the row.

### The problem

List every shipment of Lay's Chips to Finland, across all stores.

Something that would have been straightforward in a relational DB becomes a complex problem with this particular model.

In a normal database this is one join. Shipment has `product_id`, product has `id`, you join and filter. You never think about versions, because a row *is* the current truth. When the price changes you update it, there is one Lay's Chips row, and historical accuracy is what you pay for that simplicity.

We inverted that trade. We guarantee the 2021 shipment still points at the price that was real in 2021, and we get it by keeping every snapshot forever. So "Lay's Chips" is not one row, it is three, and no single column anywhere says "this shipment shipped Lay's Chips." The link exists only as a chain through two tables in another database: entity, version, row. And "across all stores" makes it worse, because each store's Lay's Chips is a separate entity that must be walked separately and never conflated.

### The algorithm

- Start from the logical entity, Lay's Chips in this store (entity 12).
- Ask `versions` for every `business_row_id` it ever occupied: {123, 252, 990}, which gives you ids 501, 502 and 503.
- Find every entry in `references` pointing at any of those ids.
- For each one, read the other side of the link, and resolve it through `versions` to find out what it is and which `business_row_id` holds it.
- Go to `BusinessDB` and read that row to get the real shipment. Repeat for every store, and follow any further hops where a shipment references something that references something else.

Two stores and a chain of lookups where every answer required bouncing between them. This was complex because the backend, in Scala, had to merge queries from both databases across multiple tables and multiple reference hops. And the real requirement was never as simple as this example; I had to join multiple tables with different constraints.

It was not hard because it was complex. It was hard because we had deliberately made "the current version" not exist.

### The outcome

Splitting the databases did not only make reads slower. It removed the database's ability to enforce the relationships, because a foreign key cannot cross two databases. Instead of a constraint the engine guarantees, we got a row in a table that nothing enforces, so the application had to check every reference by hand on every write.

I spotted the root cause: two legacy databases doing one job. The algorithm worked, but it was hard to understand, hard to maintain, and a big chunk of code.

With a single database, my Scala code that merged two query results could have collapsed into a single query, improving both performance and maintainability, and it was easier to back up and deploy.

I had to explain the problem carefully to my department and convince management to invest in merging the two databases.

## 3. SaaS developer experience

When you visit the website of a SaaS company that has an API, what do you look for? What do you think is missing in most cases?

**Answer:**

When I visit a SaaS API, I look for two kinds of dealbreakers: business and technical.

Business: pricing, licensing, ToS, SLA and compliance. If any of these fails our constraints, I stop. It does not matter how good the API is.

Technical: I read the Introduction, Getting Started and FAQ. Not cover to cover. I go straight to authorization, error shapes, rate limits, obvious endpoint URLs, a real OpenAPI spec with examples, and a sandbox with dummy data. If something is missing, that is a bad sign.

I also care about AI:
1. Every page available as Markdown: my-api.com/payments also served as my-api.com/payments.md
2. An MCP server so agents can search efficiently instead of guessing.
3. Skills that encode the integration workflow.

If the spec is good, I generate a client, make a real request and look at the actual response. That is how I can have an idea how this API will be modeled in my app.

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
