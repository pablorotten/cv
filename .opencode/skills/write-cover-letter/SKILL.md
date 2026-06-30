---
name: write-cover-letter
description: Use when the user asks you to write a cover letter for a job offer. Trigger words: "write a cover letter", "cover letter", "cover letter for", "apply to". Do NOT use for general job search questions or resume edits.
---

# Write a Cover Letter

## Workflow

1. **Read the offer** — fetch the LinkedIn URL the user provides. If the URL doesn't contain the full description, ask the user to paste it or provide an alternative source.

2. **Read the profile** — read `index.html` and `devrel/resume-devrel.md` (or `devrel/Pablo-Antonio-Rodriguez-Rubio-DevRel.pdf` if available). These are the canonical sources for Pablo's experience and DevRel/Solutions Engineer narrative.

3. **Match check** — compare the offer against these criteria and report to the user which match and which don't:

   **Wants (must align with several):**
   - Help customers with technical problems
   - Do presentations and promote tools
   - Explain the tools
   - Design and develop demos and PoCs

   **Don't wants (should not be core to the role):**
   - Develop code that goes to production
   - Design production architecture

   **Target roles:** Solutions Engineer, Technical Solutions Engineer, Developer Advocate, DevRel, Developer Evangelist, Developer Educator, Technical Content Engineer, Technical Product Marketer, Technical Community Manager

   Also check if the responsibilities match Pablo's CV experience (training, demos, documentation, API productization, ticketing, etc.).

4. **Ask to proceed** — present the match analysis to the user and ask: "This looks like a [good / partial / poor] match. Do you want me to write the cover letter?" Only continue if they say yes.

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
