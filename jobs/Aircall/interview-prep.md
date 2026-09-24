# Aircall - Interview Prep

Role: Customer Engineer / Staff Customer Engineer - Iberia & FIME (Madrid, hybrid)
Contact: Marie Mas (recruiter) - 30-min video screen

---

## What Aircall does

**One line:** Aircall is a cloud phone system for customer-facing teams - voice, SMS, and WhatsApp in one workspace, with AI on top - that captures every call as data and pushes it into the tools a company already uses. The phone number is the key, the CRM is the record, Aircall is the engine in between.

**Who buys it:** any company with a phone-heavy customer motion - sales (SDRs/AEs calling out), support/contact centers, and general ops. 22,000+ companies, SMB through enterprise. Strong in Europe: Paris HQ, big Madrid hub.

**The value stack (5 layers):**
1. **Run the calls** - cloud telephony: routing, IVR, queues, transfers, agent availability. Entry point for many buyers is "our phones are a mess."
2. **Capture** - recording, transcript, and metadata (number, duration, direction, agent, tags) on every call.
3. **Context** - screen-pop, click-to-call, and full interaction history on the contact/deal/ticket in the CRM.
4. **Automate** - flows and the AI Voice Agent handling routine calls.
5. **Analyze** - dashboards and AI on top of the captured data.

**Products:**
- **Core platform:** voice, SMS, WhatsApp; numbers, call routing/queues, IVR, voicemail, recording.
- **Integrations:** native connectors for Salesforce (v3, with a dedicated Aircall Log object), HubSpot, Pipedrive, Zoho, Zendesk, Intercom, Freshdesk, Slack + 100 more. Public REST API + webhooks for custom work. Everywhere SDK to embed the softphone inside a CRM. Insight Cards show up to 5 fields from a CRM object during a call.
- **AI layer:** AI Voice Agent (handles routine calls), AI Assist (post-call work), AI Assist Pro (real-time guidance). Smartflows = current routing engine.
- **Data/intelligence layer (two flavors):**
  - **Analytics / reporting (operational BI):** volume, missed calls, AHT, wait times, agent performance, tags, AI interventions. Tiered: Analytics vs Analytics+ (add-on). Export via API, or feed external BI/dashboards.
  - **Conversation Intelligence (content analytics):** what was *said* - summaries, structured custom summaries, action items, playbook results, call evaluations.

**How it integrates (the "don't switch tabs" picture):**
- **UI inside the CRM** -> Everywhere SDK / CTI (full softphone embedded in the CRM).
- **Data both ways with a CRM** -> native connector (click-to-call, screen-pop, call logging).
- **Anything custom** -> Public API + webhooks.
- **Slack** -> native: posts call activity and user events to channels. **Google** -> Calendar for agent availability; Contacts sync via automation tools. **Jira** -> no deep native connector; via Zapier/Workato or custom webhooks.

**Nuances worth knowing:**
- **Metadata vs content:** metadata is always stored; recording/transcript/summary depend on plan, settings, and **compliance** (call-recording consent, GDPR).
- **Identity is the contact/company record**, not the phone number - the number is the key that links a call to the right entity.
- **Only calls through Aircall are captured.** It's a single pane of glass only if the phone work runs on it.
- **AI data is editable** - the API distinguishes AI-generated vs human-corrected summaries.

## Template answer: "What do you know about us?"

> "Aircall is a cloud phone system for customer-facing teams. It brings voice, SMS, and WhatsApp into one place, and it connects to the tools companies already use, like Salesforce, HubSpot, Zendesk, or Slack. So every call gets captured and tied to the right contact, instead of call data living in one system and the CRM in another. On top of that there's an AI layer: a Voice Agent that handles routine calls, and tools that summarize and structure the calls a person takes. They work with over 22,000 companies, from small teams to enterprise, and Europe is a big part of that - Paris is the HQ and Madrid is a major hub. What caught my eye is that it's the same bridge I've been doing for the last few years: the technical integration on one side, the customer on the other, plus this growing data and AI piece that I find genuinely interesting."

