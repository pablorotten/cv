# Voxgig - Junior Developer Relations Engineer: Application Questionnaire

> Reply by email, writing each answer beneath the relevant question. Paste plain, no markdown.

## 1. Developer events

Tell us about your personal experience organising, attending, promoting, or speaking at a developer event. What would you have done to improve the event?

**Answer:**

Last year I spoke at [N-SIDE Connect 2025](https://www.n-side.com/en/news/n-side-connect-innovation-in-clinical-supplies-2025), the clinical-supply event my company runs for its customers in Belgium. I presented a session "Leveraging APIs and system integrations to operationalise a supply chain strategy".

The audience was mixed: software engineers, but also managers, supply-chain experts and clinical coordinators. I designed the talk as an hourglass: open broad for the business stakeholders, narrow into the technical for the engineers, then widen back out to the ROI for the decision-makers.

Connecting the business and technical point of view was the real challenge. So rather than just saying "coordinators save four hours a week on data entry", I make the business connection out loud: "by removing four hours of data entry, coordinators can spend that time refining risk, preventing supply stockouts and cutting drug waste by 15%." One fact, bridged for both halves of the room.

Everyone knows how Excel looks like, so I showed a huge spreadsheet and then showed how it collapses into a small JSON payload a machine can process: technical for the developers, but still familiar for everyone else.

Q&A with a mixed audience is hard: I can't control what people ask, and a technical question can lose the rest of the room. I set the ground rules up front (questions at the end, technical deep-dives after the session). For business or pricing questions, I never guess without the data; we had the relevant manager and a salesperson on hand for that.

If I ran it again, I'd fix the one thing I actually missed: a formal, scheduled post-talk slot for the engineers to ask technical questions. Some of them came over informally afterwards, but that space should have been announced and planned. The best technical questions deserve a room where you can go deep.

## 2. Algorithms and problem-solving

What algorithm have you implemented or invented that you are most happy with? How did you arrive at the working solution, and what problems does it still have?

**Answer:**

We had two databases: `BusinessDB` and `MetaDataDB`. Together they stored the full history of everything.

Nothing was ever overwritten. Every time you edited something, you saved a new snapshot with a bumped version instead of editing the existing entry. So "Lay's Chips" was never a single row; it was all of its snapshots.

`BusinessDB` --> Products table:

```
{id:123, name:"Lays chips", price:"2.00", description:"blah"}
{id:252, name:"Lays chips", price:"2.20", description:"blah, blah"}
{id:990, name:"Lay's chips", price:"3.00", description:"blah, blah, blah, blah"}
```

The rows themselves carry no version. It is `MetaDataDB` that knows these three rows are the same product, and that `123` is `version 1`, `252` is `version 2` and `990` is `version 3`. The latest version with id `990` is the current Lay's Chips, but the older ones still matter. Why? not only to be able to revert to an older version, it's because of **references**.

When you created a shipment in 2021, it was linked to whichever snapshot of Lay's Chips was current at that time:

`BusinessDB` → Shipments table:

```
{id:9025, date:"2021", destination:"Germany", item:252}
```

`item:252` means "this shipment shipped product snapshot 252" (Lay's Chips version 2). It stays pinned to that snapshot forever: even after a later version changed the price, the 2021 shipment still points to the version it actually shipped.

The problem: list every shipment that shipped "Lay's Chips".

The algorithm:

- Ask `MetaDataDB` for every snapshot that represents Lay's Chips on `BusinessDB`: {123, 252, 990}.
- Then, in `BusinessDB`, find every shipment whose `item` is one of those ids, and collect them.
- Where references chained, like a shipment referencing something that referenced something else; follow those hops too, so it was not always a single step.

This was complex because the backend, in Scala, had to merge queries from two different databases (`MetaDataDB` and `BusinessDB`) across multiple tables and multiple reference hops. Also the real requirement was not as simple as this one, I had to join multiple tables with different constraints.

The outcome:

I spotted the root cause: two legacy databases doing one job. The algorithm worked, was complex to understand and hard to mantain. Was a big chunk of code.

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
