# Byjus.AI — Design System

Scanned from the shipped product pages: `Home Page.dc.html` + `app-cosmos.js`, `Teaching Room.dc.html`, `Chapter Journey.dc.html`, `Onboarding v2.dc.html`.

The system is a **Mantine-derived** palette (10-step hue scales, hairline borders, soft layered shadows, system font stack) with three product-specific departures: a **lavender→cream page canvas** instead of Mantine's flat white, **violet-tinted shadows** instead of neutral black, and a **character colour language** (Vyom = violet, Spark = yellow).

---

## 1. Foundations

### 1.1 Page canvas

One gradient, on every page — this is the product's most recognisable surface.

```css
linear-gradient(180deg, #eee9fd 0%, #f8f5fe 46%, #fdfaf0 100%)
```

Pale purple → near-white lavender → pale cream. Exposed as `CANVAS` in `app-cosmos.js`; written literally in each `.dc.html`.

**Dot lattice** overlays the canvas on Home, Chapter Journey, and Onboarding:

```css
background-image: radial-gradient(rgba(96,74,190,.13) 1px, transparent 1px);
background-size: 24px 24px;
```

**Ambient blobs** — two blurred radial washes, top-left violet and bottom-right warm, both under everything:

```css
radial-gradient(circle, rgba(190,170,255,.22), transparent 70%)   /* filter: blur(12px) */
radial-gradient(circle, rgba(255,196,150,.20), transparent 70%)   /* filter: blur(14px) */
```

### 1.2 Colour

**Primary — Mantine blue.** The one saturated accent. CTAs, active states, progress fills.

| Token | Hex | Use |
|---|---|---|
| `BLUE` / blue-5 | `#339af0` | An ordinary blue step — **not** a button gradient (retired 2026-08-19, §20) |
| `BLUE7` / blue-6 | `#1c7ed6` | Links, icon accents |
| `BLUE9` / blue-8 | `#1864ab` | Pressed, deep accents |
| `BLUE2` | `#a5d8ff` | Focus rings, active hairlines |
| `BLUE1` | `#d0ebff` | Selected chip fill |
| `BLUE0` | `#e7f5ff` | Tinted panel / featured bubble |

~~Primary button is always the vertical pair.~~ **Retired 2026-08-19** — §20 bans gradient fills on every button without exception. A primary button is a flat `base` fill at the board's anchor angle on a solid base edge (§20.0.1).

**Violet — Vyom / AI.** Every AI surface, every shadow tint.

| Token | Hex | Use |
|---|---|---|
| `VIOLET` | `#7950f2` | Vyom accents, onboarding CTA top |
| `VIOLET9` | `#5f3dc4` | Breadcrumb active, deep violet text |
| `#6741d9` | — | Onboarding CTA bottom, back-button icon |
| `VIOLET2` | `#d0bfff` / `#b197fc` | Hover borders, past-step dots |
| `VIOLET0` | `#f3f0ff` / `#f4f1ff` | Vyom bubble fill, hover wash |
| `#e5dbff` | — | Violet hairline (chat edge, handle border) |

**Yellow/orange — Spark, streaks, goals.**

| Token | Hex | Use |
|---|---|---|
| `TEAL` (misnamed; Spark) | `#f59f00` | Spark accents |
| `TEAL2` | `#ffe066` | Spark highlight |
| `TEAL8` | `#e8590c` | Streak flame, streak text |
| `TEAL9` / goal bar | `#d9480f` | Goals progress fill, goal percentage |
| `#fff4e6` | — | Streak pill fill, Spark bubble |
| `#ffe0b3` | — | Streak pill border |

**Semantic.**

| Meaning | Hex |
|---|---|
| Success | `#40c057` (green-6) · deep `#2f9e44` · fill `#dcf7e1` · border `#b2f2bb` |
| Error / fail | `#fa5252` (red-6) · deep `#c92a2a` |
| Locked / disabled | `#8f8aa8` icon · `rgba(33,26,74,.09)` fill |

**Text.**

| Token | Hex | Use |
|---|---|---|
| `INK` | `#212529` | Headings, primary text |
| `TXT` | `#343a40` | Body, option labels |
| Deep violet ink | `#211a4a` | Text on canvas (goal statements, chapter titles) |
| Muted | `#5d5880` · `#6b6390` | Secondary text, meta |
| Eyebrow / label | `#6f66a3` · `#7a749b` | Uppercase micro-labels |
| `DIM` | `#868e96` | Icons, placeholders |
| Faint | `#a9a3c4` · `#adb5bd` | Chevrons, future states |