**If pushed for depth, add:** the analytics angle - "there's also a reporting and conversation-intelligence layer, so teams can see call volumes, handle time, and what actually happened on each call. That part maps to work I've done too - I built data-visualization dashboards earlier in my career and later a data-extraction product at N-SIDE."

## Template answer: "Why Aircall?"

**The three ingredients:** role fit, product fit, momentum. Hit all three, in that order, and keep it personal.

**Say this (primary):**

> "Two reasons, and the biggest one is the role. I'm ready to stop splitting my time. For the last five years I've been 50/50 between Solutions Engineering and development, and I want to go all-in on the customer side. This is exactly that opportunity - Aircall's Customer Engineer is the full version of the work I enjoy most: the discovery, the integrations, seeing someone actually adopt what we built. That's what motivates me most right now. The second is the product. I've spent my career on APIs and integrations, and that's central to what Aircall is - the value comes from how it plugs into Salesforce, HubSpot, webhooks, the tools a team already uses. So it's the same kind of work I've been doing, just on voice, SMS, WhatsApp, and now AI. And the AI part is what makes me want this now rather than later: the Voice Agent and the assist tools are changing what a support or sales team can actually do, and I'd rather be on the side helping customers use it than reading about it. And it's a European company with a real hub in Madrid, which fits where I am and the languages I speak."

**Shorter version (20-30s):**

> "For me it's the chance to go from 50/50 to full Solutions Engineering - that's what I want right now. Aircall's Customer Engineer is the full version of the customer-facing work I've been doing half-time, on a product where the value is exactly my strength: the CRM, the API, webhooks. Add the AI layer, and it's the kind of problem I want to work on."

**Don't:**
- Don't just praise the company generically ("great culture, great product"). Give your reason.
- Don't lead with location or salary.
- Don't recite features. One or two concrete ones (Voice Agent, CRM integrations) is enough.
- Don't say "passionate about" or "excited to" - just say what pulls you toward it.

---

## 1. What the 30-min screen actually is

A recruiter screen is not a technical bar. Marie wants to confirm:
- Motivation: why Aircall, why Customer Engineering
- Baseline fit: your background vs the role
- **Level fit**: the role is titled Staff, and that is the main thing to resolve
- Logistics: Madrid/hybrid, languages, salary expectations, timeline

She is not trying to trap you. She is building a shortlist. Your job: be easy to advance and remove any reason to pass.

---

## 2. The level question - handle it early, stay senior

Don't ignore the gap and don't apologise for it. Raise it calmly and let her calibrate.

