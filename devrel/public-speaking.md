# My public speaking experience

## What

https://www.n-side.com/en/news/n-side-connect-innovation-in-clinical-supplies-2025

My company organized this gathering to attract clinical trials professionals. A wide audience: managers, steering committees, clinical data coordinators, clinical research associates, supply chain experts, and software engineers working in pharma companies.

## Audience

First I analyzed the audience's interests:
- **Techies:** architecture, endpoints, automation
- **Management:** speed, cost, error reduction

I decided on an **hourglass structure**:
- Start broad for the business stakeholders
- Narrow into the technical execution for the developers
- Widen out again to the strategic business impact

I assumed the non-technical audience would tune out at some point (especially step 3). So whenever a point mattered to one group, I called them out: "For coordinators, this can be very interesting…", "Steering committees usually ask...", etc.

## Talk flow

1. **Pain points**
   - Explain the loop of a consultant using our SaaS, with examples the audience would recognize.
2. **Visual workflow**
   - Show the complete manual workflow in a diagram.
   - Give numbers on the time spent on:
     - **Execution:** repetitive tasks like extracting data, entering data, the number of clicks to run an optimization, checking input errors, etc.
     - **Judgement:** decision-making like understanding the results and tweaking parameters to improve them.
     - **Complex steps** where human error can creep in when entering data.
   - Then redraw the workflow, replacing humans with robots in the **Execution** steps.
3. **How it works** (technical audience; keep it short but insightful)
   - Pure technical details: authentication, formats, error handling, etc.
   - Show examples of the data clients send to our API and what our API sends back, and how many manual steps those replace.
   - Integration: focus on integrating our APIs with Salesforce and SAP, with examples.
4. **Strategic impact** (decision-makers; ROI)
   - Numbers on:
     - How much time automation saves on the **Execution** steps.
     - How much time humans can then spend on the **Judgement** steps.

## Business presentation

A manager from my department gave a quick business perspective: SLAs, pricing models, partnerships, etc.

## Q&A

This part is tricky because:

1. **Devs going deep:** the technical audience may ask questions and fall into rabbit holes the general audience finds uninteresting.
2. **Unanswerable business/pricing questions:** management may ask high-level questions I can't answer.
3. **Technical misunderstanding:** less technical people may misunderstand a technical part and ask questions that are hard to answer without a technical background.
4. **People who want their moment:** some ask questions just to show how smart they are — out of scope, or they end up answering themselves; they just want attention.

First I set the framework: *"We'll take questions at the end. Technical deep-dives are best handled after the session, and I'll be around for that."*

How I handle each:

1. **Devs going deep:** give a high-level answer, acknowledge the mixed audience (who won't want an extended answer), and invite the person to go deeper after the session.
2. **Unanswerable business/pricing questions:** rule — never guess without the data. We were prepared for this: the manager who gave the business presentation and a salesperson were there to back me up if a business question came up.
3. **Technical misunderstanding:** be empathetic. I never say "no, that's wrong" and then re-explain the same thing. Instead I try to picture the map the person has drawn in their head and adjust from there until it's clear for everyone. I also praise them for attempting a complex topic that's outside their scope, and stay supportive.

## Lessons learned

- **Fight a mixed audience, don't retreat from it.** A mixed audience is a challenge, not a defeat. Don't stay on the technical side and ignore the business half — use the two halves to connect to each other. Example: *"Coordinators save 4 hours a week on data entry"* is raw, technical data. Make the business connection explicit: *"By eliminating 4 hours of data entry, coordinators spend that time refining risk thresholds — preventing supply stockouts and cutting drug waste by 15%."*
- **Meet the audience where they already are.** Non-technical people still live in Excel. For the technical part, visualize the data in Excel so everyone can follow: show a huge spreadsheet, then show how it collapses into a small JSON payload a machine can process. Engaging for everyone, still technical for the developers.
- **Schedule a post-talk space for the devs.** Prepare a timeslot where developers can ask technical questions without filtering for a mixed room. Some came over informally after the talk, but it should be formal and announced.
