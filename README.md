# Handoff: Ahnoud Export — Marketing Landing Page

**Version:** 1.0.0
**Fidelity:** High-fidelity (hifi) — final colors, type, spacing, copy and interactions.

---

## Overview

A single-page marketing site for **Ahnoud Export**, a Dubai-based (Est. 2021) import/export
trading company sourcing across the GCC, India, China and Europe. The page presents the
company's divisions, value props, certifications, logistics flow, served markets, social proof,
and a quote-request flow (modal form). It supports **light/dark themes** and is **responsive**
(desktop → tablet → mobile).

## About the Design Files

The files in this bundle are a **design reference built in HTML** — a working prototype that
demonstrates the intended look, motion and behavior. They are **not** meant to be shipped as-is.

The task is to **recreate this design inside the target codebase's existing environment**
(React, Vue, Svelte, Astro, plain HTML/CSS, etc.) using that project's established patterns,
component library and conventions. If no codebase exists yet, choose the most appropriate
framework for a marketing site and implement it there. Treat the HTML/CSS/JS here as the source
of truth for **visual spec and behavior**, not as code to copy line-for-line.

> The prototype is authored as a "Design Component" (`.dc.html`) that depends on a small runtime
> (`support.js`). You do **not** need to reproduce that runtime — it only exists to make the
> prototype interactive in the design tool. Reimplement the markup, styles and logic natively.

## How to view the prototype

Open `Ahnoud Export.dc.html` in a browser (it loads `support.js` and `assets/` relative to it).
Use the tool's Tweaks panel — or edit the `data-props` defaults — to switch device, font pairing,
accent color and corner radius.

---

## Design Tokens

All tokens are CSS custom properties defined in `:root` (light) and `#ae-root[data-theme="dark"]`.

### Accent (single source of truth)
- **`--accent: #a851d6`** (purple). This is the one brand accent. It is referenced everywhere via
  `var(--accent)` and is also injected at runtime by `applyTheme()`. To retheme, change it in
  **three** places that must stay in sync: the `:root` declaration, the `applyTheme()` fallback,
  and the `accent` entry in `data-props`.
- Accent is used for: eyebrow labels, section numbers, nav "Quote" button, active division card,
  chip dots, map nodes/routes/glow, hover fills (stat cells, capability/region cards), footer link
  hovers, the custom cursor dot+ring, and the CTA cursor-fill gradient.

### Color — Light theme
| Token | Value | Use |
|---|---|---|
| `--page` / `--surf` | `#ffffff` | page + card backgrounds |
| `--surf2` | `#fafafa` | inputs, subtle surfaces |
| `--ink` | `#1a1a1a` | primary text |
| `--ink2 … --ink5` | `#33312d`, `#44413c`, `#55524c`, `#6b675f` | secondary text ramp |
| `--mut` / `--mut2` / `--mut3` | `#7a766e` / `#8a8780` / `#9a968e` | muted labels |
| `--faint` | `#b0aca3` | fine print |
| `--line` / `--line2` / `--hair` / `--stripe` | `#eceae5` / `#efedea` / `#e2dfd9` / `#e9e7e2` | borders, grid gaps, dividers, placeholder stripes |
| `--bd … --bd4` | `#d4d1cb … #ddd9d2` | input borders |
| `--fill` / `--fill2` / `--warm` | `#f7f6f4` / `#f3f1ee` / `#fdf6f4` | chip/section fills, error field bg |
| `--solid` / `--on-solid` | `#1a1a1a` / `#ffffff` | dark buttons + their text |

### Color — Dark theme (`data-theme="dark"`)
| Token | Value |
|---|---|
| `--page` / `--surf` / `--surf2` | `#0e0d0b` / `#1b1a17` / `#161512` |
| `--ink … --ink5` | `#f3efe8`, `#dad5cb`, `#c8c3b9`, `#aca69c`, `#9a948b` |
| `--line` / `--hair` / `--stripe` | `#2a2825` / `#2c2a26` / `#201f1c` |
| `--bd … --bd4` | `rgba(255,255,255,.17 / .15 / .12 / .12)` |
| `--fill` / `--warm` | `#191815` / `#241a17` |
| `--solid` / `--on-solid` | `#f3efe8` / `#1a1a1a` |

Fixed (theme-independent) darks used in hero / quality / footer: `#0d0c0b` (hero & footer bg),
`#1a1a1a` (quality band), `#211f1c` (cert cards), `#34322e` / `#4a463f` (cert borders),
`#b8b4ac` / `#cfcbc2` / `#8e8a82` (cert text), footer text `#f2efe9` / `#c4beb4` / `#d2ccc2` /
`#9a948b`. Nav pill bg `#1d1c19`, nav icon buttons `#2a2824`. Error text/border `#b04030` / `#d8836f`.

