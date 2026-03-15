# Design Best Practices — Personal Site Redesign

Practical reference for Owen's site redesign. Distilled from research across 20+ personal sites.

---

## Typography Pairing

**Recommended approach:** Serif headings + sans-serif body.

| Role | Font | Notes |
|------|------|-------|
| Headings | Cormorant Garamond | Already chosen. Elegant, warm, editorial feel |
| Body | Inter, Lato, or system sans | Clean readability, doesn't compete with headings |
| Code | JetBrains Mono or SF Mono | If showing code snippets |

**Alternative serif to consider:** Roslindale Variable (used by wongmjane.com) — beautiful character, more distinctive than Cormorant.

**Key settings:**
- Body line-height: 1.6-1.75 (generous = warm)
- Content column max-width: 640-720px (intimate reading width)
- Heading line-height: 1.1-1.2 (tight for large text)
- Base font size: 16-18px

---

## Color Palette

**Warm cream backgrounds (not pure white):**
- `#faf9f6` — warm cream (recommended base)
- `#fdfdfb` — barely warm off-white (wongmjane)
- `#fdf9ee` — warmer cream (Tania Rascia light mode)

**Text colors (not pure black):**
- `#141414` — near-black (boz.com)
- `#1c1b19` — warm dark brown
- Use 3-4 opacity tiers for text hierarchy (primary/secondary/tertiary/quaternary)

**Accent:** One warm accent color. Muted terra cotta, olive, or dusty rose — avoid blue/teal.

---

## Marquee / Scrolling Project Banner

### CSS-Only Implementation

```html
<div class="marquee">
  <ul class="marquee__content">
    <li><!-- project card --></li>
    <!-- ... -->
  </ul>
  <ul class="marquee__content" aria-hidden="true">
    <!-- identical copy for seamless loop -->
  </ul>
</div>
```

```css
.marquee {
  --gap: 1.5rem;
  display: flex;
  overflow: hidden;
  user-select: none;
  gap: var(--gap);
  /* Edge fade — signals "more content" elegantly */
  mask-image: linear-gradient(
    to right,
    transparent,
    black 10%,
    black 90%,
    transparent
  );
}

.marquee__content {
  flex-shrink: 0;
  display: flex;
  justify-content: space-around;
  min-width: 100%;
  gap: var(--gap);
  animation: scroll 40s linear infinite;
}

/* Hover to pause */
.marquee:hover .marquee__content {
  animation-play-state: paused;
}

@keyframes scroll {
  to {
    transform: translateX(calc(-100% - var(--gap)));
  }
}

/* Accessibility: respect reduced motion */
@media (prefers-reduced-motion: reduce) {
  .marquee__content {
    animation-play-state: paused;
  }
}
```

### What Makes Marquees Tasteful (Not Tacky)

- **Slow speed:** 35-50s per cycle. Fast = carnival, slow = editorial.
- **Edge fade masks:** Gradient fade at edges signals continuity.
- **Muted styling:** Content speaks, not the animation.
- **Pause on hover:** Gives user control.
- **Consistent card sizing:** Uniform dimensions, not random sizes.
- **GPU acceleration:** Use `translate3d(0,0,0)` for smooth rendering.

---

## Writing / Article Presentation

### Recommended: Editorial List Style

```
[Category tag in small caps]
Article Title as Link
One-line excerpt or subtitle
March 2026
```

- Title + one-line excerpt + date
- No featured images on the list page (avoids content-farm look)
- Full generous typography on article pages

### Date Formatting

| Style | Example | Feel |
|-------|---------|------|
| Editorial | March 14, 2026 | Warm, magazine-like |
| Abbreviated | Mar 2026 | Clean, minimal |
| ISO | 2026-03-14 | Technical, cold |

**Recommendation:** "March 2026" or "March 14, 2026" for editorial warmth.

### Tags / Categories

- 2-4 broad categories max (e.g., "Engineering", "Reflections", "Projects")
- Display as small caps label above or below title
- Avoid tag clouds (dated) and long tag lists (cluttered)
- Can double as filter on /writing page

---

## About Page Patterns

### Homepage Teaser (Compact)

Keep it to 2-3 elements:
1. Round avatar photo (optional)
2. Name as heading (include Chinese name 汪峻加 prominently)
3. One sentence: role + location + current work

Example structure:
```
Owen Wang 汪峻加
ML/CV engineer at Meta, based in [city].
Building things at the intersection of vision and intelligence.
```

Link to full /about for more.

### Dedicated About Page

**Tone model: boz.com/about**
- Open conversationally: "Hi, I'm Owen..." not "Owen Wang is a..."
- Lead with human details, not resume bullets
- Mention personal interests alongside work
- Acknowledge learning, not just achievements
- Direct, unpretentious — anti-LinkedIn
- Link to CV/resume separately, don't embed it

**Structure:**
1. Conversational intro (2-3 sentences)
2. What you work on and care about
3. Personal interests / life outside work
4. Contact / social links

---

## Homepage Structure (Recommended)

Based on best-performing personal sites:

1. **Hero / About teaser** — Name (EN + CN), one-line bio, social icons
2. **Project marquee** — Horizontal scrolling banner of project cards
3. **Recent writing** — 3-5 latest articles in editorial list style
4. **Navigation cards** — 2-card grid linking to Work and Projects sections

### Key Principles

- **Constrained width** for text content (640-720px)
- **Full-bleed** for marquee/visual elements
- **Generous vertical spacing** between sections
- **Minimal navigation** — 3-4 items max (Writing, Projects, About)

---

## Differentiation Ideas

### Cultural Identity
- Display 汪峻加 prominently, not parenthetically (precedent: wongmjane.com shows 黄文津 in hero)
- Consider using Chinese typography as a subtle design element

### "Now" Section
- What you're currently working on / reading / thinking about
- Makes the site feel alive and personal, not a static portfolio
- Update monthly (paco.me does this well)

### Project Presentation (Brian Lovin Style)
- Clean list with: project name, one-line description, role/company
- Hover state reveals more detail or subtle visual change
- No grid of screenshots — let titles do the work

---

## Reference Sites

| Site | What to study |
|------|--------------|
| wongmjane.com | Serif typography, cultural identity display, warm palette |
| boz.com | About page tone, EB Garamond + Lato pairing, anti-LinkedIn voice |
| brianlovin.com | Homepage about teaser, project list layout, text hierarchy |
| paco.me | "Now" section, minimal structure, command menu |
| maggieappleton.com | Cream palette, garden metaphor, essay card grid, warm editorial |
| stephango.com | Topic taxonomy, editorial voice, keyboard shortcuts |
| craigmod.com | Writer-centric design, photography integration, newsletter emphasis |
| frankchimero.com | Understated warmth, illustrated essay thumbnails, archival rigor |
| leerob.com | Narrative-first homepage, inline bio, bulleted writing list |
| rauno.me | OS-inspired design, horizontal project scroll, dock navigation |
| rsms.me | Project list with one-line descriptions, 500+ article archive |
| taniarascia.com | Light mode cream palette (#fdf9ee), tag system, deep dive cards |
