# Universal Website Generation Prompt — v2

A master prompt for building any professional website from any input.
Copy the core prompt, add your input block, and send.

---

## THE PROMPT

```
You are a senior front-end engineer and visual designer with expertise across
all website categories — landing pages, SaaS products, portfolios, e-commerce,
corporate sites, dashboards, documentation, and more.

Your job: take whatever input I provide and produce a complete, production-ready,
single-file HTML website of the highest professional quality.

If the input is ambiguous or incomplete, do NOT ask clarifying questions —
make sensible professional assumptions and build the best site you can in one pass.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
INPUT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[PASTE YOUR INPUT HERE — see input options below]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STEP 1 — PLAN  (output this briefly BEFORE any code)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

State in 4–6 short lines, then start building:
- Website type (landing, portfolio, SaaS, e-commerce, corporate, event, docs…)
- Target audience (B2B, B2C, developer, creative, enterprise…)
- Visual direction (style + one line on why it fits this brand/industry)
- Section list, in order
- Output language

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STEP 2 — BUILD  (universal rules, apply to every site)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

SITE STRUCTURE:
- Choose sections that fit THIS site type — do not use a fixed template.
- Every section must earn its place; remove anything that adds no value.
- Navigation must reflect the actual sections present.
- Page flow must follow the natural decision journey of the target visitor.

DOCUMENT HEAD (mandatory — responsiveness silently breaks without this):
- <html lang="…"> matching the output language.
- <meta charset="utf-8">
- <meta name="viewport" content="width=device-width, initial-scale=1">
- A descriptive <title> and <meta name="description">.

VISUAL DESIGN:
- Coherent design system: consistent type scale, spacing, color usage.
- CSS custom properties for every design token (colors, radii, shadows, spacing).
- Typography: weights, sizes, and hierarchy appropriate to the brand tone.
  Load web fonts with font-display: swap.
- Color: derive the palette from the input (logo, screenshots, brand colors) or
  choose one that fits the industry and audience — never use generic blue-gray
  defaults unless they genuinely fit.
- Every interactive element must have hover, focus-visible, and active states.
- Modern CSS only: Grid and Flexbox, no float hacks.
- Whitespace is a design element — use it deliberately.

RESPONSIVENESS:
- Mobile-first CSS; breakpoints at 480px, 768px, 1024px as needed.
- Navigation collapses to an accessible hamburger on mobile.
- No horizontal scroll at any viewport width.
- Touch targets minimum 44×44px.

ACCESSIBILITY:
- Semantic HTML5 landmarks: header, nav, main, section, footer.
- Text/background contrast meets WCAG AA.
- All images have descriptive alt text; decorative images use alt="".
- Fully keyboard-navigable with visible focus; use ARIA only where needed.

CONTENT & LANGUAGE:
- Use all content from the input exactly — names, numbers, features, quotes.
- Never invent facts, statistics, or product claims not present in the input.
- If content is missing for a section that clearly belongs, write contextually
  appropriate placeholder copy marked: <!-- PLACEHOLDER: … --> . No lorem ipsum.
- Output the site in the SAME LANGUAGE as the input content, unless I specify
  a different language.

IMAGES:
- If a real image is provided, use it via <img> with descriptive alt text and
  loading="lazy".
- If NO image is provided, use a styled placeholder — a CSS gradient block or
  inline SVG in the brand palette, with a short label. NEVER leave a broken
  <img src>.

CODE QUALITY:
- Single self-contained .html file: all CSS in <style>, all JS in <script>.
- Semantic HTML5 throughout.
- No frameworks, no jQuery, no CDN dependencies (exception: Google Fonts link).
- Vanilla JS only.
- Forms: inline validation + success state, no page reload (do not let a <form>
  navigate away).
- Smooth scroll; scroll-padding-top matching the sticky header height.

ANIMATION & INTERACTION:
- Subtle scroll-entrance animations via IntersectionObserver (fade-up or fade-in,
  threshold 0.1–0.15) — only where they add to the experience. Never animate for
  the sake of it.
- Sticky header with backdrop-filter blur on scroll.
- prefers-reduced-motion: disable all animations/transitions if set.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STEP 3 — SELF-REVIEW  (check and fix before finishing)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

□ Viewport meta present; no horizontal scroll at 360 / 768 / 1280px
□ Every nav link points to a section id that actually exists
□ Every interactive element has hover + focus-visible + active states
□ No broken images — all placeholders are styled, not empty
□ Contrast passes WCAG AA; full keyboard navigation works
□ prefers-reduced-motion is respected
□ No lorem ipsum; no invented facts or numbers

QUALITY BAR:
The result must look like it was built by a professional agency — something the
client would actually ship, not a demo or wireframe. No mismatched font sizes,
no amateur spacing, no unfinished or disconnected elements.
```

---

## INPUT OPTIONS

Provide input in any of these forms — or mix them freely.

---

### TEXT INPUT

Paste any combination of the following. Only include what you have.
The model figures out the rest from context.

```
TYPE: [landing page / portfolio / SaaS product / e-commerce / corporate /
       event / app promo / documentation / other]      ← optional, inferred if absent

COMPANY / NAME: ...
PRODUCT / SERVICE: ...
INDUSTRY: ...
TAGLINE: ...                    ← optional
AUDIENCE: ...                   ← optional
PROBLEMS: ...                   ← optional
BENEFITS: ...                   ← optional
FEATURES: ...                   ← optional
PROCESS / STEPS: ...            ← optional
STATS / NUMBERS: ...            ← optional
PRICING / TIERS: ...            ← optional
TESTIMONIALS: ...               ← optional
TEAM: ...                       ← optional
CONTACTS: ...                   ← optional
COLOR PALETTE: ...              ← optional, hex values or description
STYLE DIRECTION: ...            ← optional, e.g. "minimal", "bold", "editorial",
                                   "dark", "technical", "luxe", "playful"
LANGUAGE OUTPUT: ...            ← optional; defaults to the input content's language
EXTRA INSTRUCTIONS: ...         ← anything specific you want
```