### Typography
- **Default pairing:** "Manrope · Modern" — display + body both **Manrope**, mono **JetBrains Mono**.
  (`--font-display`, `--font-body`, `--font-mono` are swapped at runtime by the chosen pairing.)
- **`.mono` class** uses Manrope/Plus Jakarta Sans for label-style text.
- Selectable pairings (font tweak): Helvetica · Swiss · `'Helvetica Neue'` / JetBrains Mono;
  Archivo · Industrial; Space Grotesk · Techy; Bricolage · Editorial; Manrope · Modern (default).
- **Type scale (desktop):** hero H1 `136px / 700 / line 0.9 / -0.045em`; section H2 (`.h-sec`)
  `64px / 700 / -0.035em`; CTA H2 (`.h-cta`) `64px / 700 / -0.04em / line 0.98`; division detail
  H3 `34px / 700 / -0.025em`; card titles `20–22px / 700 / -0.02em`; stat numbers `38px / 700`;
  body `15–17px / line 1.5–1.6`; testimonials `23px / 500`; eyebrow/mono labels `10–12px`,
  uppercase, letter-spacing `0.12–0.16em`.

### Radius, spacing, shadow
- **`--radius: 8px`** (tweakable 0–28), `--radius-sm = radius × 0.5`. Used on cards, buttons,
  inputs, images, panels. Nav pill uses fixed `18px`, nav inner buttons `12px`.
- Section vertical rhythm: `padding-top: 104–108px` per section; container side padding `28px`
  (desktop), `28px` ≤900px, `18px` ≤560px; container `max-width: none` (full-bleed with padding).
- Grid gaps: hairline `1px` (stat strip, why-us grid — gap shows `--line` through), `16–24px`
  (card grids), `12px` (region list).
- Button hover shadow `0 12px 26px rgba(0,0,0,0.17)`; card active shadow
  `0 10px 26px rgba(0,0,0,0.12)`; nav pill `0 18px 48px rgba(0,0,0,0.36), 0 2px 6px rgba(0,0,0,0.22)`;
  modal `0 30px 80px rgba(0,0,0,0.3)`.

---

## Screens / Views

The page is one continuous scroll. Sections in order:

### 0. Custom cursor (global)
A fixed-position custom cursor: an 8px accent **dot** (tight follow, lerp 0.30) plus a 30px accent
**ring** (trails behind, lerp 0.12, stretches with speed). Driven by `requestAnimationFrame` +
`mousemove`. Hidden until first move; fades on `mouseout` of the document. `z-index: 9999`,
`pointer-events: none`. **Layout/cosmetic only — make it desktop-only and respect
`prefers-reduced-motion`; it is not required for accessibility.**

### 1. Floating nav pill (fixed, bottom-center)
- Hidden until the user scrolls past the hero (an IntersectionObserver on a 130px `[data-navtrigger]`
  sliver toggles it). Slides up from `translateY(150%)` → `0`, fades `0→1`, `0.45s`
  `cubic-bezier(.16,1,.3,1)`.
- Contents (left→right): home/logo button (42×42, `#2a2824`), section links (`.aenav`:
  Divisions, Why us, Quality, Logistics, Markets — anchor scroll, hover → accent text +
  faint bg), **Quote** button (accent bg, white text, `13px 22px`, radius 12, hover brightens),
  theme-toggle button (sun/moon icon, persists to `localStorage['ae-theme']`).
- Pill: `#1d1c19` bg, `1px` translucent border, radius `18px`, padding `7px`.

### 2. Hero
- 600px tall rounded panel, full-bleed photo (`object-fit: cover`) with a left-to-right dark
  gradient scrim `linear-gradient(90deg, rgba(8,8,7,.74) → .5 → .28)`.
- **Top-left brand lockup:** 42px accent-less `--solid` logo tile + "AHNOUD EXPORT" (18px/800) +
  "EST. 2021 · DUBAI" mono caption.
- **H1** bottom-left: "Source the / world." (136px).
- **Sub** below H1: max 480px, white 86%.
- **Glass card** bottom-right (324px, `--card` + `backdrop-filter: blur(8px)`): "TRUSTED EXPORTER"
  eyebrow + "ISO 9001 · Halal · CE…" line.
- **CTA buttons** bottom-right: "Request a quote →" (`--solid`) opens the quote modal;
  "View divisions" (translucent) anchors to `#divisions`.
- **Stat strip** below hero: 4 cells (2021 Founded · 3 Sourcing regions · 100+ Product categories ·
  3 Active certifications), hairline-separated, **hover fills each cell with accent**
  (animated `background-size 0%→100%`, `0.5s`).

### 3. Trust bar
Top/bottom hairline-bordered row: "CERTIFIED & COMPLIANT" + ISO 9001 / HALAL / CE MARK +
Certificate of Origin / Phytosanitary / Customs cleared. Mono type.

