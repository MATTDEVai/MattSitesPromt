# Universal Website Generation Prompt

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

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
INPUT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[PASTE YOUR INPUT HERE — see input options below]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
UNIVERSAL RULES — apply to every website you build
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

BEFORE YOU WRITE A SINGLE LINE OF CODE:
1. Identify the website type from the input (landing page, portfolio,
   SaaS, e-commerce, corporate, event, app promo, docs, etc.)
2. Identify the audience (B2B, B2C, developer, creative, enterprise, etc.)
3. Choose the appropriate visual language for that type and audience
4. Map the input content to a logical page structure for that type
5. Only then begin building

SITE STRUCTURE:
- Choose sections that make sense for THIS site type — do not use a fixed template
- Every section must earn its place; remove anything that adds no value
- Navigation must reflect the actual sections present
- Page flow must follow the natural decision journey of the target visitor

VISUAL DESIGN:
- Apply a coherent design system: consistent type scale, spacing, color usage
- Use CSS custom properties for every design token (colors, radii, shadows, etc.)
- Typography: choose weights, sizes, and hierarchy appropriate to the brand tone
- Color: derive palette from input (logo, screenshots, brand colors) or choose
  one that fits the industry and audience — never use generic blue-gray defaults
  unless they genuinely fit
- Every interactive element must have hover, focus-visible, and active states
- Layout must use modern CSS: Grid and Flexbox, no float hacks
- Whitespace is a design element — use it deliberately

RESPONSIVENESS:
- Mobile-first CSS, breakpoints at 480px, 768px, 1024px as needed
- Navigation collapses to hamburger on mobile
- No horizontal scroll at any viewport width
- Touch targets minimum 44×44px

CONTENT:
- Use all content from the input exactly — names, numbers, features, quotes
- Never invent facts, statistics, or product claims not present in the input
- If content is missing for a section that clearly belongs, write contextually
  appropriate placeholder copy marked with a comment: <!-- PLACEHOLDER: ... -->
- If input is in another language, output the site in English

CODE QUALITY:
- Single self-contained .html file: all CSS in <style>, all JS in <script>
- Semantic HTML5 elements throughout
- No frameworks, no CDN dependencies (exception: Google Fonts link only)
- Vanilla JS only; no jQuery
- All images: <img> with descriptive alt text; use placeholder src if no image provided
- Form submissions: inline validation + success state, no page reload
- Smooth scroll, scroll-padding-top matching sticky header height
- prefers-reduced-motion: disable all animations/transitions if set

ANIMATION & INTERACTION:
- Scroll-triggered entrance animations via IntersectionObserver (fade-up or
  fade-in, threshold 0.1–0.15) — apply only where they add to the experience
- Never animate for the sake of it; keep it purposeful and subtle
- Sticky header with backdrop-filter blur on scroll

QUALITY BAR:
The result must look like it was built by a professional agency.
It must be something the client would actually use, not a demo or wireframe.
No lorem ipsum. No generic stock-photo placeholders with broken layout.
No mismatched font sizes. No amateur spacing. No elements that appear
unfinished or disconnected.
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
LANGUAGE OUTPUT: English  (if source materials are in another language)
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
