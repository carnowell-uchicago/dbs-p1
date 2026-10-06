## Project Idea 
A webpage (one page) that tells and/or reimagines the story of the three little pigs.
A reimagining could change the characters or what is happening to them without changing the key plot points.

## Audience
The page should appeal to both children and audience with the purpose of making the story exciting again.

## Functionality
A visitor should be able to work through the story at their own pace. They should be able to go back if they miss something.

## Claude

### Assignment context
- Course: Design, Build, Ship · MPCS 51238 · Autumn 2026 (due Oct 6, 5:30 PM)
- Build 25 versions of the Three Little Pigs page + 1 gallery page (index.html)
- Deploy on Vercel, code on GitHub with commits showing real iteration
- Graded on breadth of exploration, decision-making, and how well the story is told in the gallery
- Challenge: at least 20 of 25 designs must look completely unique vs. ~700 other student sites

### Tech constraints (hard rules)
- Plain HTML + CSS + optional vanilla JS only
- No frameworks (React, Vue, etc.), no build step, no npm packages, no external APIs
- If tempted to add a framework or package: don't

### File structure
- `index.html` — gallery page showing all 25 versions with thumbnails, short note per version, and final pick
- `v01/index.html` through `v25/index.html` — one folder per version
- Each version page must have a link back to the gallery
- Commit after each version so git history shows real iteration

### Story: key plot points to always preserve
1. Three siblings (pigs, or reimagined characters) each build a shelter of different strength
2. A threat (wolf, or reimagined antagonist) tries to destroy each shelter in sequence
3. The first two shelters fail; the third (strongest) holds
4. The three siblings end up safe together in the strongest shelter
The reimagining can swap pigs → astronauts, wolf → asteroid, straw/sticks/bricks → any three tiers of material or defense.

### Navigation requirement
Every version must let a visitor work through the story at their own pace with clear forward/back controls — no auto-advancing, no forced scrolling without a way to go back.

### Dual audience
Designs must feel engaging to both young children (visual, playful, clear) and adults (interesting, not condescending). Avoid pure baby-toy aesthetic unless it has a self-aware or ironic layer.

### What counts as a new direction (not just colors/fonts)
Layout structure, narrative format, era/setting, tone, design school, reading mode, or genre — e.g.:
- Magazine spread · brutalist manifesto · children's picture book · horror · sci-fi · western · corporate satire
- Newspaper front page · vintage scroll · game UI · comic strip · film poster · nature documentary
- Recipe card · breaking news alert · social media feed · zine/DIY · medieval manuscript · superhero origin

### Exploration arc
- v01–v08: go wide — radically different directions, no two should feel alike
- v09–v16: notice what works for the audience, start combining promising elements
- v17–v22: converge — mix typography from one with layout from another, tighten
- v23–v25: refinements only, v25 should feel definitive

### Gallery page requirements
- Thumbnail (screenshot or representative preview) for each version
- One-sentence note per version: what direction was tried and what worked or didn't
- Final version clearly marked as the chosen one
- Every thumbnail links to its version; every version links back to gallery

## Context

### Deployment & local dev
- GitHub repo: `https://github.com/carnowell-uchicago/dbs-p1` (remote: `origin`)
- Vercel is connected to that repo — every push to `main` auto-deploys; no manual deploy step needed
- Local preview: run `python3 -m http.server 8080` from `/Users/jacob/projects/p1`, open `http://localhost:8080`
- The assignment PDF (`Design, Build, Ship - Assignment 1 - Accelerated Prototyping.pdf`) is in the project folder but must NOT be committed to git
- Workflow: build a version → user approves → commit specific files by name → push → repeat

### Commit discipline (IMPORTANT)
After every user-approved change — whether a new version, an edit to an existing version, or a gallery update — commit immediately before moving on. Stage only the specific files changed (never `git add -A`). Never leave work uncommitted between prompts. Push after committing when auth allows; if push fails, note it and let the user push manually (`! git push`).

### Gallery card activation
Each card in `index.html` starts as `<a class="card placeholder" ...>`. When a version is built and approved:
1. Remove `placeholder` from the class
2. Replace the `<span class="vnum">` placeholder with `<iframe src="vNN/" ...></iframe>` inside `.thumb`
3. Fill in `.title` and `.note`
For the final chosen version, also add class `final` to the card.

### Current progress
- `index.html` (gallery) — committed
- `v01/` — **built, not yet committed** (awaiting final approval)

### v01 design decisions
Direction: brutalist manifesto, half-screen flip book
- 6 panels: title → preface → straw → sticks → bricks → conclusion
- Wolf dialogue in bold red; verdicts ("It fell." / "It stood.") are the typographic punch
- Layout: `.wrapper` (centered, `min(900px, 90vw)`) → `.book-frame` (full wrapper width, left/top/bottom border + center spine line) → `.book` (perspective container) → `.panel` (50% wide, left half, `transform-origin: right center`)
- Flip mechanic: `rotateY(180deg) → rotateY(0deg)` for forward (new page covers current), `rotateY(0deg) → rotateY(180deg)` for backward (current peels away). No `backface-visibility: hidden` — the full arc is intentional so the free edge peaks toward the viewer at 90°.
- Z-index stack: visited pages stay rendered at their assigned z-level; forward increments `zCounter`; backward resets the outgoing page to z=0/opacity=0 so it can flip in again
- Nav sits below `.book-frame`, width 50% of wrapper (aligns under left page), all three controls (Back / counter / Next) visible
