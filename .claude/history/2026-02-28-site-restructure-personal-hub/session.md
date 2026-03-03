# Session: Full Site Restructure — Resume to Personal Hub

## Goal
Transform the personal website from a dark-themed digital CV (single-page resume layout) into a modern, multi-page personal hub with equal emphasis on writing, career, and projects. The user wanted a calm, elegant aesthetic — "modern, water, flowy" — with turquoise/ocean/alpine tones instead of the original dark blue/cyan tech palette.

## Approach
1. Explored the codebase thoroughly (static HTML + Tailwind CDN, no build tools)
2. Gathered user preferences through iterative Q&A — mood, color direction, structure, writing prominence
3. Created a detailed plan covering architecture, palette, typography, page designs, and implementation order
4. Built all pages, then iterated on palette and font choices based on user feedback

## Key Decisions

### Architecture
- **Hub model**: Homepage became a landing page with 3 cards (Writing, Work, Projects) instead of a scrollable resume
- **Multi-page**: Split content into `index.html` (hub), `work.html` (resume), `writing.html` (listing), `projects.html` (showcase)
- **Writing section**: Fresh start — all 8 placeholder blog posts deleted, `/blog/` directory removed, replaced with `/writing/` directory
- **No build tools**: Kept the zero-dependency static HTML + Tailwind CDN approach

### Color Palette Evolution
1. **Original site**: Dark blue/cyan (`#0B1121` bg, `#38BDF8` accent) with Syne + Outfit fonts
2. **First redesign**: Warm beige/papyrus (`#F5F0EB` bg, `#8B6F4E` accent) with Cormorant Garamond + Inter — user found this too "serif'd, exquisite papyrus writer"
3. **Final palette**: Cool alpine mist (`#F0F5F4` bg, `#2C9E96` turquoise accent) with aurora purple `#8B5CF6` for selection highlight

### Typography Evolution
1. Cormorant Garamond (serif) — too papyrus/old-fashioned
2. Sora (geometric sans) — too blocky and childish
3. Presented 5 options: Outfit, Plus Jakarta Sans, Manrope, Figtree, Urbanist
4. User compared Manrope vs Figtree, chose **Figtree** for its light, airy quality
5. Hero name "Owen Wang" was too heavy at bold weight — dropped to `font-medium` (500)

### Layout
- Homepage hero + cards in single viewport (no scroll needed to see cards)
- Work page: single column 720px, includes Experience + Skills + Projects + Resume download
- Projects section added to Work page per user request, linking to same external URLs

## Work Performed (Chronological)

1. **Exploration**: Two parallel agents explored the full codebase — file structure, design system, components, blog content, responsive patterns
2. **User Q&A**: Gathered preferences on site vibe (hybrid), writing prominence (equal), blog content (fresh start), design taste (described the "iced americano at dawn" mood)
3. **Plan creation**: Plan agent designed full architecture, color palette, typography, page-by-page layouts, implementation sequence
4. **Plan review**: Read `index.html` (514 lines) and `blog/index.html` (369 lines) to validate plan details
5. **Asset setup**: Created `assets/` directory, copied and renamed `owen profile picture.png` → `assets/owen-profile.png`
6. **Built `index.html`**: Complete rewrite — hero section with name/tagline, 3 hub cards, nav bar, footer. Used frontend-design skill for initial build
7. **Built `work.html`**: Migrated all resume content (5 experience entries, skills, about blurb, resume link)
8. **Built `writing.html`**: Listing page with empty state ("New writing coming soon") and commented-out template for future posts
9. **Built `projects.html`**: 2 project cards (CS234 RL, COCO Segmentation) in full-width card layout
10. **Built `writing/_template.html`**: Article template with full typography system (headings, code blocks, blockquotes, lists)
11. **Deleted `/blog/`**: Removed all 8 placeholder posts and blog index
12. **Layout fix**: Combined hero and hub cards into single viewport (removed `min-h-screen` on hero alone, merged sections)
13. **Palette shift**: Rewrote all 5 files from warm beige to cool alpine/turquoise palette
14. **Font iteration**: Swapped Cormorant Garamond → Sora → Figtree (via Manrope comparison) across all 5 files
15. **Hero weight fix**: Changed hero name from `font-bold` to `font-medium` for lighter Figtree rendering
16. **Projects on Work page**: Added Projects section between Skills and Resume link on `work.html`

## Artifacts Created
- `index.html` — rewritten homepage hub
- `work.html` — new career/resume page
- `writing.html` — new writing listing page
- `projects.html` — new projects page
- `writing/_template.html` — blog post template
- `assets/owen-profile.png` — renamed profile image
- `.claude/plans/shimmering-chasing-kite.md` — implementation plan

## Artifacts Deleted
- `blog/index.html`
- `blog/posts/` (8 HTML files: diffusion-models-production, synthetic-data-challenges, optimizing-gpu-training, pytorch-lightning-migration, int8-quantization-guide, neural-rendering-ar, applied-research-mindset, debugging-distributed-training)

## Final Design System
- **Background**: `#F0F5F4` (pale alpine mist)
- **Surface**: `#E3ECEB` (soft sage)
- **Text**: `#151D20` / `#486168` / `#7C9499` (deep slate → coastal gray)
- **Accent**: `#2C9E96` (turquoise)
- **Selection**: `#8B5CF6` (aurora purple)
- **Border**: `#CEDBD8` (cool sage)
- **Display font**: Figtree (300-700)
- **Body font**: Inter (300-500)

## Lessons / Takeaways
- User has strong aesthetic instincts but needs to see options to compare — iterative font selection (5 options → 2 → 1) worked well
- The "mood description" approach (iced americano at dawn) was more useful than asking for specific hex values
- User pivoted significantly from initial warm/beige direction to cool/turquoise — be ready for aesthetic pivots
- Keeping the zero-build-tool approach (Tailwind CDN) means duplicating ~80 lines of config across pages, but the simplicity is worth it for a 5-page site
- User prefers projects visible on the Work page too, not just isolated on Projects page — content can live in multiple places
