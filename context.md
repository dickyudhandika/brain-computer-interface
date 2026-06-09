# Project Context — Identify Use Case Page

## Stack
- **Framework**: Static HTML (no build step)
- **Fonts**: Figtree 300/400/500 (display), Inter 400/500 (UI) — Google Fonts CDN
- **Design System**: ElevenLabs typography system (Waldenburg → Figtree substitute)

## Design Tokens
```css
--font-display: 'Figtree', sans-serif;  /* weight 300 — all headlines */
--font-ui: 'Inter', ...;               /* weights 400/500 — all functional text */
--text-display: 48px / 1.08 / -0.02em
--text-heading: 32px / 1.17 / -0.02em
--text-subheading: 18px / 1.44 / 0.01em
--text-body: 16px / 1.5 / 0.01em
--text-caption: 13px / 1.4 / 0.01em
```
Color: `#000`, `#fff`, `#f6f6f6`, `#0066ff` (accent)

## Files
- `artists-musicians-optA.html` — primary template (Artists & Musicians use case)
- `placeholder.png` — 814×964 placeholder for gallery images
- Various `.docx` source documents for other use cases

## Conventions
- No bold weights anywhere — display uses light 300, UI uses 400/500
- Gallery captions: optional per tile, just include/omit the `.gallery-tile-caption` div
- Gallery images: `object-fit: cover`, center-default
- Section alternation: `.section-dark` (black bg), `.section-light` (off-white), `.section-white`

## Recent Changes
- 2026-06-09: Applied ElevenLabs typography system — Figtree 300 for headlines, Inter for UI, zero bold weights
- 2026-06-09: Gallery tiles switched from CSS gradients to `<img>` tags with `placeholder.png`
- 2026-06-09: Gallery captions made optional — 4 of 7 tiles have captions
- 2026-06-09: Added Dana Leong quote to TEKTONIK gallery tile