**Neutrals** — cosmic-tinted, not pure grey.

`G0 #f6f5fd` · `G1 #efedfa` · `G2 #e6e3f5` · `G3 #ddd9ee` · `G4 #cdc8e2` · `G5 #a9a3c4`

Structural border is `#dee2e6` (Mantine gray-3) on cards and inputs, `#e6e3f5` on canvas-level chrome.

### 1.3 Type

**One font stack. Nothing downloaded.**

```
-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif
```

SF Pro on Apple, Segoe UI on Windows, Roboto on Android.

**8 sizes, 3 weights** — no half-pixel steps, no ad-hoc values.

| Token | Size | Weight | Use |
|---|---|---|---|
| `--fs-display` | 38px | 800 | Celebration headline |
| `--fs-title` | 30px | 800 | Chapter titles, board titles |
| `--fs-heading` | 24px | 700 | Modal titles, onboarding questions |
| `--fs-subheading` | 20px | 700 | Sub-headings, "Locked" |
| `--fs-body` | 16px | 500 | **Default** — bubbles, rows, inputs |
| `--fs-secondary` | 14px | 500 | Meta, chips, buttons |
| `--fs-caption` | 12px | 600–700 | Breadcrumb, badges |
| `--fs-eyebrow` | 11px | 700 | Uppercase labels, `+.08em` tracking |

Weights: `--fw-regular:500` · `--fw-bold:700` · `--fw-heavy:800`.

Headings carry `letter-spacing:-.01em` to `-.02em`. Body line-height 1.4–1.55; headings 1.3.

**Documented exception** — Chapter Journey's decorative chapter numerals are graphic, not text: `--fs-numeral-sm:44px` · `-md:48px` · `-lg:58px`.

### 1.4 Radius

| Value | Use |
|---|---|
| 8px | Segmented-control inner button |
| 10–11px | Small icon buttons, chips, pills, active badges |
| 12px | Logo tile, icon tiles, footer buttons |
| **14px** | **Default card** — resume cards, popovers, inputs, tiles |
| 16px | Bubbles, composer, expanded panels |
| 18–20px | Detail hero, module labels, larger panels |
| 24px | Room-card gutter |
| 999px | Progress tracks, streak pill, avatars |

### 1.5 Shadow

Never neutral black — always violet-tinted, four steps.

```css
SH_XS  0 2px 6px -3px rgba(70,46,146,.16)     /* resting card */
SH_SM  0 6px 14px -8px rgba(70,46,146,.22)
SH_MD  0 10px 24px -12px rgba(70,46,146,.30)
SH_LG  0 14px 30px -18px rgba(70,46,146,.36)  /* popover, raised */
```

Two more special-purpose forms:

- **Soft downward lift** (fill-less chrome — goals and streak widgets): `0 8px 14px -10px rgba(70,46,146,.34)`
- **Coloured button glow**: primary `0 4px 12px rgba(28,126,214,.35)`, violet CTA `0 10px 26px -12px rgba(103,65,217,.6)`

### 1.6 Spacing

Mantine scale: `xs 10 · sm 12 · md 16 · lg 20 · xl 32`.

In practice: 6–9px inside compound controls, 14–18px card padding, 22–28px section gaps, 24–28px page gutter. **Always flex/grid + `gap`**, never margin chains.

### 1.7 Motion

| Duration | Curve | Use |
|---|---|---|
| 120–180ms | `ease` | Hover, colour, background |
| 300–340ms | `cubic-bezier(.2,.8,.3,1)` | Enter/exit, popover |
| 420–600ms | `cubic-bezier(.4,0,.2,1)` | Layer slides, panel travel |
| 700ms | `cubic-bezier(.2,.8,.3,1)` | Progress fills |
| 1.15s | `cubic-bezier(.33,0,.2,1)` | Answer light leak |

Named keyframes: `bob` (mascot idle, 2.6–3.4s) · `popIn` · `riseIn` · `twn` (twinkle) · `dockripple` · `tipRing`. Everything decorative is disabled under `prefers-reduced-motion`.

### 1.8 Icons

**Tabler Icons** webfont — outline, 1.5px stroke, 24px grid.

```html
<link href="https://cdn.jsdelivr.net/npm/@tabler/icons-webfont@3.24.0/dist/tabler-icons.min.css">
<i class="ti ti-flame"></i>
```

Sizes: 13–15px inline, 17–20px in controls, 23px in tiles. No emoji as icons (a single 👋 in the greeting is the one exception).

