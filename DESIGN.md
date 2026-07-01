# Design

Visual system for the Chester Bowl site. Register: **brand**. Full art-direction rationale + references: `/tmp/chester/aesthetic-direction.md`.

## Theme

**Punk snowboard-zine photo-collage for a kids' ski hill + summer camp.** Cut-and-paste energy, halftone grit, and one signature device — **diagonal color ribbons/wedges slicing across the layout, cutting behind a snowboarder mid-trick.** Fun and loud for kids, but with clear hierarchy and AA-legible type for the parents doing the registering. The black woodcut logo (giant ski jumps) is the crest; color lives around it, never on it.

Light theme (paper ground), not dark. Physical scene: a Duluth parent on a phone in July signing their kid up for camp, or a teen in December checking the terrain park — both should feel the hill's punky joy in two seconds and find the button in three.

## Color palette (OKLCH)

Ink + paper base, punchy punk accents, **season-flex** on one accent axis:

- `--ink`  oklch(0.20 0.02 250) — near-black, all body + line art + the logo. (AA-safe on paper.)
- `--paper` oklch(0.96 0.01 95) — warm off-white ground (NOT a saturated cream; low chroma).
- `--surface` oklch(0.99 0.005 95) — cards/panels lift.
- `--cyan` oklch(0.78 0.13 210) — **turquoise ribbon** (the signature diagonal), winter accent. (From references #2/#3.)
- `--blaze` oklch(0.68 0.20 45) — **blaze orange** hot accent / primary CTA (ski-patrol/terrain-park energy).
- `--pine` oklch(0.55 0.12 155) — **summer** accent (day camp / green season).
- `--gold` oklch(0.83 0.15 90) — powder-gold pop / highlight blocks (references #4).

**Contrast is non-negotiable:** body text is `--ink` on `--paper` (well past 4.5:1). White text only over sufficiently dark photo/ink areas; on cyan/gold use `--ink`, never white. Blaze CTA uses white text (verify ≥4.5:1) or ink — test it.

**Seasonal theming:** Summer mode → `--pine` is the live accent; Winter mode → `--cyan`; `--blaze` + `--gold` stay in both as the punk pop. Toggle re-themes via a `data-season` attribute on `<html>`.

## Typography (Google Fonts)

- **Display / hero:** `Anton` (bold, tall, condensed, high-impact + clean; shears well for the P5 angular energy). Alt: `Bebas Neue` / `Archivo Black`. **NOT `Bagel Fat One`** — its fat/round bubbliness was rejected as distracting and fighting the angular direction. Keep `Bungee` for small sticker/patch/badge labels (blocky, bold). Layer/overlap headline words; outline or hard-offset-shadow one layer; italic/shear for kinetic P5 feel.
- **Hand annotation:** `Shantell Sans` for marker-style callouts ("the jumps live on", "sign up!").
- **Body / UI:** `Nunito` (rounded, friendly, very readable) — this carries all real content + forms.
- Rules: hero clamp() max ≤ 6rem; display letter-spacing ≥ -0.04em; `text-wrap: balance` on headings; body 65–75ch; pair on contrast (fat-display + rounded-humanist), not two similar sans.

## Motifs & devices

- **Diagonal ribbon/wedge** — the signature. Cyan/blaze bands cutting across sections at ~15–25°, passing behind cut-out photos. Section transitions are angled cuts, not flat lines.
- **Photo-collage cut-outs** — silhouette a snowboarder mid-grab/rail from the asset pack, thick sticker outline, break the frame. The airborne rider is the single most on-brand image.
- **Halftone / photocopy** duotone on photos (ink+accent), riso-flat fills.
- **Die-cut stickers / merit-badge patches** — one per program (Terrain Park / Freestyle Fridays / Learn to Ride / Summer Camp), tilted ±3–6°, doubling as nav/wayfinding.
- **The ski-jump silhouette** (from the logo) as a ghosted watermark / "the jumps live on" heritage beat — proud sticker, never sepia.
- Torn-paper/tape edges, chunky buttons with hard offset shadows, black-ink doodles (pines, board, rail).

## Photo treatment

Real Chester Bowl photos only (`assets/chester/pack/`, `MANIFEST.json`). Prioritize **snowboard/terrain-park action** for winter, **kids/camp/summer** for summer. Treatments: halftone-duotone the loudest hero; sticker-cutout 1–2 focal images breaking the grid; bold black borders + slight tilt on others; keep 1–2 clean full-color so it's warm, not all-effect. No stock, no generated images.

## Layout

Mobile-first. Maximal collage energy in heroes (ribbons + cutout + logo) over a calm, readable content grid below — NOT a uniform card grid (impeccable ban). Color-blocked program bands with angled dividers; controlled tilt but headline/body text stays horizontal + legible. Winter block leads with **Terrain Park / Freestyle Fridays**; summer block leads with **Day Camp registration**. Every mode leads with a clear primary action (Register / Buy Pass) + the scholarship promise.

## Seasonal architecture (required)

A prominent **Summer/Winter toggle** in the header. JS auto-defaults to the current season (May–Oct → summer, Nov–Apr → winter; it's July → summer). Both content sets live in the DOM (show/hide), so it works as a static page; persist manual choice in localStorage. Shared across modes: header (logo+toggle), about, get-involved (volunteer/donate/scholarships), contact, footer. Season-specific: hero, programs, primary CTA, live accent.

## Motion

Purposeful, not reflexive. Sticker "slap-in" (scale+settle, ease-out-quart) on badges; ribbon draw/parallax on scroll; hover tilt on stickers/buttons. Staggered reveals per list, each fitting what it reveals. Full `prefers-reduced-motion` fallbacks (crossfade/instant). Content visible by default — never gate visibility on a transition class.

## Bans (impeccable)

No cards-as-default / identical card grids; no uppercase tracked eyebrows on every section; no numbered-section scaffolding; no gradient text; no side-stripe borders; no glassmorphism-default; no hero-metric template; no cream-plus-one-accent SaaS look (the exact failure of the rejected v1). No headline overflow at any breakpoint.
