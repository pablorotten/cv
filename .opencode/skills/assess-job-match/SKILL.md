---
name: assess-job-match
description: Assess whether a job offer is a good fit for Pablo's profile, optionally save the job details, and optionally write a cover letter. Trigger words: "good match", "is this a good match", "is this a good fit", "should I apply", with a LinkedIn link and/or job description.
---

# Assess Job Match & Write Cover Letter

## Workflow

### 1. Read the offer
If the user provides a LinkedIn URL, try to fetch it. If the URL doesn't contain the full description, ask the user to paste it or accept inline paste.

### 2. Read the profile
Read `dev/resume-dev.md` and `devrel/resume-devrel.md` for Pablo's experience and narrative.

### 3. Match check
Compare the offer against these criteria and give a clear assessment:

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
- Any major gaps

### 4. Present assessment
Give a concise verdict (e.g. "Strong match 8/10", "Partial match 5/10", "Poor match 2/10") with bullet points on what aligns and what doesn't.

### 5. Ask to save job details
If the match is reasonable (partial or better), ask: "Want me to save this job to a new entry?"
If yes:
- Create folder `jobs/<CompanyName>/` (PascalCase, exactly as user provides the company name)
- Create `jobs/<CompanyName>/<name-of-company>.md` (lowercase kebab-case) with:
  - LinkedIn URL
  - Full job description (paste what user provided)
  - Any trivia or notes the user wants to save

### 6. Ask about cover letter
After saving (or if user says no to saving), ask: "Want me to write a cover letter?"
If yes:
- Save as `jobs/<CompanyName>/Cover letter - <CompanyName>.md`
- Include at the top: ## Headline and ## Summary sections
- Content guidelines:
  - LinkedIn offer URL for identification
  - Phone, email, location, willingness to relocate
  - Honest about gaps where applicable
  - Spanish native + English full professional + other languages as assets
  - 10+ years engineering framed as Solutions Engineering work
  - Specific metrics and anecdotes from N-SIDE (TYK gateway, 80% ticket reduction, training for 50+ consultants, Argo automation, troubleshooting guides)
  - Quick learner angle (ProGuard Assembler story)
  - Link to portfolio: `https://pablorotten.github.io/cv/`
- **Never use the em dash character (—). Always use a regular hyphen (-) instead.**

### 7. Handle application screening questions
If the user provides application screening questions from the job portal, save them as `jobs/<CompanyName>/application-questions.md` with the questions and notes on how to answer / what stories to prepare.