### 4. Divisions (`#divisions`) — "01 — Divisions / What we trade"
- 3 selectable cards (Industrial Goods & Machinery · Agricultural & Food Products ·
  Mixed / Other Commodities). The **active** card is filled accent (white text, lifted shadow);
  others are `--surf` with `--line` border. Clicking selects it.
- Below: a 2-column **detail split** — left = division detail (eyebrow, H3 name, long description,
  a 2-col grid of item chips, "Request a quote for this division →" button); right = a stacked set
  of three cross-faded images, only the active one at `opacity:1` (`0.45s`), with a mono image label
  badge. Footnote: handles all legal commodities, **no fuels/petroleum**.

### 5. Why (`#why`) — "02 — Why Ahnoud Export"
H2 "Built for buyers who can't afford surprises." + a 4-up hairline grid:
Certified quality · Global logistics reach · Documentation handled · A single point of contact.
Each cell hover tints bg `color-mix(--accent 7%, --surf)` and nudges its number up.

### 6. Quality & certifications (`#quality`) — dark band "03"
Fixed dark `#1a1a1a` rounded band: H2 "Trust, on paper." + 3 cert cards (ISO 9001, Halal Certified
[حلال], CE Marking) each with a circular badge. Hover lifts the card and turns the badge ring +
fill accent. Footer row lists also-handled docs (Certificate of Origin, Phytosanitary, Commercial
invoice & packing list, Bill of lading).

### 7. Logistics (`#logistics`) — "04 — Logistics & capabilities"
H2 "How we ship." + a **6-step flow** (Inquiry → Quote & Incoterm → Sourcing & QC → Documentation →
Freight → Delivery), 3-col grid with left-border separators. Then **4 capability cards** (Methods,
Incoterms, Lead time `2–6` weeks, Capacity `FCL+`) that hover-fill accent.

### 8. Markets (`#markets`) — "05 — Markets we serve"
H2 "Four regions, one corridor." 2-col split: **left** an animated world-map panel
(`assets/worldmap.svg` tinted by CSS filter), an overlaid `viewBox="0 0 950 620"` SVG drawing
trade corridors with animated dashed routes (`@keyframes dashmove`), travelling cargo dots
(`<animateMotion>`), and 4 pulsing nodes (`@keyframes pulsering`) labelled Europe / GCC / India /
China; **right** four region cards (GCC, India, China, Europe) that hover-fill accent.

### 9. Testimonials — "06 — Proof"
2 sample quote cards with striped placeholder avatars + role/industry. Footnote flags them as
sample references to replace with named clients.

### 10. CTA + Footer (`#contact`)
Fixed dark `#0d0c0b` full-bleed footer. **CTA block at top:** H2 "Ready to source with confidence?"
+ sub + white "Request a quote →" button.
- **CTA cursor-fill interaction:** on `mousemove` over the CTA band, a 1500px radial accent gradient
  circle tracks the cursor and is positioned at the pointer; on `mouseenter` it scales `0→1`
  (`0.6s cubic-bezier(.22,.61,.36,1)`), on `mouseleave` back to `0`. Purely decorative; behind the
  text (`z-index:0`, content `z-index:1`), `pointer-events:none`, clipped by `overflow:hidden`.
- **Footer rows:** link column (Divisions/Why us/Quality/Logistics/Markets); center contact block
  (head office address, phone `+971 50 290 9038`, email `hello@ahnoud.com`, WhatsApp/Instagram/email
  social buttons); right certification badge card ("Certified Exporter", ISO 9001 · HALAL · CE);
  bottom bar © 2026 + Privacy Policy.

### 11. Quote modal (overlay)
Opened by any "Request a quote"/"Quote" button (hero, nav, division detail, CTA). Centered card
(max 620px) over a blurred scrim; click-scrim or Esc closes; body scroll locks while open.
- **Form fields:** Full name\*, Company, Email\*, Destination country, Division (select, pre-filled
  from the trigger), "What do you need to source?"\* (textarea). Submit = "Send request →".
- **Validation (client-side):** name required; email required + regex `^[^@\s]+@[^@\s]+\.[^@\s]+$`;
  details required. Invalid fields switch to error styling (border `#d8836f`, bg `--warm`) with a
  mono error message in `#b04030`.
- **Success state:** replaces the form with a check badge + "Request received" + personalized line
  using the submitter's first name. (Prototype does **not** POST anywhere — wire to your backend /
  CRM / email endpoint.)

---

## Interactions & Behavior

- **Scroll-reveal:** elements with `[data-reveal]` start `opacity:0; translateY(26px)` and animate in
  (`0.8s cubic-bezier(.16,1,.3,1)`) when 12% visible (IntersectionObserver, one-shot).
