---
name: assess-job-match
description: Assess whether a job offer is a good fit for Pablo's profile, and optionally write a cover letter. Trigger words: "is this a good match", "good match", "is this a good fit", "should I apply", with a LinkedIn link or job description. For general cover letter requests (no assessment needed), use the old trigger words instead.
---

# Assess Job Match & Write Cover Letter

## Workflow

1. **Read the offer** — if the user provides a LinkedIn URL, fetch it. If the URL doesn't contain the full description, ask the user to paste it or provide an alternative source. Accept inline paste too.

2. **Read the profile** — read `index.html` and `devrel/resume-devrel.md` (or `devrel/Pablo-Antonio-Rodriguez-Rubio-DevRel.pdf` if available). These are the canonical sources for Pablo's experience and DevRel/Solutions Engineer narrative.

3. **Match check** — compare the offer against these criteria and report to the user a clear assessment:

   **Wants (must align with several):**
   - Help customers with technical problems
   - Do presentations and promote tools
   - Explain the tools
   - Design and develop demos and PoCs

   **Don't wants (should not be core to the role):**
   - Develop code that goes to production
   - Design production architecture

   **Target roles:** Solutions Engineer, Technical Solutions Engineer, Developer Advocate, DevRel, Developer Evangelist, Developer Educator, Technical Content Engineer, Technical Product Marketer, Technical Community Manager

   Also check:
   - Responsibilities match Pablo's CV experience (training, demos, documentation, API productization, ticketing, etc.)
   - Tech stack overlap with Pablo's skills
   - Location / relocation feasibility
   - Seniority level alignment
   - Any major gaps (e.g. AI/ML domain expertise if required)

4. **Present the assessment** — give the user a concise verdict (e.g. "Strong match 8/10", "Partial match 5/10", "Poor match 2/10") with bullet points on what aligns and what doesn't. End with: "Want me to write a cover letter?" Only continue if they say yes.

5. **Create the folder** — create a directory at `jobs/<CompanyName>/` (exactly as written by the user, PascalCase). If it already exists, reuse it.

6. **Write the cover letter** — save it as `jobs/<CompanyName>/Cover letter - <CompanyName>.md` with the following in the content:
   - LinkedIn offer URL at the top for identification
   - Phone, email, location, willingness to relocate
   - Honest upfront about French: professional, not native, but applying because the role excites him
   - Spanish native + English full professional as assets
   - 10 years engineering framed as pre-Solutions Engineering work
   - Specific metrics and anecdotes from N-SIDE (TYK gateway, training, docs, ticket resolution)
   - Quick learner angle (ProGuard Assembler story)
   - Link to portfolio: `https://pablorotten.github.io/cv/`
   - Videos and demos reference (from the webpage timeline section)
