# Shervin Tattoo — Style Guide & Version History

**Domain:** shervintattoo.com
**Built by:** c.weird / cweird.com
**Last updated:** April 12, 2026

---

## Version Overview

| Version | Folder | Key Changes |
|---------|--------|-------------|
| v1 | `/v1/` | Persian manuscript scroll design, wooden dowels, diamond borders |
| v2 | `/v2/` | Card flip bug fixes (Y-axis only, Web Animations API for X-axis) |
| v3 | root | New parchment header/footer, logo image, flowers, SEO overhaul, llms.txt |

---

## v1 — Persian Manuscript Scroll (Initial)

**Design concept:** Site as an unfurling dark Persian manuscript scroll. Wooden dowel "rollers" at top (nav) and bottom (footer). Diamond crosshatch ornamental borders on left and right edges. Scroll unfurls on first visit via clip-path animation.

### Typography

| Role | Font | Weight | Fallback |
|------|------|--------|----------|
| Display / Headings | Cormorant Garamond | 300, 400 | Georgia, serif |
| Body | DM Sans | 400, 500, 600 | system sans-serif |
| Mono / Labels | JetBrains Mono | 400, 500 | monospace |

*Note: Cormorant Garamond was chosen as the closest free match to Hoefler Text (proprietary) per client preference.*

### Color Palette

| Token | Hex | Usage |
|-------|-----|-------|
| `--color-paper` | `#161412` | Main background (near-black warm brown) |
| `--color-paper-dark` | `#0e0c0a` | Deeper background, side borders |
| `--color-paper-light` | `#1e1b18` | Form inputs, lighter sections |
| `--color-manuscript` | `#1a1714` | Manuscript body tone |
| `--color-ink` | `#d2cec6` | Primary text |
| `--color-ink-light` | `#a8a295` | Secondary text, body copy |
| `--color-ink-faded` | `#706a5e` | Tertiary text, labels |
| `--color-ink-ghost` | `#4a4438` | Hints, placeholders |
| `--color-accent` | `#4a8fbf` | Electric blue — links, buttons, CTA |
| `--color-accent-hover` | `#5eaadf` | Lighter blue — hover state |
| `--color-gold` | `#8b7340` | Gold — borders, ornamental elements |
| `--color-gold-light` | `#b89a52` | Light gold — nav logo, hover accents |
| `--color-gold-dim` | `#5a4a2a` | Dim gold — section dividers, border lines |
| `--color-green` | `#336633` | Custom cursor base |
| `--color-green-light` | `#69d869` | Cursor effect |
| `--color-border` | `#2e2822` | Section borders, form borders |
| `--color-border-dark` | `#3d362c` | Heavier borders |
| `--color-dowel` | `#3a2f22` | Wooden dowel mid-tone |
| `--color-dowel-light` | `#5c4a34` | Dowel highlight |
| `--color-dowel-dark` | `#1e1610` | Dowel shadow |

### Key Design Elements

**Wooden scroll dowels (nav + footer):** 3D gradient simulating turned wood. Linear gradient from light at top to dark at bottom. End caps as radial gradient ellipses. Drop shadow for depth.

**Diamond side borders:** Fixed position, full height. Repeating 45° and -45° linear gradients creating crosshatch. Gold lines on inner/outer edges. Semi-transparent (opacity: 0.5). 28px wide (12px on mobile).

**Scroll unfurl animation:** CSS `clip-path: inset()` from `0 0 100% 0` to `0 0 0 0`. 2.2s duration with `cubic-bezier(0.22, 0.61, 0.36, 1)`. Opacity from 0.6 to 1.

**Paper texture:** Tileable 512x512 dark aged parchment JPG. Base color rgb(22,20,18). Heavy grain with horizontal fibers and age blotching.

**Custom cursor:** Green evil eye PNG (32x32). CSS cursor property for static. JS overlay for hover effects — enlarges to 44px with electric blue glow on clickable elements. Reverts to text cursor over form inputs.

**Section dividers:** Gold ornamental gradient lines (`divider--ornate`). Fade from transparent → dim gold → gold → dim gold → transparent.

**Hero:** Full-viewport video with dark parchment gradient overlay. Text title "Tattooing by Shervin" in Cormorant Garamond 300 weight, clamp(3rem, 8vw, 6rem).

**Business card:** 3D CSS card with preserve-3d. Front = dragon illustration, Back = contact info. Idle rotation via requestAnimationFrame. Click opens shadowbox lightbox. Cursor sweep flips via Y-axis. Click flips via X-axis (two-phase Web Animation).

---

## v2 — Card Flip Fixes

**Design:** Identical to v1 visually. All CSS unchanged.

### Changes from v1

- **Card X-axis flip:** Replaced setTimeout two-phase approach with Web Animations API for precise keyframe control. Four keyframes: flat → tilt to 90° → swap face at midpoint → flat with new face.
- **Flip debounce:** Added `lbFlipLock` boolean that prevents double-flips during the 450ms animation. Prevents 3D hit-area jitter from firing extra mouseenter/mouseleave events.
- **Card face pointer-events:** Added `pointer-events: none` to `.card-body--lb .card-face` to prevent child elements from interfering with scene-level mouse tracking.
- **Lock-aware mouseleave:** mouseleave handler now checks `lbFlipLock` and discards stale position data during active flips.

