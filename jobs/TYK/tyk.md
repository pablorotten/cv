## The problem we had at my job
We had this problem in my job

### 1. Business & Deployment Context
* Product: B2B SaaS for supply chain optimization. Clients upload data, run optimizations, and view/export results (Excel, Qlik dashboards). We also offer consulting support.
* Architecture: Single-Tenant SaaS. For every new client, we provision an isolated AWS instance and deploy our stack using Docker containers.

### 2. The Problem
* A pilot client (and eventually future clients) needs a client-facing RESTful API.
* Currently, our system only has generic internal endpoints that return large data chunks. Clients have to pull everything and filter on their side, which wastes bandwidth and memory.
* Clients want specific endpoints (e.g., asking directly for date range filters) so they only receive the lean data they need.

### 3. Core Constraints
* Legacy Backend: Core backend is written in Scala with Akka. Our newly hired API developer does not know Scala/Akka.
* Slow Release Pipeline: The core Scala product is mature and resilient, but its release pipeline is intentionally slow and rigorous. We cannot wait on heavy backend release cycles for fast API experimentation.
* Cost & Margins: Because we run 1 single-tenant AWS environment per client, any solution must be 100% free/open-source per instance (zero per-client software licensing fees).
* Execution Goal: Rapidly experiment and iterate on custom endpoints with 1 interested pilot client, then productify the solution for all clients once stable.

### 4. Proposed Solution: Gateway
* We want to place a Gateway inside the client's single-tenant Docker environment, sitting in front of the Scala app deployed in AWS.
* How it works:
  1. Client calls the Gateway (e.g., GET /api/v1/data?startDate=X&endDate=Y).
  2. Gateway calls generic Scala endpoints locally over localhost.
  3. Gateway filters/reshapes the raw data in memory and returns a lean JSON payload to the client.
* Benefits: Unblocks the new dev (writes JS/TS), bypasses the slow Scala release cycle, costs $0 in license fees, and allows us to natively optimize the Scala backend later without changing the public API contract.

We hired an expert in APIs with a lot of experience working in consultancy with different clients. He did an assesment studing different options in the market and he chose TYK mainly because it was open source so we don't have to pay 1 license per client. I helped him a lot implementing the endpoints, adapting the scala app endpoints and writting some specific ones to solve performance issues and helped customers to solve questions and indicidents they had with the Gateway. Also wrote internal and external documentation for the Gateway, the endpoints and the different internal endpoints of the scala app and external endpoints of the Gateway. 

## TYK Job Description

I saw in TYK they have an open position for devrel

