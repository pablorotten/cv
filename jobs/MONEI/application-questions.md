# MONEI - application questions

## Q1. Content born from real developer pain. Min 800 chars.

Pick **one piece of content** you personally published — a doc page, blog post, tweet/thread, video, talk, or repo README — that was directly **triggered by a real developer issue or recurring pain point**. Then tell us:

- **The content** — link to it
- **What sparked it** — was it a single support ticket, a recurring pattern across many users, a thread you saw on X, a confused colleague? Be specific about how the pain surfaced.
- **What you did between sparking and publishing** — debugging, code reading, talking to the user, prototyping a fix, writing a runbook
- **What the content did** — engagement, follow-up tickets that stopped, "this saved my life" replies, internal team adoption.

> [!TIP]
> Pick the Tyk Gateway vs BFF video: https://www.youtube.com/watch?v=d8GkpmMJqsI
>
> Spark = the N-SIDE API work and the recurring support mail. Not a tweet.
>
> Middle = built the API, answered the mail, wrote the docs and screencasts, THEN recorded the video. The video is the last step, not the first.
>
> Docs killed the tickets. The video is the public proof. Don't swap those.
>
> Skip Movie Kombat, PearNote, GuardSquare, Vercel email.
>
> 800 characters is about 130 words. Four short paragraphs, then stop.

**Answer:**

```
# If you implement an API you'll need a gateway, but probably you'll need a BFF... and I didn't know that.

Recently, and with recently I mean 2 days ago, I did a video talking about a topic that matches wit this. There's also a bunch of internal presentations, demos and documentation I did for my company but I can't share this with you. But there's a video I did in youtube about that topic.

- What sparked it

We had the idea of building an API for our SaaS, so robots could also connect with the tool and use it. 

We partnered with 1 customer who was really excited about this topic since they automated many processes and our human-centered SaaS was a blocker for them. So we designed an API and they tested it, we iterated a lot until they gave us green light. 

But our bottleneck was our SaaS release pipeline. At that time was reeeeeeally slow. Like 1 month to release anything (fortunately, not the case anymore). This was unnaceptable for our partner so we chose TYK as gateway for setting up quotas, rate limits, authentication... and for their virtual endpoints (https://tyk.io/docs/api-management/traffic-transformation/virtual-endpoints)  

This feature is meant to reshape and make minor modifications to the data before sending back to the client... and this was the case in the begining. But after a few iterations it exploded and was a mess to modify, to test and to keep track of the versioning.

- What you did between sparking and publishing

Once we had an "stable" version of the API for this client I led a "lessons learned" explaining our API trip, the good and the bad decisions and all the problems we had. In that session the BFF idea sparked. BFF stands for "Backend For Frontend", it's a small app that stands between the core SaaS and the Gateway to handle all the data. I investigated this pattern, implemented it and it was a success.

- What the content did

I wrote documentation, made videos and presentation of why implement a BFF is good and then all the teams started to implment BFF instead of overloading the Gateways. This BFF become a thing for all our teams, many of them adopted it and now it's part of our pipeline everytime we need to build an API.
```

## Q2. Top 3 educational posts.

Share **3 of your best educational posts/threads/videos from the last 12 months** — Twitter/X, LinkedIn, dev.to, YouTube, anywhere. For each:

- The link
- The metric you're proudest of (likes, replies, "saved my life" comments, citations from elsewhere)
- **One sentence on why you think it landed** — what made it good, not just what it was about

> [!TIP]
> Three URL fields, all required. Put one URL in each.
>
> Last 12 months only. Fake Tinder is out.
>
> Don't reuse the Tyk BFF video, it's already Q1.
>
> Metric: open the post and copy the real number. Views, impressions, a reply. Don't invent "saved my life."
>
> The one sentence is the *why it landed*, not the topic.
>
> The text field is a single-line input, not a textarea. Keep it to three short bullets.

**Answer:**

```
- https://www.youtube.com/watch?v=mUKR67VA0Lg 
  - Title: Beyond the Bytecode: Solving OWASP UnCrackable L1 with Guardsquare's Proguard Assembler 
  - YT: 138 views in 6 months
  - LinkedIn: 422 impressions
- https://lnkd.in/p/eV4A95ez 
  - Title: Vercel has no email. Found Amelu, an Ordnary tool, to solve this.
  - LinkedIn: 465 impressions
- https://www.youtube.com/watch?v=B8783WSrCjI
  - Title: What If Your App Had No Server, No Database, No Accounts? = Holepunch Stack Explained
  - YT: 131 views
  - LinkedIn: 333 impressions

I can't answer this properly because this form has 1 single input field for all 3 posts, not even a textarea. Anyway, I'm proud of those videos because I manage to explain complex topics in a simple and fun way. They have rookie numbers: like average 400 impressions in LinkedIn and 130 views in YouTube, but I think they are good examples of my work. The oldest one is 6 month old, when I started with this DevRel adventure. 
```

## Q3. Long-form deep-dive.

Link to **one long-form piece** you wrote/recorded that taught a concept well — a blog post, video, conference talk, multi-tweet thread, technical doc, or detailed GitHub README. Then in ~150 words: **what made this one land?** What was the pedagogy — the structure, the analogy, the diagram, the order of revelation?

> [!TIP]
> Do NOT reuse the Tyk BFF video. It's already Q1.
>
> Best candidate: the GuardSquare / ProGuard Assembler video. Long-form, teaches something hard, and you built the thing before writing about it.
>
> Alternative is the Vercel email post, but it's narrower and shorter.
>
> The 150 words are about **method, not topic**. They name four things: structure, analogy, diagram, order of revelation. Use the ones you actually used.
>
> Your strongest angle: you learned the toolchain by using it, so the content follows the path a reader would have to take. Each step earns the next. That's the pedagogy.
>
> Don't describe what ProGuard Assembler does. They can read the video.
>
> Don't use "clear", "accessible" or "engaging" as the explanation. Show the mechanism instead.
>
> Don't claim you knew it beforehand. The opposite is your best material.

**Answer:**

```
```