**Minimum required:** just enough to identify what the site is about.

Shortest valid input:
```
COMPANY: Dune Studio
PRODUCT: Architecture and interior design firm, Moscow
```

---

### FILE INPUT

Attach files alongside the prompt. The model reads them and extracts everything.

| What you attach | What gets used |
|---|---|
| Screenshots of an existing site | Layout reference, color palette, content structure |
| Presentation / slide deck (PDF or PPTX) | Headlines, sections, value props, feature lists |
| Brand PDF / brochure | Copy, specs, claims, contact info |
| Product or facility photos | Placed into relevant sections as real images |
| Logo file | Placed in header and footer |
| Dashboard or UI screenshot | Used in product/analytics section |
| Competitor site URL | Style and structure reference (do not copy content) |

When files are attached, add a short note:
```
[files: pitch_deck.pdf, office_photo.jpg, logo.png]
Use the deck as the main content source.
Use the office photo in the about or facility section.
Match the brand colors from the logo.
```

---

### OVERRIDE / EXTEND

Add these to any input to force specific behavior:

```
FORCE SECTIONS: hero, features, pricing, faq, contact
SKIP SECTIONS: testimonials, team
ADD SECTION: interactive ROI calculator after pricing
LANGUAGE OUTPUT: English  (overrides the default of matching the input language)
STYLE OVERRIDE: dark theme, monochrome, brutalist grid
IMAGE TREATMENT: all image slots use CSS gradient placeholders in brand colors
```

---

## QUICK-START EXAMPLES

### 1 — Minimal text, B2B service
```
COMPANY: Arcline
PRODUCT: Industrial automation consulting for mid-size manufacturers
STATS: 140+ projects, 23% avg efficiency gain, 8 countries
COLOR PALETTE: #1a1f2e, #e8502a
```

### 2 — Files only
```
[files: company_deck.pdf, product_screenshots.png, team_photo.jpg]
Build a corporate site. Use all content from the deck.
Place the team photo in the about section.
Use the product screenshots in the features section.
```

### 3 — Portfolio / creative
```
TYPE: portfolio
NAME: Marta Voss — Brand Identity Designer
STYLE DIRECTION: editorial, black and white, high-contrast, full-bleed typography
PROJECTS: 6 (extract names and descriptions from attached PDF)
[files: portfolio_overview.pdf]
```

### 4 — SaaS product
```
TYPE: SaaS landing page
PRODUCT: Relo — async video feedback tool for remote design teams
TAGLINE: Replace endless review calls with precise video comments.
FEATURES: Record screen + webcam, timestamp comments, version compare,
          Figma and Notion integrations, public share links
PRICING: Free (3 projects), Pro $12/mo (unlimited), Team $29/mo (SSO + admin)
STYLE DIRECTION: clean, modern, slightly playful — think Linear meets Loom
STATS: 14,000 teams, 4.9 rating, 2 min avg review time saved per comment
```

### 5 — Files + overrides
```
[files: brand_guidelines.pdf, hero_image.jpg]
TYPE: event landing page
EXTRA INSTRUCTIONS:
- Countdown timer to event date: March 14, 2026
- Speaker section with 4 placeholder cards
- Single CTA throughout: "Register Now"
- Dark theme
FORCE SECTIONS: hero, speakers, agenda, venue, faq, register
```

---

## SITE TYPE REFERENCE

Use this to set expectations or guide the TYPE field.

| Type | Typical sections | Primary goal |
|---|---|---|
| **B2B landing page** | Hero, Problem/Solution, Features, How it works, Social proof, Pricing, CTA | Lead capture |
| **SaaS product** | Hero, Features, Demo/Screenshots, Integrations, Pricing, FAQ, CTA | Trial / signup |
| **Portfolio** | Intro, Work grid, Case studies, About, Contact | Show craft |
| **Corporate / company** | Hero, About, Services, Team, Cases, Partners, Contact | Credibility |
| **E-commerce (single product)** | Hero, Benefits, How it works, Reviews, Buy CTA | Purchase |
| **Event** | Hero + countdown, Speakers, Agenda, Venue, FAQ, Register | Registration |
| **App promo** | Hero, Features, Screenshots, Stores, Reviews | Install |
| **Personal / résumé** | Intro, Skills, Experience, Projects, Contact | Hire me |
| **Documentation** | Sidebar nav, Content, Code blocks, Search | Inform |

---

## CHANGELOG (v1 → v2)

- **Output language** now defaults to the input content's language (was: always English).
- Added mandatory **document `<head>`** block: `lang`, charset, viewport, title, meta description.
- **Image placeholders** are now styled (CSS gradient / inline SVG) by default — no broken `<img src>`; real images get `loading="lazy"`.
- Added explicit **"don't ask questions, build in one pass"** instruction.
- Reorganized into **Step 1 Plan → Step 2 Build → Step 3 Self-review**, with a concrete self-review checklist.
- Added an **Accessibility** section (WCAG AA contrast, semantic landmarks, keyboard nav).
- Added `font-display: swap` and a note on the no-CDN / Google-Fonts tension.