```
Company logo for, Tyk.
Tyk
Junior Developer Relations Advocate 

United Kingdom · 1 week ago · 54 people clicked apply

Promoted by hirer · Responses managed off LinkedIn

Remote
Full-time
Apply

Saved
Use AI to assess how you fit
Get AI-powered advice on this job and more exclusive features with Premium. Try Premium for €0

Show match details

Tailor my resume

Help me stand out

See how you compare to 54 others who clicked apply

Access exclusive applicant insights, see jobs where you have the highest chance of hearing back, and more.

Try Premium for €0

About the job
Who are Tyk, and what do we do?

The Tyk API Management platform is helping to drive the connected world and power new products and services. We’re changing the way that organisations connect any number of their systems and services.Whether internal, external, public or highly encrypted systems, Tyk helps businesses drive value across the retail, finance, telecoms, healthcare, or media industries (to name just a few!)

If you’ve banked online, used an app to check the news, or perhaps even driven a connected car, API’s, and by extension, Tyk, make that possible. Founded in 2015 with offices in London – UK, London – Ontario, Atlanta and Singapore, we have many thousands of users of our B2B platform across the globe. Brands using Tyk range from Lotte, Bell, T Mobile, to RBS, Capital One and Vinci. We have a varied user base hailing from every continent – even Antarctica.

Total flexibility, default remote, radical responsibility

We offer unlimited paid holidays and remote working from anywhere in the world, for everyone. Why? Tyk was founded on the principle of offering flexibility and autonomy to our employees, we believe this allows our employees to achieve their best results. It also means we can build the best possible team, location and working hours are no barrier.

If this sounds like an environment that you believe could work for you then read on to find out more.

The role:

We want developers to recommend Tyk to their companies without being asked – and this role is central to that.

We’re looking for a Junior Developer Advocate to build Tyk’s presence in the communities where developers are already talking about API management, AI, AI governance, and modern infrastructure. This isn’t a polished marketing role. It’s a platform-building role for someone early in their career who will roll up their sleeves, learn things in public, create content as they go, and show up at the meetups and conferences where real practitioners gather. We fund the travel and the stages; you build a real personal profile in the API and AI space.

You’ll be writing, recording, talking, and travelling across Europe. You’ll cover the topics developers actually care about – API management, AI and API governance, observability, real implementation stories – and grow into a recognisable, trusted voice in the space. We’ll invest in your profile as much as Tyk’s, because we think they’re the same thing.

This is a genuine learning opportunity and a strong foundation for a career in developer relations. If you’re looking for a stable content treadmill, this isn’t it. If you’re hungry, happy to earn your reputation at a scrappy, fast-moving startup, and want to become a known name in the developer community – keep reading.

What you’ll be responsible for:

Create content

Produce regular written and video content on API management, AI and API governance, observability, and real customer implementation stories.
Publish hands-on tutorials, how-tos, and ecosystem guides that enable developers to find the solutions they are looking for (think Kubernetes, OpenTelemetry, OAS, GraphQL, MCP and the AI/API intersection).
Learn in public – share what you’re figuring out as you go, rough edges and all.
Show up in the community

Attend and speak at developer meetups and conferences across Europe, growing Tyk’s visibility and goodwill through authentic, in-person engagement.
Be a genuine, friendly presence in developer communities online and off – the kind people trust because you’re real, not polished.
Feed community insight back into our product and marketing teams.
Own developer marketing channels

Take ownership of specific developer marketing channels (for example, our YouTube, blog, or community spaces like Reddit) – you’ll run them, grow them, and be accountable for them.
Experiment, measure what’s working, and aren’t afraid to try things that might not.
What we’re looking for:

Above all, the right attitude: enthusiastic, hungry to learn, a great communicator, and not afraid to try things and put your work out into the world.

Enough technical grounding to read code, understand architecture, and get your hands dirty — however you learned it. A CS degree is welcome but not required.
Some experience creating content – writing, video, or talks – even if it’s personal projects or university work.
Comfortable speaking to small groups; meetups and community events should excite you, not fill you with dread.
A creator’s instinct – you want to make things and share them.
Genuine curiosity about APIs, AI, AI governance, and where the infrastructure space is heading.
Happy to travel regularly across Europe as part of the role.
Self-directed and energized by a small, fast-moving team.
AI-native: you use AI regularly and know the difference between AI-assisted and AI slop.
Nice to have

An existing presence in developer communities – a blog, YouTube channel, GitHub, or a talk or two.
Hands-on experience with Kubernetes, observability tooling, or CI/CD pipelines.
Familiarity with API management concepts.
Why you should join us:

Everyone has unlimited paid holiday.
We have total flexibility in hours, as we believe creativity flows better when our people are given freedom to decide when they are most productive. Everyone is unique after all.
Employee share scheme
Generous maternity and paternity leave
Company retreats
We all share the same vision – we value authenticity, respect, responsibility, independence, honesty, diversity and inclusion and most importantly treating others how you wish to be treated. We look for like-minded people who bring their personalities to work everyday, strive to achieve their personal goals and who are willing to challenge the way we do things, why? – to make what we do even better!

It’s ok to screw up

We’ve found that it’s often the ‘stupid’ or unexpected ideas that turn out to be the successful ones – so try it, at least we can say we have.

The only stupid idea, is the untested one

It’s in our DNA – starting a business with founders 12 hours apart, giving our gateway away for free – sure, we did that, and we’d do it again.

Trust starts with you – make it count

Trust is a two-way street – instil it from day one.

Assume best intent

We have each other’s back – we’re all on the same team. Think before you speak or act.

Make things, better

Always try to leave things better than when you found them – change is constant, inevitable and embraced! Be that change we want to see.

What’s it like to work here?! check it out: https://tyk.io/worklife/

Tyk is an equal opportunities employer and we are determined to ensure that no applicant or employee receives less favourable treatment on the grounds of gender, age, disability, religion, belief, sexual orientation, marital status, or race, or is disadvantaged by conditions or requirements which cannot be shown to be justifiable.
You can see more about us here https://tyk.io
Benefits found in job post

Paid paternity leave
```