---

## v3 — Parchment Header, Logo, SEO Overhaul (Current)

**Design concept:** Simplified navigation. Wooden dowels replaced with warm brown parchment-textured bars. Diamond side borders removed for a cleaner look. Persian calligraphy logo replaces text title. Ornamental flower illustrations in header corners. Comprehensive SEO + AI discoverability.

### Typography

Unchanged from v1/v2:

| Role | Font | Weight |
|------|------|--------|
| Display | Cormorant Garamond | 300, 400, 500, 600, 700 |
| Body | DM Sans | 400, 500, 600 |
| Mono | JetBrains Mono | 400, 500 |

### Color Palette

All CSS custom properties unchanged from v1/v2. Same warm dark brown + gold + electric blue system.

### Key Design Changes from v2

**Header:** Wooden dowel gradient → flat parchment bar. Uses `--color-border` (#2e2822) as base with paper-texture.jpg overlay via `background-blend-mode: overlay`. Subtle gold dim bottom border. Drop shadow for depth.

**Footer:** Same treatment as header — parchment bar with texture overlay. Gold dim top border.

**Dowel end caps:** Removed entirely (no more radial gradient pseudo-elements on nav/footer).

**Diamond side borders:** Removed (`.scroll-body::before` and `::after` cleared).

**Header flowers:** Persian lotus ornament PNGs (`Shervin_flower_left.png`, `Shervin_flower_right.png`) positioned at left and right of nav-inner. 28px height, 50% opacity. `aria-hidden="true"` for accessibility.

**Hero logo:** Text h1 replaced with `TattooingByServin_logo+flowers.png`. Persian calligraphy with integrated flower ornaments. `alt="Tattooing by Shervin"`. Max width: min(80vw, 520px). Drop shadow for legibility over video.

**Nav text:** "Shervin" → "Tattooing by Shervin". Font size reduced from 1.4rem to 1.15rem.

**SEO additions:**
- Title: "Tattooing by Shervin — Tattoo Artist in San Francisco, CA"
- Meta description targeting: tattoo, San Francisco, Persian, color, Japanese, traditional, illustrative
- Open Graph tags (title, description, type, URL, image, locale)
- Twitter Card (summary_large_image)
- Geo meta tags (US-CA, San Francisco)
- Canonical URL: https://shervintattoo.com/
- JSON-LD structured data (TattooParlor schema with alternate names, location, services)
- Enhanced alt text on all images (keyword-rich, descriptive)
- `rel="noopener"` on external links
- `aria-label` on nav element

**AI discoverability:** `llms.txt` file describing the business for ChatGPT, Perplexity, Claude, and other LLMs.

### Files Added in v3

| File | Purpose |
|------|---------|
| `TattooingByServin_logo+flowers.png` | Hero logo — Persian calligraphy with flower ornaments |
| `Shervin_flower_left.png` | Left header flower ornament |
| `Shervin_flower_right.png` | Right header flower ornament |
| `llms.txt` | AI/LLM discoverability file |
| `STYLE-GUIDE.md` | This document |

---

## Asset Inventory

| File | Type | Size | Purpose |
|------|------|------|---------|
| `index.html` | HTML | ~53KB | Single-page site (HTML + CSS + JS) |
| `hero-video.mp4` | Video | ~11MB | Hero background, H.264, 1280px, no audio |
| `paper-texture.jpg` | Image | ~91KB | Tileable 512x512 dark parchment texture |
| `cursor.png` | Image | ~1KB | 32x32 green evil eye cursor |
| `TattooingByServin_logo+flowers.png` | Image | ~1MB | Persian calligraphy logo |
| `Shervin_flower_left.png` | Image | ~448KB | Left flower ornament |
| `Shervin_flower_right.png` | Image | ~449KB | Right flower ornament |
| `Shervin_Polaroid_bycweird.jpeg` | Image | ~398KB | Portrait photo |
| `Shervin_businesscard_1.jpg` | Image | ~270KB | Card info side |
| `Shervin_businesscard_2.jpg` | Image | ~297KB | Card dragon side |
| `Shervin_tattooing_1_byextraekster.jpg` | Image | ~300KB | Portfolio photo 1 |
| `Shervin_tattooing_2_byextraekster.jpg` | Image | ~404KB | Portfolio photo 2 |
| `Shervin_tattooing_3_byextraekster.jpg` | Image | ~234KB | Portfolio photo 3 |
| `llms.txt` | Text | ~1KB | LLM discoverability |

---

## Domains

| Domain | Role |
|--------|------|
| shervintattoo.com | Primary |
| persiantattoo.com | Redirect → shervintattoo.com |
| californiatattooing.com | Redirect → shervintattoo.com |
