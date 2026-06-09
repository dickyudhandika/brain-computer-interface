# ElevenLabs Typography System — Applied to Artists & Musicians Page

## Status
DRAFT

## Goal
Replace the current bold-weight typography system with ElevenLabs' restrained, light-weight display approach. The ElevenLabs system uses Waldenburg 300 for headlines (authority through restraint, not mass) and Inter for all functional text — a deliberate anti-convention for tech brands that creates a calmer, more authoritative reading experience.

## Source
ElevenLabs Style Reference (Refero) — "Parchment command terminal." Light warm-canvas design system with split typographic personality: Waldenburg weight 300 for display, Inter for UI.

## Key Typographic Principles

1. **Display font = light weight.** Waldenburg 300 at negative tracking for all headlines 32px+. Never bold. Never Inter.
2. **UI font = Inter exclusively.** All body, cards, labels, nav, buttons use Inter 400 or 500. Never Waldenburg.
3. **No Inter above 20px.** Display sizes use Waldenburg, not Inter at large scale.
4. **Tracking is intentional.** Display gets tight negative tracking (-0.02em). Body gets subtle positive tracking (0.01em). These are not defaults — they're design decisions.
5. **Line heights are tight on display** (1.08–1.17), comfortable on body (1.4–1.5).

## Current vs Proposed Mapping

### Type Scale Map

| Element | Current | Proposed | Font | Weight | Size | Line-height | Tracking |
|---------|---------|----------|------|--------|------|-------------|----------|
| Hero h1 | `clamp(36px, 6vw, 72px)` / 800 / -1.5px | `clamp(36px, 6vw, 48px)` / 300 | Waldenburg | 300 | 48px max | 1.08 | -0.96px |
| Section h2 | `clamp(28px, 3.5vw, 44px)` / 700 / -0.8px | `clamp(24px, 3.5vw, 32px)` / 300 | Waldenburg | 300 | 32px max | 1.17 | -0.64px |
| Featured h2 | `clamp(32px, 3.5vw, 48px)` / 700 / -1px | same as section h2 | Waldenburg | 300 | 32px | 1.17 | -0.64px |
| Hero body | 18px / gray-300 | 16px | Inter | 400 | 16px | 1.5 | 0.16px |
| Card title | 18px / 650 / -0.3px | 18px | Inter | 500 | 18px | 1.44 | 0.18px |
| Card body | 14px / gray-500 | 14px | Inter | 400 | 14px | 1.5 | 0.14px |
| Hero badge | 12px / 600 / 0.5px | 13px | Inter | 500 | 13px | 1.4 | 0.13px |
| Section label | 13px / 600 / 0.5px | 13px | Inter | 500 | 13px | 1.4 | 0.13px |
| Hero stat number | 40px / 800 / -1px | 36px | Waldenburg | 300 | 36px | 1.13 | -0.72px |
| Hero stat label | 14px / gray-500 | 14px | Inter | 400 | 14px | 1.5 | 0.14px |
| About pull number | `clamp(48px, 6vw, 88px)` / 800 / -2px | `clamp(40px, 6vw, 48px)` / 300 | Waldenburg | 300 | 48px max | 1.08 | -0.96px |
| About body | 18px / gray-700 | 16px | Inter | 400 | 16px | 1.5 | 0.16px |
| Project year badge | 13px / 600 / 0.5px | 12px | Inter | 500 | 12px | 1.4 | 0.12px |
| Gallery caption | 15px / 500 / -0.2px | 14px | Inter | 500 | 14px | 1.5 | 0.14px |
| Related card title | 18px / 650 / -0.3px | 18px | Inter | 500 | 18px | 1.44 | 0.18px |
| Related card body | 14px / gray-500 | 14px | Inter | 400 | 14px | 1.5 | 0.14px |
| Related arrow | 13px / 600 / 0.3px | 13px | Inter | 500 | 13px | 1.4 | 0.13px |

### Font Substitutes
Waldenburg is not available as a free web font. Substitutes (from ElevenLabs reference):
- **DM Sans 300** or **Figtree 300** — both free on Google Fonts, both have a clean geometric feel at light weight
- **Recommendation: Figtree 300** — closer to Waldenburg's character, has the right amount of geometric precision without feeling cold