### 1.9 Mascots

| | Vyom | Spark |
|---|---|---|
| Asset | `<vyom-rive>` (live Rive) | `spark-mascot-sm.png` |
| Role | AI tutor — teaches, guides | Study buddy — small questions |
| Colour | Violet | Yellow/orange |
| Bubble | `#f4f1ff` on `#3a3450` | `#fff4e6` on `#8a4712` |
| Idle | `bob` 2.8–3.4s | `bob` +0.4–0.6s delay |

`<vyom-rive>` inflates its canvas by `art-scale` (default 2.5) because the artboard carries transparent padding. **Any fixed-size mount must set `overflow:hidden`** or the art bleeds out of its box.

---

## 2. Components

### 2.1 Buttons

**Primary** — **see §20 and §20.0.1–20.0.3, which supersede this row (2026-08-19).** A primary button
is `base` fill at the board's anchor angle, white 800, radius 20, `20px 34px`, on a **5px flat base
edge** that the press spends: the face travels down by exactly the edge height and lands level with
the page. That travel is the entire press.

> **This row said `linear-gradient(180deg,#339af0,#1c7ed6)` with a blue glow until 2026-08-19.**
> Both are banned by §20's own list — *"Banned on every button, without exception: gradient fills ·
> text shadow · a lit top face or inner highlight · outer glow that is not `attention` (§8a.3) ·
> a drawn hand or pointer beside it · scale or bounce on press."* The `brightness(1.07)` + scale
> hover is the same list's last clause. This document is the earlier per-component geometry that
> §20.0 states it supersedes; the conflict was internal to canvas, and it is resolved toward §20.
> Colour comes from **state**, depth from the base edge, and feedback from the press travel.

**Secondary** — white fill, `1.5px #dee2e6`, `#343a40` label, `SH_XS`. Hover: `#f3f0ff` wash, border → `#b197fc`.

**Ghost / icon** — 44px square, radius 11px, white, `1px #e6e3f5`, violet icon.

**Text link** — no fill or border, `#5d5880` 600, underline at `3px` offset, `1px` thickness; hover → `#1c7ed6`.

**Nav arrows** (Teaching Room) — 46px squares, chevron only, no label.

### 2.2 Cards

Default: white, radius 14px, `1.5px #dee2e6`, `SH_XS`, 16px padding. Hover raise: `translateY(-2px)` + `SH_LG` + violet border.

**Island / hero surface** — a plain three-stop gradient, no gloss:

```css
linear-gradient(158deg, #ffffff 0%, #fbfaff 48%, #f1ecff 100%)   /* neutral */
linear-gradient(158deg, #ffffff 0%, #f7fdf8 46%, #dcf7e1 100%)   /* completed */
```

**Fill-less chrome** (goals, streak) — no background, no border, only the soft downward lift. Expanding swaps in the canvas gradient plus `0 14px 30px -14px rgba(70,46,146,.28)`.

### 2.3 Inputs

56px tall, radius 14px, white, `1.5px #dee2e6`, `SH_XS`, 18px/600 text, `caret-color:#228be6`, leading icon at 16px.

**Search + dropdown fuse into one component**: while open the field's radius becomes `14px 14px 0 0`, and the panel is pinned at `top:54.5px` (field height minus its border) with `border-top:none` and radius `0 0 14px 14px`, so the two hairlines overlap into one.

### 2.4 Chips & options

Option row: 15×17px padding, radius 14px, white, `1.5px #dee2e6`. Selected adds `.on` — `#d0ebff` fill, blue border, blue label, check icon.

Pills: radius 999px, 8×14px padding, tinted fill + matching border (streak = `#fff4e6` / `#ffe0b3`).

### 2.5 Progress

**Bar** — 5–6px tall, radius 999px, track `rgba(33,26,74,.13)`, fill the semantic colour, `width` transition 700ms.

**Module bar with step nodes** (Teaching Room) — a track with one dot per step, first and last on the ends. Completed nodes filled, upcoming nodes the track colour. A travelling tip (`.tr-tip`) rides the fill with three staggered looping rings, hidden by class at rest.

**Milestone dots** (Onboarding) — 7px dots, active one stretched to 20px; violet-7 current, violet-3 past, `#dcd8e6` future.

### 2.6 Chat

