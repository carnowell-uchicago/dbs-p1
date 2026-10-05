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
