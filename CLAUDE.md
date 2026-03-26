# maninae.github.io

Owen Wang's personal website. Pure static HTML/CSS — no frameworks, no build step.

## Stack
- Vanilla HTML5 + CSS3 + minimal inline JS
- Deployed via GitHub Pages (`.nojekyll` disables Jekyll)
- Google Fonts: Cormorant Garamond (headers), DM Sans (body)

## Pages
- `index.html` — Homepage: hero, about teaser, featured projects, writing preview, explore cards
- `work.html` — Work experience timeline (Meta, Cruise, Stanford) with logos, metrics, skill pills
- `projects.html` — Project showcase cards (CS234 RL, COCO segmentation)
- `about.html` — Bio, profile photo, resume link, social links
- `writing.html` — Writing hub (currently placeholder)

## Styling
- `styles.css` — Shared stylesheet with CSS custom properties for theming
- Light theme: parchment (#F3F0E4) + warm accent (#C47832)
- Dark theme: ocean (#0E1620) + golden accent (#D4923A)
- Theme toggle persists via localStorage
- Responsive breakpoints at 768px and 640px
- Scroll-triggered fade-in animations via Intersection Observer

## Key directories
- `assets/logos/` — Company logos (meta.png, cruise.png, stanford.png)
- `assets/owen-profile.png` — Profile photo
- `callback/tesla-32cfe0/` — Tesla OAuth callback (hidden from crawlers)
- `.well-known/appspecific/` — OAuth app verification
- `writing/` — Writing content directory

## Conventions
- Each page is self-contained (own nav, footer, inline scripts)
- Nav includes active-state dot indicators
- No package.json or build tools — edit HTML/CSS directly and push
- `robots.txt` blocks `/callback/` and `/.well-known/` from crawlers
