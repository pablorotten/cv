# Aircall - Interview Prep

Role: Customer Engineer / Staff Customer Engineer - Iberia & FIME (Madrid, hybrid)
Contact: Marie Mas (recruiter) - 30-min video screen

---

## What Aircall does (know this cold)

**One line:** Aircall is a cloud phone system for customer-facing teams - voice, SMS, and WhatsApp in one workspace, with AI on top - that captures every call as data and pushes it into the tools a company already uses.

**Who buys it:** any company with a phone-heavy customer motion - sales (SDRs/AEs calling out), support/contact centers, and general ops. 22,000+ companies, SMB through enterprise. Strong in Europe: Paris HQ, big Madrid hub.

**The value stack (5 layers):**
1. **Run the calls** - cloud telephony: routing, IVR, queues, transfers, agent availability. Entry point for many buyers is "our phones are a mess."
2. **Capture** - recording, transcript, and metadata (number, duration, direction, agent, tags) on every call.
3. **Context** - screen-pop, click-to-call, and full interaction history on the contact/deal/ticket in the CRM.
4. **Automate** - flows and the AI Voice Agent handling routine calls.
5. **Analyze** - dashboards and AI on top of the captured data.

**Products:**
- **Core platform:** voice, SMS, WhatsApp; numbers, call routing/queues, IVR, voicemail, recording.
- **Integrations:** native connectors for Salesforce, HubSpot, Pipedrive, Zendesk, Intercom, Freshdesk, Slack + 100 more. Public REST API + webhooks for custom work. Everywhere SDK to embed the softphone inside a CRM. Insight Cards show CRM data during a call.
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

**Clean version:**
> "Aircall is a cloud phone system that captures every call as data, ties it to the right contact, pushes it into the tools a team already uses (CRM, Slack, ticketing), and layers AI on top to summarize, structure, and even handle calls. The phone number is the key, the CRM is the record, Aircall is the engine in between."

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

"I'm a software engineer who spent the last five years building an API platform and then supporting the customers who used it. I designed ~20 endpoints, took the product from PoC to production, onboarded five customers, wrote all the external docs and tutorials, and handled their technical issues directly. So I sit exactly where Aircall puts a Customer Engineer - between the product/engineering side and the customer."

Then pivot to Aircall: "Aircall is doing that same bridge with a much bigger surface - voice, SMS, WhatsApp, and now AI agents. That's the work I want to be doing."

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

---

## 5. Likely questions + angles

**Motivation / fit**
- "Why Aircall, why Customer Engineering?" -> The bridge role is literally what you did at N-SIDE; Aircall adds voice/SMS/WhatsApp/AI scale. Mention Madrid + languages.
- "You're a developer - why customer-facing?" -> You did both 50/50 and chose the customer side; you like translating complex tech into outcomes.

**Customer craft (very likely even at screen)**
- "Tell me about a time you turned a challenging customer around." -> integration friction story, docs + hands-on support.
- "Describe where you drove adoption of a product/feature." -> N-SIDE API adoption, screencasts, data extraction.
- "How do you handle a feature request that's not on the roadmap?" -> understand the underlying problem first, workaround if possible, champion the business case, follow up.
- "Walk me through a hard technical problem you solved." -> API/webhook integration debugging; use a structured troubleshooting approach (reproduce -> hypothesis -> isolate one variable -> update customer throughout -> escalate when stuck).

**Technical literacy**
- "Explain APIs/webhooks to a non-technical person." -> restaurant analogy: API = ordering from a menu; webhook = the kitchen texts you when your order is ready instead of you checking the counter.
- "How would you debug a customer integration that stopped working?" -> check what changed, logs on both sides, auth/token expiry, endpoint returning 2XX in time, webhook delivery/retries.
- "Experience with CRMs (Salesforce/HubSpot)?" -> be honest; connect it to integration mindset: screen-pop, call logging, field mapping.

**Behavioral**
- Cross-functional influence, conflict, ownership beyond your job, prioritising a large portfolio, staying calm in escalations.

---

## 6. Domain crash course (do this before the screen)

