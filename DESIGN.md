# Design

Visual system for the Quantixz one-page landing. Cosmic-premium, dark, identity-driven. Color strategy: **drenched** — the deep oxblood surface IS the brand; one saturated red accent carries energy; warm cream is the ink.

## Color

Committed brand tokens (do not drift — identity preservation wins):

| Token | Value | Role |
|---|---|---|
| `--c-bg` | `#160002` | Body background (near-black oxblood) |
| `--c-black` | `#0a0001` | Deeper sections (benefits, services) |
| `--c-deep` | `#3a0008` | Mid oxblood for aurora/gradients |
| `--c-accent` | `#e50c33` | Primary red — CTAs, accents, links, focus |
| `--c-cream` | `#ffedd9` | Primary ink / text on dark |
| `--c-cream-dim` | `#ffedd9b3` (70%) | Secondary body text |
| `--c-cream-mut` | `#ffedd966` (40%) | Muted labels, meta — **audit contrast** |
| `--c-line` | `#ffedd91a` (10%) | Borders |
| `--c-line-2` | `#ffedd90d` (5%) | Subtle fills |

Notes: body text on `--c-bg` uses `--c-cream` / `--c-cream-dim` (high contrast). `--c-cream-mut` (40%) is borderline for small text — reserve for non-essential labels only, never body. `::selection` = accent bg + cream.

## Typography

- **Display & body:** Axiforma (Kastelov), self-hosted woff2, weights 400/500/600/700/800/900. Fallback Archivo (Google Fonts) → system sans.
- `.display`: weight 900, line-height 1.0, letter-spacing -0.02em, uppercase. Used for h1/h2 section heads.
- Hero h1: `clamp(2.4rem, 7vw, 6rem)`. Contact h2 goes larger (`clamp(2.6rem, 9vw, 7rem)`) — the one intentional shout.
- Body: 16px base, line-height 1.6, weight 400.
- One family in many weights (no font pairing) — contrast comes from weight + case + size.

## Motion

- Easing: `--ease: cubic-bezier(.2,.7,.2,1)` (ease-out). No bounce/elastic.
- Reveal-on-scroll: opacity + translateY + blur(6px)→0, 0.9s, staggered via `data-d` (0.08s steps). IntersectionObserver; falls back to visible if no IO.
- Ambient: starfield (twinkle + drift), aurora blobs, Saturn breathing, cursor halo (lerp follow), scroll parallax (desktop >760), 3D tilt on portfolio grid.
- Micro: buttons lift -3px + glow; cards scale img + reveal "ver proyecto"; service rows expand chips on hover; nav underline grow.
- `prefers-reduced-motion`: disables cursor, parallax, tilt; reveals become instant; all animations ~0ms.

## Layout

- Max width `--maxw: 1360px`; gutter `clamp(24px, 4vw, 68px)`.
- Border radius: 2px on most boxes (sharp, intentional); web mockups use 8–10px (browser-chrome metaphor).
- Section rhythm: `clamp()` vertical padding, varies per section. Numbered section heads (01–05) — legitimate here as an ordered studio narrative, not eyebrow scaffolding.
- Grids: portfolio 4→3→2→1; benefits 2→1; web mockups 2→1; services = custom row grid.
- Sticky fixed header; vertical dot-nav (desktop >1180); floating WhatsApp + to-top FABs.

## Components

Header, dot-nav, hero (eyebrow + display h1 + tagline + sub + dual CTA), about (lead + body + stats + checklist `.why`), benefits grid, services row-list with hover chips, web-work browser mockups, portfolio tilt grid (Behance), contact (form + Calendly/WhatsApp/socials cards), footer, FABs. Icons: inline Lucide-style SVG injected via `{ICON_*}` token replace (no emojis).

## Backgrounds / Effects

Per-section: aurora blobs (radial-gradient, blur 120px), starfield layer (edge-positioned, parallax), section separators (`.sep` thin cream line), hero Saturn (ultra-blurred, opacity ~0.03 breathing). Content always `z-index:2` above ambient layers.