### Weight Map
| Context | Weight | Rationale |
|---------|--------|-----------|
| All headlines (h1, h2, stat numbers, pull numbers) | **300** | "Authority through restraint" — the anti-convention |
| Card titles, badges, nav, buttons | **500** | Slightly heavier for interactive/emphasis elements |
| Body text, descriptions, captions, labels | **400** | Standard reading weight |

### Section-by-Section Impact

#### Section 1 — Hero
- h1 drops from 800 weight → 300. This is the biggest perceptual change. The headline becomes quieter, more confident, less shouting.
- Stat numbers drop from 800 → 300, becoming elegant counters rather than aggressive stats.
- Body text tightens to 16px with explicit tracking.

#### Section 2 — Featured Project
- h2 drops from 700 → 300. The featured title feels editorial, not promotional.
- Year badge stays blue accent but drops from 600 → 500 weight.

#### Section 3 — About the Project
- Pull number drops from 800 → 300. The large number becomes a graceful anchor, not a blunt instrument.
- Body text standardizes to 16px Inter.

#### Section 5 — Project Grid
- Card titles move from 650 → 500 weight, 18px → subheading size.
- Year badges become 500 weight with defined tracking.

#### Section 6 — Related (2×2 bordered cards)
- Card titles: Inter 500 at 18px
- Arrow labels: Inter 500 at 13px

## Color Palette (unchanged)
ElevenLabs is a light-theme system. The existing page uses dark/light alternation. Keep the existing color palette:
- `#000` (black), `#fff` (white), `#f6f6f6` (off-white), `#0066ff` (accent)

The typography system is independent of the color system — it works on both dark and light backgrounds.

## Implementation Steps

### Step 1: Add Figtree via Google Fonts CDN
- File: `artists-musicians-optA.html`
- What: Add `<link>` for Figtree (weights 300, 400, 500) + Inter (weights 400, 500) in `<head>`
- Validation: Font loads, no FOUT issues

### Step 2: Replace CSS token variables
- File: `artists-musicians-optA.html`
- What: Add typography CSS custom properties in `:root`:
  ```css
  --font-display: 'Figtree', sans-serif;
  --font-ui: 'Inter', sans-serif;
  --text-display: 48px; --leading-display: 1.08; --tracking-display: -0.02em;
  --text-heading: 32px; --leading-heading: 1.17; --tracking-heading: -0.02em;
  --text-subheading: 18px; --leading-subheading: 1.44; --tracking-subheading: 0.01em;
  --text-body: 16px; --leading-body: 1.5; --tracking-body: 0.01em;
  --text-caption: 13px; --leading-caption: 1.4; --tracking-caption: 0.01em;
  --text-small: 12px; --leading-small: 1.4; --tracking-small: 0.01em;
  ```
- Validation: Variables don't conflict with existing tokens

### Step 3: Update all type selectors
- File: `artists-musicians-optA.html`
- What: Systematically replace every `font-size`, `font-weight`, `letter-spacing`, and `line-height` with token references and correct font-family assignments:
  - All h1, h2: `font-family: var(--font-display); font-weight: 300;` + correct size/tracking
  - All body, p, labels, cards: `font-family: var(--font-ui); font-weight: 400;` + correct size/tracking
  - Card titles, badges: `font-family: var(--font-ui); font-weight: 500;`
  - Remove any `font-weight: 700/800` — nothing should be bold
- Validation: Visual regression check — no element accidentally bold

### Step 4: Responsive check
- What: Figtree 300 at display sizes should remain legible at all breakpoints. Check mobile — the light weight may need slightly larger minimum sizes.
- Validation: 375px viewport, all headlines readable, no orphans

## Risks & Open Questions
- **Light weight on dark backgrounds**: Figtree 300 on black (#000) may appear thinner than on white. May need to bump to 400 on dark sections only, or accept the slightly lighter rendering as intentional.
- **Stat numbers at 300 weight**: Currently aggressive at 800 weight. The 300-weight 40px stat numbers are a radical shift — they become elegant counters. Could feel too understated for a tech use-case page. Flag this for review.
- **Figtree vs DM Sans**: Both are valid Waldenburg substitutes. Figtree chosen for closer geometric character. Can swap if preferred.

## Changelog
- 2026-06-09: Initial draft — ElevenLabs typography system applied to artists-musicians page
