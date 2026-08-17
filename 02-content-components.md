<!-- Content Canvas Rules — v1.0 — 17 August 2026 — part file 3 of 13 -->

> **PART 2 — CONTENT COMPONENTS**
> 
> | | |
> |---|---|
> | **Owner** | Content Canvas — **owns outright** |
> | **Domain** | Canvas & Surface Design (8) |
> | **Governs** | Media, text blocks, lists, tables, formulas, callouts. |
> | **Loaded when** | A board carries prose, a list, a table or a formula. |
> | **Requires** | `00-contract.md` + `01-foundations.md` + `12-rules.md` |
> | **Version** | v1.0 — 17 August 2026 |

> **What this file does not decide.** Type steps, colours, radii, shadows, spacing, the layout
> contract, motion and state values are defined in `01-foundations.md` and cited here by `§`
> number. If a value you need is not in this file, it is there — do not infer it. `§` refers to
> sections (numbered 0–45); `R` refers to rules (numbered 1–120) in `12-rules.md`. Both numbering spaces are
> permanent: numbers are added, never reassigned.

---
# PART 2 — CONTENT COMPONENTS

### 8b. Reveal order

§8 gives durations; nothing gave **sequence**. On a step-by-step maths board the order things appear *is* the explanation, so it cannot be left to DOM order.

1. **Frame first** — axes, grid, empty model, board title. The stage exists before anything happens on it.
2. **Given information** — the numbers or shapes the student starts with.
3. **One step at a time**, in the order a person would do them. Never two simultaneous reveals.
4. **Result last**, and never before the working that produces it.

- **120ms between steps**, using `riseIn`. A reveal that outruns reading is decoration.
- **Nothing already revealed moves when the next thing appears.** Reserve the space up front — a board that reflows on every step is unreadable, and it is the single most common animation defect.
- A student can **step back**. An auto-playing reveal with no way back is a video, not a board.
- Under `prefers-reduced-motion` everything is present immediately, in final position.

### 8c. Loading and failure

Every board that mounts an applet, media or data needs both states, or the student sees a blank canvas and assumes they broke it:

| State | Treatment |
|---|---|
| Loading | The board's frame at `muted`, no spinner over content, no layout shift when it arrives |
| Failed | A `#495057` `ti-alert-triangle`, one plain sentence, and a **Retry** secondary button. Never a raw error string |
| Slow (>3s) | Loading plus one line naming what is loading |

A failed applet **never blocks the module** — the nav row stays live so the student can continue.

## 9. Media

### 9.1 Boxes

| Token | Ratio | Radius | Use |
|---|---|---|---|
| `media-wide` | 16:9 | 16 | Scene, screenshot, video still |
| `media-standard` | 4:3 | 16 | Photograph, scan |
| `media-square` | 1:1 | 16 | Object, tile, grid cell |
| `media-portrait` | 3:4 | 16 | Standing figure, tall diagram |
| `media-circle` | 1:1 | 50% | A face or one cut-out object |
| `media-bleed` | 16:9 | 0 | Full-frame, the only thing on the board |

### 9.2 Rules

- **Always a fixed box + `object-fit:cover`.** Never let an image size itself.
- **No border, no shadow.** If it needs separation, put it in a card as a full-bleed section.
- **Caption outside**, below, 16/500 `#868e96`, `gap-tight`, aligned to the box's left edge.
- **Circles are for subjects** — a face, one object. Never crop a diagram or scene to a circle.
- **A row of media is equal ratio and equal height.** Never mix 16:9 with 1:1.
- **Height caps:** 200 single · 150 in a row of 2–3 · 120 in a row of 4+.
- **Placeholder:** `#f1f3f5` fill, centred `ti-photo` 24px `#adb5bd`, radius per box. Never coloured. **It may carry one `label`-size line in `#adb5bd` naming the asset** (`Applet 3 — Rapid fire`, `lesson-video.mp4`) — that is what makes a placeholder actionable for whoever sources it. Never more than one line.
- **One visual kind per board.** Media and diagrams never share a board.

### 9.3 Slot notation

Layouts declare media slots as `MEDIA[wide|standard|square|portrait|circle|bleed]`, so an author knows the ratio before sourcing the asset.

### 9.5 Diagram descriptions

Every diagram, chart, model and instrument carries a **one-sentence description** naming what it shows and its answer-bearing content — not its appearance.

- **Good:** "A number line from −5 to 5 with points plotted at −3 and 2."
- **Bad:** "Number line diagram." · "An image showing maths."
- **A board whose entire content is a diagram with no description is Tier A.** It is unreadable to a screen reader, unsearchable, and cannot be reviewed at scale.
- The description is authored with the diagram, in the same file. It is not alt text bolted on later.
- Decorative illustration (§30) takes an empty description — explicitly empty, never missing.

### 9.6 Scale honesty

- A figure drawn with stated measurements **is drawn to those measurements**. A triangle labelled 3-4-5 with a visibly wrong shape teaches the student not to trust the picture.
- When a figure genuinely cannot be to scale, it carries `Not to scale` as a `label` in `#868e96`, bottom-right of the figure. **This is required, not optional.**
- Two figures compared on one board share one scale, and that scale is stated once.
- A chart's bar heights are proportional to its values, always (§15a).

## 10. Text blocks

