# Artists & Musicians — 6-Section Layout Rework

## Status
DRAFT

## Goal
Make all 6 sections visually distinct. Problem: section 5 (3-col card grid) and section 6 (4-col pill grid) are both multi-column grids — they read as "grid of things" twice in a row. Fix section 6.

## Context
- File: `artists-musicians.html`
- Color palette stays: `#000`, `#fff`, `#f6f6f6` (off-white), `#0066ff` (accent)
- Only 4 related use cases — small data set, opens layout possibilities

## Refero Research

### Styles (visual direction)
| Style | Key traits | Relevant to section 6 |
|-------|-----------|----------------------|
| **Suno** (music AI) | Dark canvas, neon pink/green accents, pill-shaped ghost buttons, compact density | Ghost button treatment for "View use case →" links |
| **Neuralink** (BCI) | Dark-to-light progression (Midnight Void → Soft Linen), 80px pill radius, 20px card radius | Soft Linen `#f5f5f5` light break could be the section 6 background instead of dark |
| **Krea** (AI tool) | Midnight monochrome, subtle bordered cards, 8px radius precision | Clean border treatment, monochrome restraint |

### Screens (layout patterns)
| Screen | Pattern | Takeaway |
|--------|---------|----------|
| **Asana Resources** | "Explore resource hubs" — bordered cards with icon left, title + desc + arrow right, separated by subtle gray borders | Bordered-card grid vs solid-card grid creates visual distinction |
| **Fingerprint Case Studies** | Dark CTA band at page bottom — dramatic contrast to main content, full-width | Dark section band as distinct closer |
| **Instagram Business Success** | 3-col image grid with category filters | Standard grid pattern — what we want to differ from |

### Key insight
Nearly every "related resources" / "case studies" section across the web uses a **multi-column card grid**. The differentiation comes from **card styling** (bordered vs solid, size, presence of imagery), not from abandoning the grid entirely.

## Layout Map — 6 Distinct Sections

| # | Section | Layout | BG | Differentiation from #5 |
|---|---------|--------|----|------------------------|
| 1 | Hero | Centered bold type + stats | Black `#000` | — |
| 2 | Featured | 55/45 split, text + visual | White `#fff` | — |
| 3 | About | Narrow 680px column + pull | Black `#000` | — |
| 4 | Gallery | Full-bleed 4-col mosaic | Black `#000` | — |
| 5 | All Projects | 3-col card grid (solid bg, auto-fill) | Off-white `#f6f6f6` | — |
| 6 | Related | **2×2 large bordered cards** | White `#fff` | Fewer columns (2 vs 3), bordered not solid, larger, has arrows |

## Section 6: Options (3 approaches, pick one)

### Option A: 2×2 Large Bordered Cards ← RECOMMENDED
```
┌──────────────────────┐  ┌──────────────────────┐
│  [icon]              │  │  [icon]              │
│  Documentaries       │  │  Academic Research   │
│  Film, television... │  │  Studies on empathy..│
│              View →  │  │              View →  │
└──────────────────────┘  └──────────────────────┘
┌──────────────────────┐  ┌──────────────────────┐
│  [icon]              │  │  [icon]              │
│  Consumer Research   │  │  Accessibility       │
│  Brand and advert... │  │  BCI-powered wheel.. │
│              View →  │  │              View →  │
└──────────────────────┘  └──────────────────────┘
```
- 2 columns (vs section 5's 3 columns) — instantly different
- Bordered cards (vs section 5's solid cards) — from Asana "Explore hubs" pattern
- Larger cards, more whitespace, arrow CTA
- **Reference**: Asana Resources — "Explore resource hubs" section
- **Style**: Neuralink's 20px card radius + soft bordered treatment

### Option B: Horizontal Scroll Row
```
← scroll →
┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐
│ Doc...   │ │ Academic │ │ Consumer │ │ Access.. │
│          │ │          │ │          │ │          │
│   View → │ │   View → │ │   View → │ │   View → │
└──────────┘ └──────────┘ └──────────┘ └──────────┘
```
- Only horizontally scrolling section on the page — completely different rhythm
- Cards are wider, fewer per "page"
- **Reference**: Common on Apple, Netflix, Spotify
- Risk: hidden content on mobile if not done well

### Option C: Full-Width Stacked Banners
```
┌──────────────────────────────────────────────┐
│  Documentaries & Media            View →     │
├──────────────────────────────────────────────┤
│  Academic Research                View →     │
├──────────────────────────────────────────────┤
│  Consumer Research                View →     │
├──────────────────────────────────────────────┤
│  Accessibility & Mobility         View →     │
└──────────────────────────────────────────────┘
```
- Vertical stack, each item full-width — grid vs stack is clear contrast
- **Reference**: Neuralink's dark-to-light section progression
- Simplest CSS change

## Recommendation: Option A (2×2 Bordered Cards)
- Visually most distinct from section 5's 3-col solid card grid
- Backed by Asana's real-world pattern
- 2 columns creates breathing room, feels premium
- Bordered cards (1px `#eaeaea`) vs solid cards — clear stylistic difference
- Only 4 items, perfect for 2×2

## Implementation Steps

### Step 1: Rewrite section 6 CSS
- File: `artists-musicians.html`
- What: Replace `.related-dark`, `.related-list`, `.related-pill` with:
  - `.related-section` — white background, section header stays
  - `.related-grid-2` — CSS grid, 2 columns, 24px gap
  - `.related-card` — bordered card (1px `#eaeaea`), 20px radius (Neuralink), 32px padding, hover: border darkens + slight lift
  - `.related-card-icon` — small blue icon area top-left
  - `.related-card-arrow` — right-aligned, blue, transitions on hover
- Validation: No style conflicts, section header reuse confirmed

### Step 2: Rewrite section 6 HTML
- File: `artists-musicians.html`
- What: Replace `<section class="related-dark">` with white-bg section, swap 4 `<a class="related-pill">` for `<a class="related-card">` with icon + title + desc + arrow
- Validation: Links preserved, all 4 items render

### Step 3: Responsive check
- What: 2×2 collapses to single column on mobile
- Validation: 375px viewport

## Changelog
- 2026-06-09: v1 — wrongly targeted section 5
- 2026-06-09: v2 — targeted section 6, full-width banners
- 2026-06-09: v3 — added Refero screen/style research, 3 options, recommend Option A (2×2 bordered cards from Asana pattern)