**VoIP / telephony basics**
- SIP = signalling protocol; RTP = carries audio; PSTN = the traditional phone network.
- DID = your Aircall phone number. Number provisioning and porting.
- IVR = the "press 1 for sales" menu. Call routing / call flows. Queues, ring strategy, voicemail, call recording.
- Why it's hard: latency/jitter, codecs, NAT/firewalls, compliance (call-recording consent, GDPR).

**Contact-center vocabulary**
- Agent, queue, AHT (average handle time), FCR (first call resolution), abandon rate, CSAT, occupancy/SLA. Know these so you sound native.

**Aircall platform specifics**
- Product: one workspace for voice, SMS, WhatsApp, AI. AI Voice Agent (automates routine calls), AI Assist (post-call work), AI Assist Pro (real-time guidance). Smartflows = current routing engine (replacing legacy routing).
- **Public API:** REST at `api.aircall.io/v1`, HTTPS only, OAuth2 access tokens. User V1 deprecated, removed 30 Sep 2026 -> build on User V2.
- **Webhooks:** register from the Dashboard or `POST /v1/webhooks`; events include `call.created`, `call.ended`, `call.tagged`, `call.commented`, `contact.*`, `user.opened/closed`, `message.*`, `ai_voice_agent.started/ended/escalated`, `realtime_transcription.utterances_received`, `custom_summary.*`, `call_evaluation.*`. Max 100 webhooks/account. Must return 2XX (ideally 200) within 5s; auto-disabled after 10 failed deliveries. Each webhook has a unique token to verify origin.
- **CNI:** integrations are enabled at Company level by an Admin; multiple instances allowed.
- **Everywhere SDK:** embeds the softphone/CTI into a CRM (V1 deprecated, use V2).
- **Insight Cards:** surface up to 5 fields from a CRM object in the agent's in-call view.
- **Native integrations:** Salesforce (v3 with Aircall Log object), HubSpot, Pipedrive, Zoho, Zendesk, Intercom, Freshdesk, Slack + 100 more. One-click install, call logging, screen-pop, field mapping.

**Aircall values (mirror this language):** customer-obsessed, data-driven, ownership, continuous learning, "thoughtful speed", collaborative, fast-moving.

---

## 7. Questions to ask her

1. "Is this the same opening as the Customer Engineer role, leveled differently, or a separate Staff req? And is the CE role also still open?"
2. "What does the Customer Engineering team in Madrid / Iberia & FIME look like today?"
3. "How is a CE measured - onboarding, adoption, renewals, AI add-on activation?"
4. "What does success look like in the first 90 days?"
5. "What's the biggest challenge the CE team is facing right now?"
6. "Which customer segments would I focus on, and what do their tech stacks typically look like?"
7. "What's next in the process after this call?"

---

## 8. Logistics & first-impression checklist

- [ ] Test camera, mic, and connection 10 min before.
- [ ] Quiet room, clean/neutral background, good light.
- [ ] Have the JD, this doc, your resume, and 2-3 STAR stories on screen (not visible to camera, but within reach).
- [ ] One-page note card: your narrative sentence, the level script, and 3 numbers (~20 endpoints, 5 customers, new business line).
- [ ] Speak slowly; English is a second language - fluency is fine, just don't rush.
- [ ] Confirm Madrid/hybrid + languages early ("I'm based in Belgium but Spanish native and happy to relocate" - confirm your actual situation).
- [ ] Ask about salary expectations: defer politely if possible ("I'd love to understand the band for the level first").

---

## 9. One-line summary to keep in your head

"Technical enough to build the integration, customer-facing enough to make it succeed, and honest about learning the telephony and enterprise-commercial parts."


## Stuff to add to the document

### What I did in n-side

- L0 - self-service: KB articles / docs / videos (this is what you wrote at N-SIDE for the API)
- L1 - first line: triage, known issues, route or solve the easy ones (now AI + a human supervising)
- L2/L3 - you: the technical/integration problems that got escalated, plus product feedback back to engineering

"Customers submitted issues through a ticket portal. A first line triaged them; I handled the escalated technical and integration issues as the second line. I also wrote the API documentation and tutorials that reduced the volume reaching us, and I fed recurring themes back to Product."

 intake -> triage -> escalation ownership -> knowledge/self-service -> product feedback.


### What can do with Aircall

 IVR (Interactive Voice Response)