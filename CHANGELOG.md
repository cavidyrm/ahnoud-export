# Changelog — Ahnoud Export landing page

All notable changes to the design prototype are recorded here.
Format loosely follows [Keep a Changelog]; versioning is [SemVer].

## [1.0.0] — 2026-06-26
First developer-handoff build.

### Added
- Full single-page marketing site: hero, stat strip, trust bar, divisions (with selectable
  detail + image cross-fade), why-us grid, dark quality/certifications band, 6-step logistics
  flow + capability cards, animated markets map, testimonials, CTA, and footer.
- Quote-request modal with client-side validation and a success state.
- Light/dark theme toggle (persisted to `localStorage`).
- Responsive container-query breakpoints at 900px and 560px.
- Custom trailing cursor (dot + speed-reactive ring).
- CTA "cursor-fill" interaction: a radial accent gradient that grows from and tracks the pointer
  across the CTA band.
- Design tweaks: device frame, font pairing, accent color, corner radius.

### Changed
- **Brand accent finalized to purple `#a851d6`** (previously terracotta `#b06a3f`).
  Unified the value across `:root`, the `applyTheme()` runtime fallback, the CTA fill gradient,
  and the `accent` design-prop default so there is a single source of truth.

### Cleaned
- Removed dead `.navlink` CSS rules (the nav uses `.aenav`).
- Added a version/identity banner comment at the top of the component.
