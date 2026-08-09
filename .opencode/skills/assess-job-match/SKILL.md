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

**Scoring factors (直接影响分数):**
- Role type alignment: DevRel/Developer Advocate/Developer Evangelist = highest; SE with DevRel duties = high; pure SE = medium; pure SWE/support = low
- "Bridge" framing between engineering and users/developers -- Pablo's core narrative
- Presentations, demos, workshops, technical talks, conference speaking
- Documentation, tutorials, API references, content creation
- Developer community engagement (GitHub, Discord, forums, social channels)
- Tech stack overlap: Python, JS/TS, React, REST APIs, GraphQL, Postgres, Git
- Language requirements: Spanish/English = perfect; French = bonus; German/Dutch/Arabic/Portuguese = hard gates that lower score
- Domain expertise gates: cybersecurity, fintech/lending, geospatial, broadcast, telecom, defense, K8s/MLOps, crypto, DAM/PIM, airline, contact center = lower score unless "nice to have" not "required"
- Seniority alignment: senior/staff level fits; "5+ years in [specific niche]" may be a gate
- Production coding emphasis: if role requires shipping production code as primary duty, lower score

**SE-with-DevRel-duties rule:**
If the title is Solutions Engineer but the description includes significant DevRel-like duties (developer enablement, content creation, community engagement, conference speaking, documentation ownership), BOOST the score by 1-2 points and explicitly mention this in the summary as "SE with strong DevRel overlap -- worth careful application."

**Warning factors (mention, do NOT factor into score):**
- Location / relocation requirement (mention but do NOT factor into score)
- On-site vs hybrid vs remote (mention but do NOT factor into score)
- Applicant count (100+ applicants = mention but do NOT factor into score)
- Contractor vs FTE (mention but do NOT factor into score)
- Company size / stage (mention but do NOT factor into score)

**Don't wants (should not be core to the role):**
- Develop code that goes to production
- Design production architecture
- Pure backend/frontend SWE without customer-facing component
- Technical support without developer advocacy or bridge work

**Target roles:** Solutions Engineer, Technical Solutions Engineer, Developer Advocate, DevRel, Developer Evangelist, Developer Educator, Technical Content Engineer, Technical Product Marketer, Technical Community Manager

### 4. Present assessment
Give a concise verdict (e.g. "Strong match 8/10", "Partial match 5/10", "Poor match 2/10") with bullet points on what aligns and what doesn't.

**Include in every assessment:**
- Match score with verdict label
- ⚠️ Warning section (location, applicant count, contractor, etc.) -- clearly separated from scoring
- What aligns (bullet points)
- What doesn't / gaps (bullet points)
- Application strategy recommendation:
  - **DevRel roles (score ≥ 6):** "Careful apply -- study product, make video, special CV"
  - **SE roles (score ≥ 6):** "Standard apply"
  - **SE with DevRel overlap (score ≥ 6):** "Careful apply -- SE title but DevRel duties, worth the extra effort"
  - **Score < 6:** "Skip" or "Borderline -- your call"

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

## Application Strategy

Pablo has two application modes. Recommend the appropriate one based on the assessment:

### DevRel roles (careful apply)
- **When:** DevRel, Developer Advocate, Developer Evangelist, Developer Educator roles with score ≥ 6/10
- **Also when:** SE title but duties are heavily DevRel-adjacent (developer enablement, content creation, community, docs ownership)
- **Process:**
  1. Study the company's product deeply -- use it, explore APIs, understand positioning
  2. Guess what they want to promote most (new features, key differentiators)
  3. Make a video demonstrating the product and explaining how it works / how good it is
  4. Prepare a special CV tailored to the role
  5. Write a targeted cover letter
  6. Apply with all materials
- **Target pace:** 1 per week (up from 1 per month)
- **Goal:** Show genuine interest and capability, stand out from other applicants

### SE roles (standard apply)
- **When:** Solutions Engineer, Technical Solutions Engineer roles with score ≥ 6/10 and no significant DevRel overlap
- **Process:**
  1. Save entry if user wants
  2. Write cover letter if user wants
  3. Apply through normal channels
- **Note:** SE is a stepping stone toward DevRel. Getting an SE job is still a win.

### Skip
- **When:** Score < 6/10, or user decides it's not worth pursuing
- **Process:** Acknowledge and move on