I want to apply there. I don't care it's junior.

## My plan to apply

My idea is to record a video explaining my experience with TYK. What was the problem we had in my copany, the different alternatives we tossed around and why we ended up with TYK

## The problem of my plan

When I ask to any AI to grasp a comparison with other alternatives and why TYK is better.... happens that TYK is actually the worst solution 😬.

```
Best fit: Fastify (Node.js/TypeScript)
Matches your BFF plan: fast, low overhead, great TypeScript support, free, and easy for your API dev.
Solid alternatives
Library	When to pick it
Fastify	Default choice — perf, plugins, schema validation
Hono	Even lighter; great if you want minimal surface area
NestJS	If you want structure/DI for a larger long-lived BFF
Express	Fine, but slower and more boilerplate than Fastify
Skip for this use case: Kong/Tyk/AWS API Gateway (ops weight or cost), and anything with per-instance license fees.

Why not TYK? Kong / Tyk — Built as API gateways (auth, rate limit, routing), not as a place to write custom filter/reshape logic. You’d still add a service for the BFF work, plus heavier ops (DB/config, plugins). Overkill for “thin facade in front of one internal app.”

### Could TYK do all the job? why use BFF?
Tyk can do some of the job — not cleanly the part you care about.
What Tyk does well
- Auth (API keys, OAuth, JWT)
- Rate limiting, quotas
- Routing / path rewrite
- Header/query transforms
- Basic response transforms (often template/JS plugins)
- Analytics, portal, multi-API policy
What you’re actually building
- Call multiple Scala endpoints and merge results
- Pull a big payload, filter by dates in logic
- Reshape into a stable public contract
- Iterate fast with a JS/TS dev who doesn’t touch Scala
- Stay $0 license per single-tenant instance
That’s application logic, not gateway policy.
Why Tyk is a weak fit as the “whole BFF”
Need	In Tyk
Multi-call orchestration + merge	Plugins/JS middleware — awkward, harder to test/debug
Date filter on large JSON	Possible in plugin; heavy, easy to OOM, poor DX
Complex domain rules	Fighting the tool
Fast iteration / productize endpoints	Config + plugin lifecycle
Per-tenant cost	Gateway ops; Tyk licensing can bite at scale
Your constraints	Extra moving part per client env
Tyk’s JS middleware can filter/transform, but you’re then writing a mini BFF inside a gateway — worse tooling, testing, typing, and local dev than Fastify/Hono.
When “just Tyk” is enough
- You only need: keys, rate limits, route to one existing endpoint, maybe strip fields
- Backends already return the right shape (or almost)
- No real orchestration or business filtering
When you need a BFF (your case)
- 1 client request → N internal calls → merge
- Filter/aggregate because Scala can’t yet
- Public API design separate from internal APIs
- Rapid experimentation without Scala releases
```

So I'm cooked. I can't use this story to apply for TYK because it's a fail. Whe should not have used TYK in the first place in my company.


## What I need?

I need more ideas to make a technical or kind of technical video about tyk to apply.

Some ideas I Have:
* Explaining what is the best tool for my problem you talked about BFF. I had no idea what is that (Is not Best Friend Forever 😅) and what is the difference between that and a Gateway. What are the best use cases for each, how can be combined and what are some good ones (mention TYK here)
* Explain the rate limit: This is something we used in my company and apparently TYK is specially good on that

Rate my ideas and propose yours. Ideally is for a short video of 2-5 minutes. I alredy did short-meme style for less technical and real video with my face talking and explaining deep technical things.

---

## Video strategy answer (2026-08-29)

### Honest take first

You're not cooked. The "we used TYK as a BFF and that was the wrong tool" story is actually **strong DevRel content** if you frame it right:

- TYK wants authentic, learn-in-public, real implementation stories
- "I misused a gateway as a BFF - here's what gateways are actually for" is more credible than fake hype
- You still have real TYK experience: rate limits, docs, customer incidents, single-tenant deploy, open-source cost constraint

Don't pitch "TYK solved our BFF problem." Pitch **when TYK is the right tool, and when it isn't.**

---

### Rating your ideas

#### 1. Gateway vs BFF (your first idea) — **9/10**
Best idea. Perfect for 3–5 min face-to-camera or screencast.