- **Vyom row** — mascot 38px + bubble `4px 15px 15px 15px` (tail top-left), `#fff` or `#e7f5ff` when featured, `1px` border, "Listen" TTS affordance below.
- **User row** — right-aligned, `15px 4px 15px 15px`, blue gradient fill, white text.
- **Typing** — three 5px dots, `hpDots` 1.1s staggered 0.18s.
- **Composer** — 16px radius, white, hairline, paperclip + input + mic + 40px send. Inert states drop the whole component to `opacity:.2` with `pointer-events:none` rather than half-disabling it.

### 2.7 Answer feedback

Not a border or a card tint — a **corner light leak** on the page shell's `::after`:

- Bottom-left, `70vw × 45vh`, `transform-origin: 0% 100%`
- Six-stop radial ramp halving each step (`.88 → .62 → .34 → .15 → .05 → transparent`) so there's no visible ring
- Swells from `scale(.92)`, 1.15s in and out on the same curve
- `z-index:0` — beneath the content canvas, nav, chat, and dock

### 2.8 Overlay / popover

Radius 16–18px, white, `1.5px #dee2e6`, `SH_LG`, 8–18px padding. Enter with `hpIn`/`popIn`. Dismiss with a **capture-phase `pointerdown` listener on `document`**, not a fixed scrim — an animated ancestor's `transform` makes it the containing block, so `position:fixed; inset:0` covers only that ancestor.

---

## 3. Layout & z-order

Every page is the same three-layer stack:

1. **Page shell** — full-height, the canvas gradient, `overflow:hidden`. Owns the ambient light (`z:0`) and the answer leak (`z:0`).
2. **Card gutter** — transparent fill/border, radius 24px, `overflow:hidden`. The clip boundary: any glow or shadow reaching past it gets sliced into a hard line.
3. **Content canvas** — `container-type:size` grid centring the 16:9 stage.

Teaching Room z-order: canvas `1` → nav + progress `6` → chat window, dock, composer `30` → video `20` (`80` full-screen).

---

## 4. Rules

1. **One saturated accent per screen.** Blue for action, violet for AI, orange for progress/streak, green/red only for outcome.
2. **Shadows are violet, never black.** Use the four `SH_*` steps.
3. **Hairlines do the structural work** — 1–1.5px borders before shadow.
4. **Fill-less chrome for ambient widgets.** Anything that isn't a container (goals, streak, logo, top chrome) has no background and no stroke — only a soft downward lift.
5. **8 sizes, 3 weights.** No new type values.
6. **No gradient backgrounds beyond the canvas.** Gradients are for buttons and card surfaces only.
7. **Sentence case everywhere.** Buttons are short imperatives — "Continue", "Start my first class", "Skip this".
8. **Motion is functional.** Nothing decorative survives `prefers-reduced-motion`.
9. **`gap`, not margins.** Sibling groups always flex/grid.
10. **No emoji as iconography.** Tabler only.

---

## 5. The dark room

Source: Hithesh's *Dark Mode — Colour Adoption*. The **content-canvas** dark reference is now the dual-mode `Design Component Systems.dc.html` (toggle the room — it carries both columns and measures its own contrast in each), which supersedes the separate `Component Systems - Dark.dc.html`. The player-chrome dark references (`Teaching Room - Dark.dc.html`, `Chapter Journey - Dark.dc.html`, `Home Page - Dark.dc.html`) belong to the AI-tutor product, not the journey studio, and are out of scope here. This section carries the parts that govern the **content canvas** — the boards and their components.

### 5.1 The premise

**A component never decides whether it is light or dark — the room does.** The canvas is transparent, so a board inherits the surface it sits on; that only works if every colour is a **role resolved per room**, never a fixed hex. **The dark room is a palette resolution, not a redesign:** every size, weight, radius, gap, duration, easing, dash pattern and vertex position is identical between the rooms. If a component needs different geometry in one room, the component is wrong.

The role values and the generated ladder — both columns — live in `01-foundations.md §3.1a` and `§3.7`; the dark shadow set in `§6`. Adopt those first.

### 5.2 Depth

**Shadows are depth, never brand.** Every dark-room shadow is pure black — a hued glow on near-black reads as a smear. Large soft shadows smudge on a dark canvas, so keep them tight and raise the alpha, not the blur (`§6`). The one white allowed is the lit top edge that gives a filled control its form: `inset 0 1px 0 rgba(255,255,255,.32)`, replacing the light room's button gradient.

### 5.3 Components