- **Theme toggle:** light ⇄ dark, persisted in `localStorage['ae-theme']`; `data-theme` on the root;
  `0.35s` color/background transition.
- **Hover-fill cards** (stat cells, capability cards, region cards): `background-size 0%→100%`
  accent gradient, `0.5s cubic-bezier(.22,1,.36,1)`, text flips to `--on-solid`.
- **Buttons** (`.ae-btn`): hover `translateY(-2px)` + shadow + slight brightness; active
  `translateY(0) scale(0.98)`; trailing `→` (`.ae-arrow`) slides +5px on hover.
- **Division switcher:** selecting a card updates the active card style, the detail copy/chips, and
  cross-fades the paired image.
- **Custom cursor & CTA fill:** see sections 0 and 10. Both decorative; gate behind a pointer-fine /
  reduced-motion check.
- **Nav reveal:** appears only after scrolling past the hero trigger.

### Responsive behavior (container queries on `#ae-root`)
- **≤900px:** containers tighten to 28px; why-us & cert grids → 2-col; hero de-absolutes into normal
  flow (title 88px); footer reflows to a 2-col grid; capability/region grids stack.
- **≤560px:** most grids → 1-col; hero title 54px, section H2 31px, CTA 32px; nav links become a
  horizontally-scrollable masked strip; nav pill width `100cqw − 32px`; trust bar stacks; footer
  → single column centered.

## State Management

Component state (reimplement with your framework's state primitives):
- `theme`: `'light' | 'dark'` — seeded from `localStorage['ae-theme']`, default `'light'`.
- `navShown`: boolean — driven by the hero-trigger IntersectionObserver.
- `quoteOpen`: boolean — modal visibility.
- `activeDivision`: `0 | 1 | 2` — selected division index.
- `form`: `{ name, company, email, country, division, details }`.
- `errors`: per-field validation messages (cleared on edit).
- `submitted` + `submittedName`: success-state flag + first name for the thank-you copy.

**Data fetching:** none in the prototype. The quote form needs a real submit endpoint.

## Configurable props (design tweaks)

Exposed as `data-props` on the prototype; treat as build-time/theme options:
- `device`: `Desktop | Tablet | Mobile` (preview frame only — your build is naturally responsive).
- `fontPairing`: one of the 5 pairings above (default **Manrope · Modern**).
- `accent`: brand accent color (default **#a851d6**).
- `cornerRadius`: integer px 0–28 (default **8**) → `--radius`.

## Assets

| File | Used by | Notes |
|---|---|---|
| `assets/worldmap.svg` | Markets section map | Recolored at runtime via CSS `filter` (black in light, inverted white in dark). Replace with your own equirectangular world map if preferred. |
| `assets/logo.svg` | (available) | Brand mark. The hero/nav currently inline the same mark as raw `<svg>` paths — prefer using this file. |
| Unsplash photos (hero + 3 division images) | hero, division detail | Loaded by remote URL in the prototype — **replace with licensed/owned imagery** before production. URLs are in the markup and in `divisionData`. |
| Icons (sun/moon, WhatsApp, Instagram, check, arrows) | nav, footer, modal | Inline SVG / unicode. Swap for your icon system. |

## Copy

All visible copy is final-draft and lives in the markup / in the `divisionData` getter (division
names, descriptions, item lists, image labels). The testimonials and the references footnote are
explicitly marked as **samples to replace**. Contact details: Gulf Travel & Tourism, Showroom 1,
Ground Floor, Port Saeed (Between dnata & Deira Clocktower), Deira, Dubai, UAE · +971 50 290 9038 ·
hello@ahnoud.com.

## Files in this bundle

- `Ahnoud Export.dc.html` — the full prototype (markup + styles in `<helmet>` + logic class).
- `404.dc.html` — branded "Route not found" / page-not-found screen (uses the same `#a851d6`
  accent, the Ahnoud mark, and an animated route line). Point your host's 404 handler at it.
- `support.js` — prototype runtime (design-tool only; do **not** port).
- `assets/worldmap.svg`, `assets/logo.svg` — design assets.
- `CHANGELOG.md` — version history.

## Implementation checklist

- [ ] Rebuild sections natively; keep one `--accent` token wired through everything.
- [ ] Wire the quote form to a real endpoint; keep client-side validation rules.
- [ ] Replace Unsplash images + sample testimonials with owned/licensed content.
- [ ] Implement light/dark with the documented token maps; persist preference.
- [ ] Reproduce scroll-reveal, hover-fills, nav reveal, division cross-fade.
- [ ] Gate the custom cursor + CTA cursor-fill behind pointer-fine + `prefers-reduced-motion`.
- [ ] Verify the ≤900px and ≤560px breakpoints.
- [ ] Accessibility pass: focus states, labels, modal focus-trap, color contrast on accent fills.