**Script (adapt, don't recite):**

> "One thing I wanted to align on: I applied to the Customer Engineer role, and your email mentioned the Staff position. I'd love to understand whether this is the same opening leveled up, or a separate req. I'm flexible on level - my priority is the scope and the team. I have 10+ years in engineering, the last ~5 at N-SIDE building and supporting an API product directly with customers, so I'd like to understand where that lands on your ladder."

That does three things: shows you noticed, shows you're not intimidated, keeps both reqs alive. If she says "Staff needs 8+ years of CE," you can respond: "Understood - would you also consider me for the Customer Engineer opening? It's still live and I think it's a strong fit." Either way you're in a process.

**If she asks if you're comfortable with Staff level:** be honest. "I'm confident on the technical and customer sides. The newer part for me is the enterprise/commercial weight - exec QBRs, renewal and NRR ownership at scale. I'm keen to grow into that, and I pick up domains fast." Honest, not self-disqualifying.

---

## 3. Your narrative in one breath

**Keyword note:** the call is likely on Aircall and transcribed, so the transcript will be scanned for keywords. Say the exact title **"Solutions Engineer"** early and repeat it - never paraphrase yourself as "software engineer" or "product person". Lead with it.

**Say this (primary):**

> "I'm a Solutions Engineer. For the last five years at N-SIDE I've worked 50/50 as a Solutions Engineer and a Developer on an API platform. On the Solutions Engineer side I owned the customer relationship: I designed around 20 API endpoints, took the product from a PoC to production, onboarded five customers, wrote all the external documentation and tutorials, and handled their technical problems directly. On the developer side I built the platform itself, on the TYK gateway. So I sit exactly where Aircall puts a Customer Engineer - a Solutions Engineer sitting between the product and engineering side and the customer."

**Then pivot to Aircall:**

> "Aircall is doing that same bridge at a much bigger scale - voice, SMS, WhatsApp, and now AI agents. That's the work I want to be doing."

**Shorter version (if time is tight):**

> "I'm a Solutions Engineer at N-SIDE, where I split my time 50/50 between Solutions Engineering and development on an API platform. I built it, documented it, onboarded the customers onto it, and supported them directly - so I've been doing Customer Engineering work for five years. Aircall takes that same bridge to voice, SMS, WhatsApp, and AI."

**Why it works:** "Solutions Engineer" lands in the first sentence and keeps coming back, the 50/50 split is explicit so HR can't misread you as "just a developer", and it closes on the bridge between product and customer - the exact CE positioning.

---

## 4. STAR stories (Situation / Task / Action / Result / Close)

Stories A-C cover most competencies; D-F are extra API/performance/architecture stories, and the process answers cover the "how do you decide / how do you measure" questions. Don't reuse the same story twice in one interview. The labels are just the skeleton - tell it as a story, and always land on the result or business value.

### Story A - The API branch
**Covers:** ownership / PoC to production · solution architecture & technical depth · driving adoption · commercial / expansion instinct.
- **Situation:** customers did everything by hand in the UI - uploading data, running simulations, copying results out; a key client asked to connect their own systems instead.
- **Task:** take it on as a PoC but treat it like a product.
- **Action:** discovery with the customer and their technical users (what they needed to push in and pull out); designed ~20 API endpoints; built the platform on the TYK gateway; wrote the external docs and video tutorials; handled their technical questions directly and iterated on what broke.
- **Result:** full product adopted by every existing account; 5 new customers integrated after launch; a new revenue line from the same API (customers pulling their own historical data - shipments, CO2 emissions, trial duration).
- **Close:** "the full circle - discover, build, document, onboard, support - which is exactly the CE loop."

### Story B - Support flow and product feedback
**Covers:** troubleshooting complex issues · cross-functional influence · honest handling of a missing feature · calm under pressure.
- **Situation:** customers submitted issues through a ticket portal; a first line triaged them; I was the second line for the technical and integration problems.
- **Task:** own the escalated problems end to end - and turn the recurring ones into product input instead of fixing the same thing forever.
- **Action:** debugged customer integrations against the API (what changed, logs, auth, webhooks); wrote the docs, tutorials, and videos that cut the volume reaching us; became the point of contact for PMs - identified pain points and possible improvements, assessed and measured new ideas, and turned them into features; when a request wasn't on the roadmap, found a workaround and logged the business case.
- **Result:** fewer support tickets; recurring issues became product improvements; trust kept when I couldn't hand over the feature.
- **Close:** intake -> triage -> fix -> self-service -> product feedback. (Also the Kanban lead story - running standups, keeping delivery moving - if they ask about leading or coordinating.)

### Story C - ProGuard Assembler
**Covers:** quick learner · learning a new domain fast (directly relevant to the telephony and product-domain gap).
- **Situation:** I had to produce a technical DevRel piece on ProGuard Assembler, a tool I'd never used.
- **Task:** learn it well enough to explain it clearly and ship something public.
- **Action:** worked through it hands-on until I could bypass root detection and decrypt AES-256 secrets, then wrote the step-by-step guide and recorded the video.
- **Result:** shipped a public video and repo.
- **Close:** "the same way I'd pick up SIP, call flows, and the Aircall product."

### Story D - Performance incident on one instance
**Covers:** troubleshooting under pressure · owning an incident end to end · prevention and lessons learned.
- **Situation:** one customer's instance became unresponsive. A single endpoint was doing heavy computation, and a specific corner case - an unusual combination of shipments, locations, patients, and other parameters - exploded the computation time. It froze that instance, so even normal users lost the UI.
- **Task:** restore the instance, find the root cause, and make sure it couldn't happen again.
- **Action:** we located the endpoint from monitoring and logs, reproduced it with the customer's data set, and profiled the computation. We mitigated first - protecting the instance by limiting or queueing the heavy operation - then fixed the root cause by optimizing the calculation.
- **Result:** the instance recovered, normal users were unblocked, and the endpoint's response time came back in line.
- **Close / prevention:** the key point is that we can't predict every corner case, so we didn't just patch that one combination. We put in general guardrails so any heavy computation stays contained:
  - heavy work runs off the main request path, in background workers, so it can't block the instance;
  - it's bounded by a time budget and timeouts, plus pagination and result-size limits;
  - per-endpoint concurrency and rate limits, with a circuit breaker, so one slow operation gets cut off instead of dragging the whole instance down;
  - per-endpoint latency and error monitoring with alerts, so the next unforeseen case is caught early;
  - and the endpoint now fails gracefully (returns a timeout or a partial result) instead of freezing the UI.
- We kept a regression test for the original case too, but the goal was to make heavy computation safe in general - so a different combination or a different endpoint can't take the instance down either.

### Story E - Native endpoint for a repeated BFF pattern
**Covers:** spotting patterns · proposing product improvements · cross-team collaboration · performance.
- **Situation:** the BFF (backend-for-frontend) was making a repeated call pattern - several calls to the internal API product just to build one screen or action.
- **Task:** cut the load and the latency without changing anything the user sees.
- **Action:** I looked at the call pattern, confirmed it was frequent and costly, and proposed a native endpoint in the internal API that returned the needed data in a single call. Worked with the team to design and ship it, then moved the BFF onto it.
- **Result:** the BFF got faster and made far fewer calls, and the load on the internal API dropped. Other consumers could reuse the same endpoint.
- **Close:** "spot the pattern, propose the product change, ship it, measure it" - the same motion I'd run with customers on Aircall.

### Story F - Gateway vs BFF (the architecture lesson)
**Covers:** solution-design judgment · owning a mistake honestly · putting logic in the right layer.
- **Situation:** our clients wanted to connect their systems to our SaaS and get clean, filtered data, but the internal backend only exposed big, generic chunks - it wasn't built for that.
- **Task:** give them a proper API quickly, without waiting on the slow core release cycle.
- **Action:** the gateway was already sitting in front, so I used its built-in scripting to filter and reshape the responses there. For the pilot it worked, and it looked like we'd avoided building a service.
- **Result / what went wrong:** as more clients asked for different filters, merges, and shapes, that logic grew inside the gateway. It was hard to test, every change meant a gateway deploy, and we mixed "edge" concerns (keys, rate limits, routing) with "application" concerns (filtering, merging). We'd built a BFF in the wrong place.
- **Close / lesson:** the right design is a gateway at the edge and a small application layer - a BFF (backend-for-frontend) - behind it: the gateway does auth, keys, rate limits, and routing; the BFF does the filtering, merging, and reshaping, and gets tested and deployed like normal code. In the end that's exactly what we did - we implemented the BFF properly as its own layer and kept the gateway for what it's good at. The lesson I carry: put logic in the right layer, not the convenient one.

### Process answers (API usage, common issues, metrics)

**How I measured which APIs were popular, and where to invest**
- Instrumented usage: call volume per endpoint, per customer, plus error rate and latency.
- Ranked endpoints by usage and by how slow or heavy they were, and by error rate.
- Invested where usage is high and performance is poor; turned repeated call patterns into native endpoints; added endpoints where a capability was missing and customers kept asking.
- Brought that data to Product to prioritise the roadmap.

**Most common daily issues, and repeated 2nd-line problems**
- Most common: integration problems - authentication/token issues, malformed requests or wrong field mapping, misunderstandings of how an endpoint works, and data not syncing.
- When a problem keeps coming to 2nd line: stop solving it case by case. Find the pattern and fix the root cause - improve the documentation, add input validation or a guardrail, or build the missing endpoint/feature. The goal is to push it down to self-service and cut recurrence.

**Metrics to prove the improvement**
- Support: ticket volume, recurrence rate of the same issue, resolution time.
- Product/API: endpoint latency, error rate, call volume, instance load, uptime.
- Adoption: API usage, number of consumers, uptake of the new endpoint.
- Always compare before and after to show the change.

**Note:** for the customer-facing stories, always say who the customer was (pharma clinical-trial supply-chain teams) and quantify where you can.

---

## 5. Common questions (full bank)

Grouped by type. For the 30-min recruiter screen, only group A plus logistics/salary realistically come up - the rest are for the hiring-manager and later rounds. Pointers on the tricky ones.

**A. Motivation / background (screen)**
- Tell me about yourself.
- Why Aircall? Why Customer Engineering? -> the bridge role is literally what you did at N-SIDE; Aircall adds voice/SMS/WhatsApp/AI scale. Mention Madrid + languages.
- Why are you leaving N-SIDE / why the change? -> the hybrid-to-full-SE story.
- You're a developer - why customer-facing? -> the 50/50 split taught you where your energy is; you stay hands-on technically.
- What do you know about us? -> use the template answer above.
- What are you looking for in your next role?
- Where do you want to be in a few years?
- Salary expectations? -> "I'd love to understand the band for the level first."
- Location / relocation to Madrid / hybrid? -> based in Belgium, Spanish native, happy to relocate (confirm your actual situation).
- Languages? -> Spanish native, English full professional, French professional. Mention early.

**B. Customer craft**
- Tell me about a time you turned around a challenging or at-risk customer. -> the integration friction story; docs + hands-on support.
- Describe a time you drove adoption of a product or feature. -> N-SIDE API adoption, screencasts, data extraction.
- How do you handle a customer asking for something not on the roadmap? -> understand the underlying problem first, workaround if possible, champion the business case, follow up.
- How do you handle an angry customer?
- How do you identify churn signals early?
- How do you prioritise a large portfolio when you can't touch every account? (Staff - key)
- How do you align a customer's technical needs with their business goals?
- Tell me about a time you explained something very technical to a non-technical person.
- How would you run a QBR / technical business review? (Staff)
- How would you spot expansion opportunities? (Staff)

**C. Technical / integration**
- Explain APIs and webhooks to a non-technical person. -> menu vs the kitchen texting you when it's ready.
- How would you debug a customer integration that stopped working? -> what changed, logs on both sides, auth/token expiry, webhook delivery, 2XX within 5s, retries and auto-disable after 10 failures.
- Walk me through how you'd onboard a new customer technically.
- What's your experience with CRMs (Salesforce/HubSpot)? -> be honest; connect to the integration mindset (screen-pop, call logging, field mapping).
- A customer's system isn't in the native list - how do you connect it? -> Public API + webhooks, or an automation platform (Zapier/Workato).
- What happens if a customer's webhook endpoint goes down? -> Aircall retries, then disables after 10 failed deliveries; you'd monitor and alert.
- Do you have VoIP / telephony experience? -> honest no, plus quick-learner proof (ProGuard) and the API/integration side.
- Tell me about a hard technical problem you solved. -> API/webhook debugging; structured approach: reproduce, hypothesis, isolate one variable, update the customer throughout, escalate when stuck.
- Some Aircall processes include a light technical/SQL screen - be ready for basic SQL and API reasoning.

**D. Behavioral / cross-functional**
- Time you influenced a cross-functional team (engineering/sales/product) against resistance.
- Time you took ownership of a problem that wasn't assigned to you.
- A disagreement with a colleague or stakeholder - how you handled it, and the outcome.
- A time you delivered under pressure or in an escalation.
- A time you failed or got tough feedback - what you learned.
- How do you handle competing priorities?
- Time you mentored or enabled someone. (Staff)

**E. Commercial / Staff-level**
- How do technical decisions affect renewal, NRR, GRR?
- How would you handle an escalation on a strategic account?
- How do you build credibility with a CTO or Head of CX?
- How would you drive AI add-on adoption (AI Assist Pro, Voice Agent)?
- How would you raise the technical bar / mentor other CEs?

**F. Closing**
- Why should we hire you?
- What questions do you have? -> always have some (section 8).
- What's an area you want to grow in? -> enterprise/commercial side, telephony domain (honest).

**Delivery tips**
- Use STAR for behavioral; always end on the outcome.
- If you don't know, say so and explain how you'd find out - never bluff.
- Keep screen-round answers to 60-90 seconds.

---

## 6. Gap awareness (the "do you fit 100%?" question)

**The setup:** she already spotted the gaps. She asks *"Do you think you fit 100%, or are there some gaps?"* This is an **honesty and self-awareness test**, not a knowledge test. The wrong answers:
- **"Yes, 100%"** -> not credible; she knows the gaps. Reads as arrogant or unaware.
- **"No, I'm underqualified."** -> self-sabotage; you give her a reason to pass.

The right answer: **don't claim 100%**, name **2-3 real gaps**, then hand her a ramp plan. Pick the 2-3 based on which role it lands on:
- **Staff CE:** product/business domain, enterprise/exec + commercial, seniority.
- **Regular CE:** product/business domain, French.

### Opening template

> "No, I don't think anyone fits 100% - and I'd rather be straight with you. There are a couple of areas where I'd be ramping up, mainly the product domain and the enterprise layer. Can I tell you how I'd go at them?"

### The gaps

**1. Product and business domain knowledge (telephony, CRM, AI)**
- **Formulate:** "The biggest gap is the domain. I've spent my career in APIs, integrations, and platforms - not telephony, not living inside Salesforce or HubSpot, and not voice AI. SIP, call flows, contact-center metrics, CRM depth, agentic voice - that's all product knowledge I'd be picking up."
- **Propose to her:** "I'd want a structured ramp: your product bootcamp, shadowing a senior CE through two or three onboardings, and pairing on live escalations. Domain knowledge is the fastest thing for me to learn - I've done exactly that before."

**2. Enterprise / strategic accounts & exec stakeholders**
- **Formulate:** "Most of my customers were mid-market and technical users. I haven't spent much time in front of CTOs or Heads of CX."
- **Propose to her:** "I'd start by joining a senior CE on a couple of enterprise accounts and one QBR, then take my own from there. Seeing it run once is the fastest way for me to pick it up."

**3. Commercial ownership (renewal, GRR/NRR, QBRs, expansion)**
- **Formulate:** "I've built the product and driven adoption, but I haven't owned renewal or expansion numbers."
- **Propose to her:** "Sit me in on a full renewal cycle and a QBR with a KAM first, so I learn how you articulate ROI and read the signals. I understand the technical levers that drive renewal - I just haven't owned the commercial outcome."

**4. Seniority / CE-years at Staff level**
- **Formulate:** "The Staff bar is 8+ years in customer engineering. I'm at about five years of direct SE work, on top of ten total in engineering."
- **Propose to her:** "I'm flexible on level - if it fits better, put me in the senior CE seat and let the work make the case for Staff. I'd rather earn it in the role than argue about the title."

**5. Mentoring at Staff scale**
- **Formulate:** "I've led a Kanban team and onboarded and documented, but I haven't mentored a team of CEs."
- **Propose to her:** "I'd start by running enablement sessions and tightening documentation, and ask the team where the technical standards need raising most."

**6. French (only if it lands on the regular CE role)**
- **Formulate:** "French is my third language, and I use it every day - my current company is based in Belgium, so a good share of internal meetings and discussions happen in French, and I'm comfortable thinking and speaking in it. Where I'm lighter is customer-facing French, because my customer work has mostly been in Spanish and English. So it's about sharpening the customer vocabulary and register, not about learning the language."
- **Propose to her:** "I'd sit in on French customer conversations with a colleague for my first few weeks and practise the product vocabulary. I'm confident I'd be fully operational in a French or hybrid environment after a short ramp - I just want to be straight that the customer-facing side would take me a little time to warm up, since it's a different register from internal meetings."

### Framing rules

- Never answer "100%."
- Name 2-3 gaps maximum - the real ones for this role. Don't recite all six.
- One sentence to acknowledge, then the plan. Don't dwell on the weakness.
- Every action is something you'd do **with their support** -> reads as coachable, not a lone fixer.
- Attach proof you learn fast: ProGuard Assembler, TYK gateway.
- Hand the level decision to them; stay flexible.
- Close on strength: "The technical and customer sides I'm confident on - the gaps are the domain and the enterprise layer, and those are exactly the parts I'm most motivated to grow into."

---

## 7. Domain crash course (do this before the screen)

**VoIP / telephony basics**
- SIP = signalling protocol; RTP = carries audio; PSTN = the traditional phone network.
- DID = your Aircall phone number. Number provisioning and porting.
- IVR (Interactive Voice Response) = the "press 1 for sales" menu. Call routing / call flows. Queues, ring strategy, voicemail, call recording.
- Why it's hard: latency/jitter, codecs, NAT/firewalls, compliance (call-recording consent, GDPR).

**Contact-center & commercial vocabulary**
- Agent, queue, AHT (average handle time), FCR (first call resolution), abandon rate, CSAT, occupancy, SLA.
- QBR (Quarterly Business Review), NRR (Net Revenue Retention), GRR (Gross Revenue Retention), churn, expansion.

**Aircall platform specifics (technical)**
- **Public API:** REST at `api.aircall.io/v1`, HTTPS only, OAuth2 access tokens. User V1 deprecated, removed 30 Sep 2026 -> build on User V2.
- **Webhooks:** register from the Dashboard or `POST /v1/webhooks`; events include `call.created`, `call.ended`, `call.tagged`, `call.commented`, `contact.*`, `user.opened/closed`, `message.*`, `ai_voice_agent.started/ended/escalated`, `realtime_transcription.utterances_received`, `custom_summary.*`, `call_evaluation.*`. Max 100 webhooks/account. Must return 2XX (ideally 200) within 5s; auto-disabled after 10 failed deliveries. Each webhook has a unique token to verify origin.
- **Integrations** are enabled at Company level by an Admin; multiple instances allowed.
- **Everywhere SDK:** embeds the softphone/CTI into a CRM (V1 deprecated, use V2).
- **Insight Cards:** surface up to 5 fields from a CRM object in the agent's in-call view.

**Aircall values (mirror this language):** customer-obsessed, data-driven, ownership, continuous learning, "thoughtful speed", collaborative, fast-moving.

---

## 8. Questions to ask her

1. "Is this the same opening as the Customer Engineer role, leveled differently, or a separate Staff req? And is the CE role also still open?"
2. "What does the Customer Engineering team in Madrid / Iberia & FIME look like today?"
3. "How is a CE measured - onboarding, adoption, renewals, AI add-on activation?"
4. "What does success look like in the first 90 days?"
5. "What's the biggest challenge the CE team is facing right now?"
6. "Which customer segments would I focus on, and what do their tech stacks typically look like?"
7. "What's next in the process after this call?"

---

## 9. Logistics & first-impression checklist

- [ ] Test camera, mic, and connection 10 min before.
- [ ] Quiet room, clean/neutral background, good light.
- [ ] Have the JD, this doc, your resume, and 2-3 STAR stories on screen (not visible to camera, but within reach).
- [ ] One-page note card: your narrative sentence, the level script, and 3 numbers (~20 endpoints, 5 customers, new business line).
- [ ] Speak slowly; English is a second language - fluency is fine, just don't rush.

---

## 10. One-line summary to keep in your head

"Technical enough to build the integration, customer-facing enough to make it succeed, and honest about learning the telephony and enterprise-commercial parts."


## TO ADD

- Situation where an endpoint was compromising the instance performance. How we handle it? There was a corner case of one study with a very specific combination of shipments, locations, patients, etc that was causing a massive computation time in the server that froze that instance so not even regular users could use the UI for that customer. We detected by X, we solved by Y and then we did lessons learned and impolemented Z measure to prevent this to happen in the future.
- Proposed feature: detected recurrent API call using the BFF that implied multiuple calls to the iternal API product. Suggested to add a native endpoint in the internal API to retreive the data in one call. This was implemented and improved the performance of the BFF and reduced the load on the internal API product.
- how you measured what APIs were more or less popular? How you decide where to invest on improve performance on which endpoint or create new ones? What is the process?
- What is the most common type of issues you have to solve every day? What do you do when there's a very common and repeated problem coming to 2nd line?
- What metrics you have to assess if your measures have improved or not the status quo?