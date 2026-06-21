# Ahnoud Export — Marketing Site

Single-page marketing site for **Ahnoud Export**, a Dubai-based import/export company
sourcing and distributing goods across the GCC, India, China and Europe.

Built as a **Design Component (DC)** — a self-contained `.dc.html` file that renders
live in the browser and is fully tweakable (theme, accent, fonts, corner radius).

---

## Contents

| File | Purpose |
|------|---------|
| `Ahnoud Export.dc.html` | Main landing page (hero, divisions, why-us, quality, logistics, markets map, contact + footer). |
| `404.dc.html` | Branded "page not found" screen. |
| `support.js` | DC runtime (renders the components). **Do not edit.** |
| `assets/worldmap.svg` | Real world-map used by the markets/corridor section. |
| `assets/logo.svg` | Source brand mark (also inlined in the pages). |

---

## Running locally

These are static files — no build step, no dependencies. Serve the folder with any
static web server so relative asset paths resolve:

```bash
# Python
python3 -m http.server 8000

# or Node
npx serve .
```

Then open <http://localhost:8000/Ahnoud%20Export.dc.html>.

> Opening the file directly via `file://` also works, but a local server is
> recommended so `assets/` and fonts load consistently.

### Deploying

Upload the whole folder to any static host (Netlify, Vercel, S3, GitHub Pages, nginx).
Point your 404 handler at `404.dc.html`.

---

## Customisation (Tweaks)

The main page exposes design tokens as editable props. The most useful ones:

| Prop | Type | Default | Notes |
|------|------|---------|-------|
| `accent` | color | `#a851d6` | Brand accent used across CTAs, links, map, hover fills. |
| `fontPairing` | enum | `Manrope · Modern` | Display/body font pairing. |
| `cornerRadius` | int (0–28) | `8` | Global corner radius for cards, buttons and panels. |
| `device` | enum | `Desktop` | Preview at `Desktop` / `Tablet` / `Mobile` widths. |

Theme (light/dark) is toggled in the nav and persists via `localStorage`.

To change brand copy, contact details or imagery, edit the markup directly in
`Ahnoud Export.dc.html` — every section is plain inline-styled HTML.

---

## Tech notes

- **No framework install** — the DC runtime (`support.js`) is vendored.
- **Styling is inline** by design (paints immediately, no FOUC). The only global CSS
  lives in the `<helmet><style>` block at the top of each page (`@font-face`,
  `@keyframes`, resets, responsive `@container` rules).
- **Responsive** via CSS container queries at `900px` (tablet) and `560px` (mobile).
- **Fonts** load from Google Fonts (Manrope, Plus Jakarta Sans).
- **Cursor effect** — a global trailing dot follows the pointer (desktop only).

---

## Browser support

Modern evergreen browsers (Chrome, Edge, Safari, Firefox). Uses CSS
`container queries`, `color-mix()` and `aspect-ratio`.
