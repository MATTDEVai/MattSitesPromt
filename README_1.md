# Universal Website Generation Prompt

A single, reusable prompt that turns any input — a few lines of text, a pitch deck, screenshots, or a logo — into a complete, production-ready, single-file HTML website.

No framework, no boilerplate, no per-project prompt engineering. You describe (or attach) what the site is about, the model decides the type, structure, and visual language, and returns one self-contained `.html` file an agency would ship.

---

## Why

Most "make me a website" prompts produce generic, template-shaped output: the same blue-gray hero, the same five sections, broken image slots, no mobile handling. This prompt fixes that by forcing the model to **plan before it builds** (site type, audience, visual direction, section list), apply a strict quality bar, and **self-review** before finishing.

It works for landing pages, SaaS products, portfolios, e-commerce, corporate sites, events, app promos, and documentation — the structure adapts to the input instead of being fixed.

---

## What you get

- **One self-contained file** — all CSS and JS inline, no CDN dependencies (except an optional Google Fonts link).
- **Type-aware structure** — sections are chosen for the specific site, not from a template.
- **Real design system** — CSS custom properties for every token, coherent type scale and spacing, palette derived from your input.
- **Responsive by default** — mobile-first, hamburger nav, no horizontal scroll, 44×44px touch targets.
- **Accessible** — semantic landmarks, WCAG AA contrast, keyboard navigation, `prefers-reduced-motion` support.
- **Honest content** — uses your exact copy and numbers, never invents facts; missing content becomes clearly marked placeholders.
- **Language matches your input** — Russian input → Russian site, unless you ask otherwise.

---

## Quick start

1. Open [`universal-website-prompt.md`](./universal-website-prompt.md) and copy the block under **THE PROMPT**.
2. Paste your input into the `INPUT` section (see options below).
3. Send it to your model of choice (Claude, GPT, Gemini, etc.).
4. Save the returned HTML as `index.html` and open it in a browser.

**Shortest valid input:**

```
COMPANY: Dune Studio
PRODUCT: Architecture and interior design firm, Moscow
```

---

## Input options

You can mix and match freely. Provide only what you have.

### Text

```
TYPE: landing page / portfolio / SaaS / e-commerce / corporate / event / app promo / docs
COMPANY / NAME, PRODUCT / SERVICE, INDUSTRY, TAGLINE, AUDIENCE,
PROBLEMS, BENEFITS, FEATURES, PROCESS, STATS, PRICING, TESTIMONIALS,
TEAM, CONTACTS, COLOR PALETTE, STYLE DIRECTION, LANGUAGE OUTPUT, EXTRA INSTRUCTIONS
```

All fields are optional except enough to identify what the site is about.

### Files

| Attach | Used as |
|---|---|
| Site screenshots | Layout / palette / structure reference |
| Pitch deck (PDF / PPTX) | Headlines, sections, value props, features |
| Brand PDF / brochure | Copy, specs, contact info |
| Product / facility photos | Real images in relevant sections |
| Logo | Header and footer, palette source |

### Overrides

```
FORCE SECTIONS: hero, features, pricing, faq, contact
SKIP SECTIONS: testimonials, team
ADD SECTION: interactive ROI calculator after pricing
LANGUAGE OUTPUT: English
STYLE OVERRIDE: dark theme, monochrome, brutalist grid
IMAGE TREATMENT: gradient placeholders in brand colors
```

---

## Example

```
TYPE: SaaS landing page
PRODUCT: Relo — async video feedback tool for remote design teams
TAGLINE: Replace endless review calls with precise video comments.
FEATURES: Screen + webcam recording, timestamp comments, version compare,
          Figma and Notion integrations, public share links
PRICING: Free (3 projects), Pro $12/mo, Team $29/mo (SSO + admin)
STYLE DIRECTION: clean, modern, slightly playful — Linear meets Loom
```

More in the [examples section](./universal-website-prompt.md#quick-start-examples) of the prompt file.

---

## How it works

The prompt runs the model through three stages:

1. **Plan** — identify site type, audience, visual direction, and section order before writing any code.
2. **Build** — apply the universal rules (structure, head, design system, responsiveness, accessibility, content, images, code quality, animation).
3. **Self-review** — verify against a checklist (no horizontal scroll, working nav anchors, all interactive states, no broken images, WCAG AA contrast) and fix issues before returning the file.

---

## Repository

```
.
├── universal-website-prompt.md   # the prompt + input options, examples, site-type reference
└── README.md
```

---

## Contributing

Issues and pull requests welcome — especially new site-type recipes, example inputs, and prompt refinements. Open an issue describing the change before a large PR.

---

## License

<!-- PLACEHOLDER: choose a license, e.g. MIT, and add a LICENSE file -->
TBD — add a `LICENSE` file (MIT recommended for a prompt/template repo).

---

<!-- PLACEHOLDER: replace with your handle -->
Made by [@your-handle](https://github.com/your-handle)