**Buttons, sliders, counters** — the per-state dark resolution and the specific inversion each carries is `05-interactive.md §20.0.5` (the section a seat building a control reads). In one line each: a button's `base` face takes **`canvas` ink** in dark (it is a *light* fill there); a slider's filled track is the **bright** part and its thumb is the **brightest** thing on the control; a counter's value tile is a dark fill with **light** ink — inverting the fill while leaving the ink `deep` makes the numeral invisible.

**Figures, graphs, number lines** (`03-data-maths-diagrams.md`):

- **Fills** — pale fill + saturated stroke in both rooms, but in the dark room the *fill* is the alpha tint and the stroke is the room's accent. A pale hex fill would glow.
- **Vertex and axis labels** sit on the room's `surface`, not on a light face, so they take the ladder's **`text`** stop. `deep` on `surface` is the same luminance — a 1.00:1 invisible label.
- **Hidden edges** — `faint`, dashed; the three dash patterns keep their three meanings (`6 4` hidden, `2 6` construction, `4 4` ghost).
- **Grid and lattice invert** — light room: dark dots at low alpha; dark room: *light* dots at low alpha. A "darken the dots" sweep erases them.

**Illustrations** (`07-illustration.md §31.7`): a palette resolution, never a redesign. Structural neutrals become `surface2` / `line2` / `dim`; a `light` background plane becomes an **alpha tint of the same hue**, never the pale hex — a pale plate is the class §5.7 exists to catch. The measured dark column for the ten extended hues and the five skin tones is still owed.

**Media scrims — the one place light ink is correct in the dark room.** A translucent near-black scrim over an image or video takes `ink` (light), in both rooms. Sweeping it to `canvas` gives near-black on near-black (~1.05:1). This is the exact inverse of the accent-fill rule, which is why a single-direction sweep cannot satisfy both.

### 5.4 Contrast

AA in both rooms, with the large-text exemption (≥24px, or ≥18.66px bold → 3:1); meaningful non-text shapes need 3:1. Every dark role measured against `surface #262038`: `ink` 9.5 · `dim` 5.5 · emphasis 7.3 · action 5.9 · concept 5.4 · correct 6.5 · wrong 5.5. Two rules that are easy to get backwards are in `§3.1a`: a *light* accent fill takes `canvas` ink; an ink authored for a light plate is not a dark-room ink — after inverting a fill, re-check every ink that sat on it.

### 5.5 Adopting the theme — the order that works

1. **Roles first** (`§3.1a`). Do not start on components.
2. **Shell and shadows** — room, lattice, the black shadow set (`§6`).
3. **The ladder** — swap the `oklch()` constants for the dark column (`§3.7`). This is the step a hex sweep cannot do.
4. **Fills, programmatically.** Classify every colour literal by the property it feeds: a **fill** inverts, an **ink** does not. Enumerating by hand does not converge — an unlisted value survives silently.
5. **Then the inks that landed on the fills you just moved.**
6. **Then the six inversions** (§5.6), each the opposite of the sweep.
7. **Measure last, and properly.** `getComputedStyle` returns `oklch()` verbatim; a naive rgb parse of that string reports a false **1.00:1**. Convert through a canvas (`ctx.fillStyle = css`, then `getImageData`).

### 5.6 The six inversions

Everything else is a substitution; these six need the *opposite* of the sweep, and each shipped a real defect before it was written down:

1. **Figure fills** — the fill becomes the alpha tint; the stroke becomes the accent.
2. **Translucent scrims over media** — keep light ink. The only such place in the dark room.
3. **Grid and lattice** — dark dots become *light* dots.
4. **The ladder's `base` face** — a dark fill in light, a light fill in dark, so its ink flips with it.
5. **Disabled states** — recessive is not illegible; a disabled numeral still owes 4.5:1 against its own fill.
6. **An ink authored for a light plate** — inverts with the plate it used to sit on.

### 5.7 Audit

A source regex over `#rrggbb` alone reports a false clean — it misses `rgba()` and `oklch()`, and a **light fill with dark ink measures fine** because it is internally consistent as a light-mode component (the class that once survived a clean sweep). Contrast alone never finds it; only a **lightness check** does — a `fill` at `oklch(L ≥ 66%)` is a light plate wherever it lands. The live pass walks every element collecting `color / backgroundColor / fill / stroke / borderTopColor / backgroundImage / boxShadow`, converts each through a canvas, and checks it against the element's own size and weight; any iframe is audited separately through `contentDocument`. The applet gate's mechanical half of this is `skills/gates/lib/measure.mjs` (`canvasAudit`) → `transcript-checks.mjs` (`checkCanvasAudit`).
