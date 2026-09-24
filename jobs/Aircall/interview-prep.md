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

## 4. STAR stories to prepare (use your real work)

Map these to whatever she asks. Always end on the outcome or business value.

| Competency they test | Your story | Outcome to land |
|---|---|---|
| Ownership / PoC to production | N-SIDE API branch: started as a PoC for one client, iterated to a full product | Adopted by all existing accounts, 5 new customers integrated |
| Driving adoption | Guided clients through integration with screencasts, hands-on support, docs | Lower integration friction, fewer support emails |
| Commercial/expansion instinct | Spotted bulk data extraction used internally, turned it into a sellable product | New profitable business line |
| Solution architecture / technical depth | Built API infrastructure on the TYK gateway, designed internal docs + automation | Scalable platform, repeatable onboarding |
| Quick learner / calm under pressure | GuardSquare ProGuard Assembler: learned a niche tool and shipped a public technical video | Shows you learn new domains fast (relevant for VoIP/telephony) |
| Cross-functional influence | Worked between customers and Product/Engineering to shape API features; Kanban lead running standups | Shipped the right endpoints, smoother delivery |
| Troubleshooting complex issues | Debugging customer integration/webhook issues against the API | Root cause found, customer unblocked, docs improved so it didn't recur |
| Honest handling of a missing feature | Customer request not on roadmap - found a workaround, logged the business case | Trust kept, request championed internally |

**Tip:** for the "customer-facing" ones, always state who the customer was (pharma supply-chain / clinical-trial customers), and quantify where you can.

### Support-flow story (N-SIDE)

Use this for "tell me about a support / technical problem" questions.

- **L0 - self-service:** KB articles / docs / videos (what you wrote at N-SIDE for the API).
- **L1 - first line:** triage, known issues, route or solve the easy ones (now AI + a human supervising).
- **L2/L3 - you:** the technical/integration problems that got escalated, plus product feedback back to engineering.

> "Customers submitted issues through a ticket portal. A first line triaged them; I handled the escalated technical and integration issues as the second line. I also wrote the API documentation and tutorials that reduced the volume reaching us, and I fed recurring themes back to Product."

Flow: intake -> triage -> escalation ownership -> knowledge/self-service -> product feedback.

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
- **Staff CE:** telephony domain, enterprise/exec + commercial, seniority.
- **Regular CE:** telephony domain, CRM hands-on, French.

### Opening template

> "No, I don't think anyone fits 100% - and I'd rather be straight with you. There are a couple of areas where I'd be ramping up, mainly the telephony side and the enterprise layer. Can I tell you how I'd go at them?"

### The gaps

**1. Telephony / VoIP / contact-center domain**
- **Formulate:** "The biggest one is the domain. I've spent my career in APIs, integrations, and platforms - not VoIP. SIP, call flows, contact-center metrics like AHT - those are newer to me."
- **Propose to her:** "I'd want a structured ramp: your product bootcamp, shadowing a senior CE through two or three onboardings, and pairing on live escalations. I pick up domains fast - I've done exactly that before."

**2. Enterprise / strategic accounts & exec stakeholders**
- **Formulate:** "Most of my customers were mid-market and technical users. I haven't spent much time in front of CTOs or Heads of CX."
- **Propose to her:** "Let me shadow a senior CE or the hiring manager on a couple of enterprise accounts and a QBR before owning my own. I'm comfortable in the room - I just need the exposure."

**3. Commercial ownership (renewal, GRR/NRR, QBRs, expansion)**
- **Formulate:** "I've built the product and driven adoption, but I haven't owned renewal or expansion numbers."
- **Propose to her:** "Sit me in on a full renewal cycle and a QBR with a KAM first, so I learn how you articulate ROI and read the signals. I understand the technical levers that drive renewal - I just haven't owned the commercial outcome."

**4. CRM platforms (Salesforce / HubSpot)**
- **Formulate:** "I've only briefly used Salesforce day-to-day - my environment was Jira, Slack, and Google."
- **Propose to her:** "Put me in the CRM with your enablement and the connectors in my first weeks. I understand the integration model - screen-pop, call logging, field mapping - I just need hands-on time in the tool."

**5. Agentic AI voice / messaging workflows**
- **Formulate:** "I haven't deployed a voice agent hands-on."
- **Propose to her:** "Pair me with the FDE/AI team on a real AI Voice or AI Assist Pro deployment, and I'll build a demo of my own to get fluent. This is the area I'm most excited to grow into."

**6. Seniority / CE-years at Staff level**
- **Formulate:** "The Staff bar is 8+ years in customer engineering. I'm at about five years of direct SE work, on top of ten total in engineering."
- **Propose to her:** "I'm flexible on level - if it fits better, put me in the senior CE seat and let the work make the case for Staff. I'd rather earn it in the role than argue about the title."

**7. Mentoring at Staff scale**
- **Formulate:** "I've led a Kanban team and onboarded and documented, but I haven't mentored a team of CEs."
- **Propose to her:** "I'd start by running enablement sessions and tightening documentation, and ask the team where the technical standards need raising most."

**8. French (only if it lands on the regular CE role)**
- **Formulate:** "My French is professional, not fluent - if the regular Customer Engineer role needs full French, that's a real gap for me."
- **Propose to her:** "Spanish and English are fully covered, and I'd get my French to working level quickly given the base I have."

### Framing rules

- Never answer "100%."
- Name 2-3 gaps maximum - the real ones for this role. Don't recite all eight.
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
