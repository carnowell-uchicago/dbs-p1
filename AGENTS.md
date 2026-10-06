## Project Idea 
A webpage (one page) that tells and/or reimagines the story of the three little pigs.
A reimagining could change the characters or what is happening to them without changing the key plot points.

## Audience
The page should appeal to both children and adults with the purpose of making the story exciting again.

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

### Build workflow for new versions
When building a new version, split work between two subagents launched in parallel:
- **Backend agent**: `vNN/index.html` — all HTML, CSS, and JS
- **Assets agent**: `vNN/assets/*.svg` — all SVG illustrations and icons

Before launching, decide on exact asset file paths and include them in both prompts so the backend can reference them and the assets agent writes to those exact names. The parent session merges the results after both complete.

### Commit discipline (IMPORTANT)
After every user-approved change — whether a new version, an edit to an existing version, or a gallery update — commit immediately before moving on. Stage only the specific files changed (never `git add -A`). Never leave work uncommitted between prompts. Push after committing when auth allows; if push fails, note it and let the user push manually (`! git push`).

**Subagents must NOT commit.** Subagents build and write files only. The parent Claude Code session commits after the user reviews and approves the result. A subagent that commits on its own violates this workflow.

### Gallery card activation
Each card in `index.html` starts as `<a class="card placeholder" ...>`. When a version is built and approved:
1. Remove `placeholder` from the class
2. Replace the `<span class="vnum">` placeholder with `<iframe src="vNN/" ...></iframe>` inside `.thumb`
3. Fill in `.title` and `.note`
For the final chosen version, also add class `final` to the card.

### Gallery thumbnail check (IMPORTANT)
After activating every new gallery card, always verify the thumbnail actually renders correctly in the browser at `http://localhost:8080`. Versions with complex fixed layouts (sticky headers, full-viewport JS, fixed positioning) often look broken or blank inside an iframe at thumbnail scale. If the thumbnail doesn't render well:
- Create a static `vNN/thumb.svg` representative of the page's visual identity
- Replace the iframe with `<img src="vNN/thumb.svg" style="position:absolute;top:0;left:0;width:100%;height:100%;object-fit:cover;">` in the card
This check must happen before committing the gallery update.

### Current progress — 18 of 25 built, all committed
Need **v19–v25** (7 more). The exploration arc says v17–v22 should converge (mix what works), v23–v25 refinements only with v25 feeling definitive.

| Version | Title / Direction | Notes |
|---------|------------------|-------|
| v01 | Brutalist flip-book | CSS 3D page-turn, 6 panels, type-heavy |
| v02 | Children's picture book | Illustrated, large type, bright |
| v03 | Newspaper front page | Breaking news framing |
| v04 | Horror film poster | Dark, cinematic, scroll-reveal |
| v05 | Social media feed | Posts from @pig1_straw, @pig2_sticks, @bigbadwolf |
| v06 | Court transcript | Wolf on trial, 7 pages, deviated septum defense |
| v07 | Nature documentary | Attenborough-style narration |
| v08 | Comic strip | Panel-based |
| v09 | Recipe card | Each shelter as a recipe with ingredients + instructions |
| v10 | PowerPoint presentation | Slide deck with PPT chrome, dot indicators |
| v11 | Video game UI | RPG/game interface |
| v12 | Illustrated side-scroll | Road with houses, scroll to progress |
| v13 | macOS desktop | Dock with icons, hover shows story captions |
| v14 | VC pitch deck | Full-bleed slides, TAM/SAM/SOM, wolf ticker |
| v15 | Classified dossier | CIA-style, redactions, typewriter reveal |
| v16 | PigInspire (siteinspire clone) | Design gallery, tag filter, lightbox |
| v17 | PigZillow | Sequential 8-scene real estate narrative, sticky map with pin state transitions |
| v18 | PigEgg.com (Newegg) | Flash-sale homepage, wolf countdown, product reviews |

### Brainstormed directions not yet built (pick from these for v19–v25)
- **IKEA instructions** — flat-pack assembly manual for each shelter (isometric diagrams, warning triangles, Swedish product names)
- **Wine/restaurant menu** — tasting notes for each shelter ("earthy straw, medium blow-throughability, short finish")
- **Encyclopedia / Wikipedia article** — dry academic entry with footnotes, infoboxes, edit-war notes
- **Tarot deck** — each card a character or event, illustrated, with divination framing
- **Infomercial** — "But wait, there's MORE!" selling the pig homes, 1-800 number, testimonials
- **D&D Monster Manual** — stat block for the wolf, HP rolls for each shelter, combat log
- **Eurovision scoreboard** — countries awarding points to each pig's shelter design
- **Wanted poster / Wild West** — bounty on the wolf, sheriff's notices for each fallen house
- **NASA mission brief** — pigs as astronauts, shelters as capsule grades, wolf as asteroid