| Block | Spec |
|---|---|
| Prose | `body`, max 560, left-aligned past two lines |
| Lead-in | `body` at `#495057`, one sentence, directly under a title |
| Pull quote | 36/500 `#495057`, no quote marks, attribution 16/700 `#868e96` |
| Definition | Tint panel; term 24/800 accent, definition 24/500 `#495057` |
| Note / aside | Tint panel with a 20px icon, text 24/500 |
| Caption | 16/500 `#868e96` |
| Footnote | 16/500 `#868e96`, one line, board bottom-left |

## 11. Lists

| Kind | Marker | Row surface |
|---|---|---|
| Numbered | 32px badge, radius 12, accent fill, numeral 16/800 white | `surface-sunken` |
| Checklist | 32px badge, `ti-check` when done | `surface-sunken` |
| Bulleted | 8px accent dot, `gap-tight` | plain |
| Stepped | Numbered badges with a 1px `#e9ecef` connector between | plain |
| Key–value | `label` left, `body` right, 1px divider | plain |

Max **5 rows** per board; 3 is the target. Text is always `body`/500.

## 12. Tables

- Header row `label`/700 `#868e96`, uppercase, `.09em`.
- 1px `#e9ecef` row dividers only — **no vertical rules, no zebra fill.**
- Cells `body`/500; numerals tabular and right-aligned.
- Max **5 columns × 6 rows**. Beyond that it's a chart.
- First column left-aligned and may be 700 if it labels the row.

## 13. Formulas & notation

- Formula card: `surface-card`, radius 16, padding `12px 26px`, `resting` shadow.
- Formula text 36/800 `#212529`; the subject term takes the accent (§3.2).
- Fractions: stacked, 24/800, 2px `#7950f2` rule, `line-height:1.05`.
- Operators get `gap-tight` breathing room on both sides.
- Variables italic; numbers upright.
- A derivation is one row per transformation, with only the changed term accented.
- Units 16/700 `#868e96`, never italic.

### 13.1 Fractions

| Part | Spec |
|---|---|
| Stack | Numerator and denominator centred on one axis, `tabular-nums` |
| Bar | **1.5px `#495057`**, width = the wider term + 4 units |
| Bar colour | Inherits ink. **Never its own hue** — a violet bar with a blue numerator and a maroon denominator is three colours saying nothing |
| Colour | A term takes an anchor **only** when it is an anchored referent (§34). Otherwise both are ink |
| Size | Both terms at the parent step; the fraction occupies two lines of that step |
| Inline | A fraction inside prose uses the solidus form `3/4` — never a stacked fraction inside a sentence |

### 13.2 Maths glyphs

Authors type what their keyboard offers, so one module contains both `-3` and `–3`. **One glyph per operator, always the Unicode form:**

| Use | Glyph | Not |
|---|---|---|
| Negative sign / minus | `−` (U+2212) | `-` hyphen, `–` en dash, `—` em dash |
| Multiplication | `×` | `x`, `*` |
| Division | `÷` | `/` (the solidus is for inline fractions only) |
| Equals, not-equals | `=`, `≠` | `!=` |
| Comparison | `<`, `>`, `≤`, `≥` | `<=`, `>=` |
| Ellipsis in a sequence | `…` | `...` |
| Degree, prime | `°`, `′` | `o`, `'` |

The negative sign and the minus operator are the **same glyph**, spaced differently: `−3` closed up, `5 − 3` with a hair space either side. Fully automatable — run it on every module (§38.3).

### 13.3 Geometry, algebra and set glyphs

| Use | Glyph | Not |
|---|---|---|
| Angle, triangle, arc | `∠`, `△`, `⌒` | `<`, `^` |
| Parallel, perpendicular | `∥`, `⊥` | `//`, `\|\|`, `T` |
| Congruent, similar | `≅`, `~` | `=~`, `≈` |
| Approximately, therefore | `≈`, `∴` | `~=`, `so` |
| Degree, prime, double prime | `°`, `′`, `″` | `o`, `'`, `"` |
| Root, pi, plus-minus | `√`, `π`, `±` | `sqrt`, `pi`, `+/-` |
| Set membership, subset | `∈`, `⊂`, `⊆` | `belongs to` |
| Union, intersection, empty | `∪`, `∩`, `∅` | `U`, `n`, `{}` |
| Ratio, proportion | `:`, `::` | `to` |
| Repeating decimal | overline on the repetend | `...`, a dot |
| Function mapping | `→` | `->` |

**Primes are the image notation** (§17c): `A′` is the image of `A`. Never an apostrophe — it renders as a quote and breaks at the wrong size.

**Module titles obey the same table.** The library currently contains `⟂ & ∥ Mixed Booster` alongside titles using ASCII substitutes; titles are normalised with the boards (§43.4).

## 14. Callouts & chips

| Kind | Spec |
|---|---|
| Eyebrow chip | 16/700 uppercase `.09em`, accent ink on its tint, radius 8, `6px 12px`, 14px icon |
| Status badge | Radius 999, tint fill, accent ink 16/700 |
| Key-idea panel | Tint panel, radius 12, `14px 16px`, 20px icon + 24/500 text |
| Warning | Emphasis tint, `ti-alert-triangle` |
| Numeral badge | 32px, radius 12, accent fill, 16/800 white |

One callout per board.

---
