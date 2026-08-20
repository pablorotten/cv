---
name: add-to-portfolio
description: Add a new project, video, document, or content to the portfolio website. Trigger words: "add project", "add to portfolio", "new video", "new content", "add entry", with a link (YouTube, TikTok, Instagram, GitHub, LinkedIn, website, etc.). Always update resume-devrel.md (never resume-dev.md). Never commit - user reviews and commits manually.
---

# Add to Portfolio

## Workflow

### 1. Gather information
When triggered, extract or ask for:
- **Link(s):** YouTube, TikTok, Instagram, GitHub, LinkedIn post, website, etc.
- **Title:** Short, descriptive title for the project/content
- **Description:** 1-2 sentences explaining what it is
- **Category:** Choose from existing categories or suggest a new one:
  - `Technical Content` - tutorials, deep dives, educational videos
  - `Short` - short-form content (TikTok, Instagram Reels, YouTube Shorts)
  - `Video Demo` - project demonstrations
  - `Full-Stack Demo` - full-stack application showcases
  - `Web Innovation` - web experiments, PWAs, novel browser features
  - `Educational Content` - documentation, learning resources
  - `Technical Storytelling` - narrative-driven technical content

### 2. Determine embed format
Based on the link type, generate the correct embed:

**YouTube (full video):**
- Timeline link icon: `<iconify-icon icon="icomoon-free:youtube2"></iconify-icon>`
- Embed iframe: `https://www.youtube.com/embed/{VIDEO_ID}?si={SHARE_ID}`
- Extract video ID from URL: `https://www.youtube.com/watch?v={VIDEO_ID}` or `https://youtu.be/{VIDEO_ID}`

**YouTube Short:**
- Timeline link icon: `<iconify-icon icon="icomoon-free:youtube2"></iconify-icon>`
- Embed iframe: `https://www.youtube.com/embed/{VIDEO_ID}`
- Note: Shorts may not embed properly; link to watch page instead

**TikTok:**
- Timeline link icon: `<iconify-icon icon="simple-icons:tiktok"></iconify-icon>`
- Embed iframe: `https://www.tiktok.com/embed/v2/{VIDEO_ID}`
- Extract video ID from URL path

**Instagram Reel/Post:**
- Timeline link icon: `<iconify-icon icon="skill-icons:instagram"></iconify-icon>` (for reels) or `<iconify-icon icon="bi:instagram"></iconify-icon>` (for posts)
- Embed iframe: `https://www.instagram.com/reel/{shortcode}/embed` or `https://www.instagram.com/p/{shortcode}/embed`

**GitHub:**
- Timeline link icon: `<iconify-icon icon="octicon:lockup-github-16"></iconify-icon>`
- No embed iframe; just a link

**LinkedIn Post:**
- Timeline link icon: `<iconify-icon icon="logos:linkedin"></iconify-icon>`
- Embed iframe: `https://www.linkedin.com/embed/feed/update/{POST_URN}?collapsed=1`

**Website/Live Demo:**
- Timeline link icon: `<iconify-icon icon="mdi:web"></iconify-icon>` or custom label
- Embed iframe: use the website URL directly

**X/Twitter:**
- Timeline link icon: `<iconify-icon icon="bi:twitter-x"></iconify-icon>`
- No standard embed; just a link

### 3. Generate HTML
Create a new `<div class="timeline-item">` block following the exact structure:

```html
<div class="timeline-item">
  <div class="timeline-dot"></div>
  <div class="timeline-content">
    <span class="category">{CATEGORY}</span>
    <h4>{TITLE}</h4>
    <p>
      {DESCRIPTION}
    </p>
    <div class="timeline-links">
      <a
        href="{URL}"
        class="timeline-link"
        target="_blank"
        rel="noopener noreferrer"
        >{ICON_OR_LABEL}</a
      >
    </div>
    <div class="embed-container">
      <iframe
        src="{EMBED_URL}"
        title="{ACCESSIBLE_TITLE}"
        frameborder="0"
        scrolling="no"
        allowfullscreen
        allow="encrypted-media"
      ></iframe>
    </div>
  </div>
</div>
```

**Important HTML rules:**
- Always include `target="_blank" rel="noopener noreferrer"` on external links
- Use `class="timeline-link"` on all timeline link elements
- Place embed in `<div class="embed-container">` for responsive sizing
- YouTube iframes get `allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"` and `referrerpolicy="strict-origin-when-cross-origin"`
- TikTok/Instagram iframes get `scrolling="no"`

### 4. Insert into index.html
- Read `index.html`
- Insert the new `<div class="timeline-item">` block **before** the first `</div>` that closes the `timeline-container` div (after the last existing timeline item)
- The new entry appears at the top of the portfolio (most recent first)

### 5. Verify
After editing, check:
- HTML is properly formatted (no unclosed tags)
- Links are correct
- Embed URLs are properly constructed
- The new entry follows the visual pattern of existing entries

### 6. Update resume
- Read `devrel/resume-devrel.md`
- Add a brief mention in the relevant section
- Keep it concise (one line)
- Do NOT touch `dev/resume-dev.md`

### 7. Numbering
- New entries become P1 (most recent), existing entries shift: P1→P2, P2→P3, etc.
- Numbering is implicit in the timeline order (top = most recent = P1)

### 8. Commit
- **NEVER commit.** User reviews changes and commits manually.
