# My public speaking experience

## What

https://www.n-side.com/en/news/n-side-connect-innovation-in-clinical-supplies-2025

My company organized this Gathering to attract clinical trials proffesionals. Wide range: managers, steerco, clinical data coordinators, clinical research associates, supply chain experts and Sofware Engineers working in pharma companies.


## Audience

First I analyzed the audience interests:
* Techies: architecture, endpoints, and automation
* Management: speed, cost, and error reduction

I decided to have an hourglass structure:
  * Start broad for the business stakeholders
  * Narrow down into the technical execution for the developers
  * widen out again to the strategic business impact

I assume non-tech audience will disconnect at some point of the presentation (specially step 3). So when I say something interesting for an audience group I call them "For coordinators, this can be very interesting...", "Steerco usually ask for this...", etc 

## Technical Presentation flow

Now the story:
1. Pain points: 
   * Explain the loop of a consultant using our SaaS with some examples audience would be familiar with.
2. Visual workflow:
  * Show the complete manual workflow in a visual diagram  
   * Give numbers about time spend in:
     * Execution: repetitive tasks like extracting data, input data, number of clicks to run an optimization, checking errors in the input data, etc
     * Judgement: Decision-making activities like understanding the results and changing some parameters here and there to improve the results.
     * Complex steps where human herror might happen introducing data.
  * Then update this visual workflow replacing humans with robots in the `Execution` steps
3. How it works: This part is more focused on tech audience. Keep it short but still insightful
  * Pure technical stuff: How we handle authentication, format we use, error handling, etc 
  * Show some examples of chunks of data client send to our apis and chunks of data our API send back to them. Show how many manual steps those chunks are replacing.
  * Integration: focus on how to integrate our APIs with Salesforce and SAP with some examples
4. Strategic impact: This part is more for decision-makers. I talk about ROI
  * Give numbers on:
    * How much time can be saved automating `Execution` steps
    * How much time humans can focus on `Judgement` steps


## Business presentation

A manager my deparment gave quickly insights about the busines point of view. Talked about SLAs, pricing models, partnership, etc.

## QA

This is tricky because:
1. Devs going deep: Technical audience might ask technical questions and enter in rabbit holes general audience don't find interesting
2. Unanswerable business/pricing questions: Management might ask business high level question I have no answer to.
3. Technical Misunderstanding: Some less technical savy might misunderstand a technical part and ask questions difficult to explain without technical knowledge
4. Some people might ask questions to have his "moment to shine and show how smart I am" that are out of scope. Or the even might answer themselves to it, they just want attention

First I define the framework: "We'll take questions at the end. Technical deep-dives are best handled after the session, and I'll be around for that."

How to deal with this?
1. Devs going deep: Give high level answer and acknowledge the mixed audience that might not find and extensive answer on this interesting. Invite to address this in more detail after.
2. Unanswerable business/pricing questions: As a rule: never guess if you don't have the data. We were ready for that, the manager who gave the business presentation and a sales were supporting me in the case some business questions arose.
3. Technical Misunderstanding: This is when you have to be empathic. I never say "no, that's wrong" and then explain again the same thing they didn't understand. What I do here is to try to visualise the map this person draw in their head and starting from there do some adjustments until is clear for everyone. Also praise the effort of trying to undestand that complex thing that is out of their scope and being always super supportive.