**Angle:**
- Problem: clients need lean filtered APIs
- Wrong instinct: "put a gateway in front and reshape in the gateway"
- Right model: **BFF for application logic**, **gateway for edge concerns**
- Where TYK shines: auth, rate limit, routing, policies, analytics, multi-tenant/API productization
- How they combine: Client → TYK → BFF (Fastify/Hono) → internal Scala

**Why this works for the application:**
- Shows product judgment, not just fanboy energy
- Matches their topics: API management, real implementation stories
- Uses your actual experience without lying
- Title hook: *"We put TYK where a BFF belonged. Here's what I learned."*

#### 2. Rate limiting deep dive — **7.5/10**
Solid, safer, more "product demo." Good if you want less architectural controversy.

**Angle:**
- Why naive rate limiting fails (per-IP only, bursty clients, multi-endpoint abuse)
- What you actually need in B2B SaaS (per-key, per-plan, quotas, soft vs hard limits)
- How TYK models this
- 60-sec live demo: key A gets 10 req/min, key B gets 100

**Risk:** more generic unless you tie it to a real customer incident ("pilot client hammered export endpoint and took down X").

---

### Better video ideas (ranked)

#### A. "Gateway vs BFF" (recommended) — 4 min
Structure:
1. **0:00** Cold open: "We chose TYK for the wrong reason… and still learned the right lesson."
2. **0:20** The real problem (single-tenant SaaS, slow Scala releases, JS/TS API dev, $0 license)
3. **1:00** What people confuse: gateway ≠ place to write domain filter/merge logic
4. **2:00** Split responsibilities table on screen
5. **3:00** Combined architecture diagram
6. **3:40** Close: "TYK is excellent at the edge. Don't force it to be your app."

This is the one I'd apply with.

#### B. "Why open-source API gateways matter in single-tenant SaaS" — 3 min
Your real constraint was **1 AWS env per client = no per-instance license tax**.

Angle:
- Multi-tenant: license once
- Single-tenant: license multiplies with every customer
- Why OSS gateway choice is a business decision, not just tech
- TYK as the pick under that constraint
- What you still needed beside the gateway (BFF/service layer)

Great for business + architecture audience. Less "I was wrong," more "decision framework."

#### C. "Rate limits that don't suck for B2B APIs" — 3–4 min
If you want a cleaner product story:
- Per-API-key limits
- Different plans
- Protect expensive endpoints (exports/optimizations)
- Show TYK config + one abuse scenario

Pair with a short meme cut for LinkedIn: "Your API without rate limits" / dumpster fire.

#### D. "From internal blob endpoints to a public API contract" — 4–5 min
Not "TYK did filtering," but:
- Internal APIs optimize for product internals
- Public APIs optimize for developer experience
- Gateway helps expose/version/protect the public surface
- Docs + support load drop when contract is stable

You can mention writing internal + external docs and reducing support noise.

#### E. Meme-style short (30–45s) as teaser, not main piece
Examples:
- "API Gateway" vs "BFF" dating-app style mismatch
- "When your gateway starts writing business logic"
- "Single-tenant SaaS + per-host license = financial horror"

Use this to drive people to the 3–5 min video.

---

### What I'd skip

- "Why TYK is the best BFF" — dead on arrival
- Pure feature tour with no story — forgettable
- "I am junior-curious and hungry" personality video with no tech — weak for this company
- Anything that needs K8s/OTel depth you don't have yet

---

### Application package suggestion

1. **Main video (A):** Gateway vs BFF, 3–5 min, face + diagrams
2. **Optional short:** meme teaser linking to it
3. **Cover letter one-liner:** "I ran TYK in production in single-tenant SaaS, wrote the docs, supported clients on it, and I want to teach the ecosystem when gateways are the right tool."
4. **Don't hide seniority:** "Junior title is fine. I'm pivoting into DevRel with production API-management scars."

---

### Quick verdict

| Idea | Score | Use as |
|------|------:|--------|
| Gateway vs BFF (honest) | 9/10 | **Main application video** |
| OSS gateway + single-tenant cost | 8/10 | Alt main / blog companion |
| Rate limiting in B2B | 7.5/10 | Second video or safer option |
| Public vs internal API contract | 7/10 | Strong follow-up |
| Meme short only | 6/10 | Teaser, not the application |