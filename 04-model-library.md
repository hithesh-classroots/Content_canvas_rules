<!-- Content Canvas Rules — v1.0 — 17 August 2026 — part file 5 of 13 -->

> **PART 3B — THE MODEL LIBRARY**
> 
> | | |
> |---|---|
> | **Owner** | Content Canvas — **feeds** |
> | **Domain** | Pedagogy & Arc (1) |
> | **Governs** | The concrete manipulatives: counting, fractions, bar models, structure diagrams, instruments, notation, equation working. |
> | **Loaded when** | A board carries a manipulative or a worked model. |
> | **Requires** | `00-contract.md` + `01-foundations.md` + `12-rules.md` |
> | **Version** | v1.0 — 17 August 2026 |

> **What this file does not decide.** Type steps, colours, radii, shadows, spacing, the layout
> contract, motion and state values are defined in `01-foundations.md` and cited here by `§`
> number. If a value you need is not in this file, it is there — do not infer it. `§` refers to
> sections (numbered 0–45); `R` refers to rules (numbered 1–120) in `12-rules.md`. Both numbering spaces are
> permanent: numbers are added, never reassigned.

---
# PART 3B — THE MODEL LIBRARY

**One model per job, drawn the same way every time it appears in the library.** §36.2 says a module uses one visual model; this part says what the legal models *are*. A model not listed here is a new entry, added before use.

## 17d. Counting & early number

| Model | Spec | Used by |
|---|---|---|
| **Counter** | 36-unit circle (Early: 44), flat accent fill, no shadow. Countable objects are identical | Counting, one-to-one, sharing |
| **Ten-frame** | 2×5 grid, 44-unit cells, 1.5px `#adb5bd`, filled left-to-right then top-to-bottom | Number bonds, adding to 10, doubles |
| **Dot pattern** | Fixed dice/domino arrangements, never re-arranged between boards | Subitising, visual dot representation |
| **Tally** | Four 2.5px verticals + a diagonal fifth, groups spaced 14 apart | Tally marks, tally tables |
| **Base-10 blocks** | unit 20· rod 20×200 · flat 200² · cube isometric (§16c). One tone per place | Place value, rods and flats, regrouping |
| **Number bond** | A whole in a circle, two parts below, 1.5px `#adb5bd` connectors | Decomposing, number pairs |
| **Group ring** | 1.5px dashed `#adb5bd` enclosure around counters | Making equal groups, division |

**A counter is never an illustration.** No faces, no fruit, no themed art — the object must be countable at a glance, and decoration slows counting.

## 17e. Fraction models

| Model | Spec |
|---|---|
| **Area — bar** | The default. 400×80 rectangle, 1.5px `#495057`, equal partitions, shaded parts accent at 0.85 |
| **Area — circle** | Only for halves, thirds, quarters, sixths, eighths. Beyond that, humans cannot compare sectors |
| **Set** | Counters in a group ring, shaded members in accent |
| **Number line** | §17a, with the denominator as the minor-tick subdivision |
| **Fraction strip stack** | Bars of equal total length, stacked, one row per denominator, aligned left |

- **Partitions must be geometrically equal**, measured, not eyeballed — the whole concept is equal parts.
- **One whole is one size across the entire module.** Comparing ⅓ and ½ with different-sized wholes is the classic fraction error, and it is a §36.5 Tier A failure.
- Unshaded parts are `#fff` with the same outline — never `excluded` grey; they are still part of the whole.

## 17f. Bar / tape models

For ratio, proportion, comparison, part-whole word problems, factors and multiples.

| Part | Spec |
|---|---|
| Segment | Height 56, 1.5px `#495057`, accent `tint` fill, **equal segments are equal widths, measured** |
| Label | Inside when it fits, otherwise on a bracket below |
| Bracket | 1.5px `#868e96`, 8-unit end caps, label centred |
| Unknown | `?` in `figure`/800 accent inside the segment |
| Comparison | Two bars, left-aligned, gap 14 — the difference is the visible overhang |

A tape model is **not** a bar chart (§15). It has no axis and its length encodes a quantity relationship, not a measured value.

## 17g. Structure diagrams

| Model | Spec |
|---|---|
| **Factor tree** | Branches at 45°, 1.5px `#adb5bd`; composite nodes ink, **prime leaves circled** 2px accent |
| **Step / ladder** | Divisor column left, quotients descending, 2px `#495057` L-rules; final row boxed |
| **Probability tree** | Left-to-right, branch label above the line, probability below, outcomes in a right-hand column |
| **Sample-space grid** | Table with both dice/coins on the axes; the counted cells take accent `tint` |
| **Arrow / mapping diagram** | Two ovals, elements listed, one arrow per pair (§16a); a many-to-one fan is the point, so never tidy it away |
| **Pattern strip** | Terms in a row with position numbers below, the next term as an empty 2.5px dashed slot |

## 17h. Measurement instruments

| Model | Spec |
|---|---|
| **Ruler** | Major tick 16 units + label, minor 8, zero at the object's left edge — **always show the zero end** |
| **Protractor** | Semicircle, both scales, centre cross on the vertex, the measured arm highlighted in accent |
| **Balance scale** | Symmetric pans, beam tilt proportional to the difference, level when equal |
| **Beaker** | Graduations with labels, liquid at accent 0.85, flat surface — no meniscus, no gloss |
| **Clock** | Hour hand 0.55× radius / 3px, minute 0.85× / 2px, 12 major + 60 minor ticks, numerals at Early band only |

An instrument is a **diagram, not an illustration** (§30) — its scale must be accurate enough to read the answer off it.

## 17i. Arithmetic notation

The column-arithmetic cluster is ~60 modules and had no spec. **Alignment is a correctness issue** — misaligned columns teach the wrong algorithm.

| Part | Spec |
|---|---|
| Digits | `figure`/700, **`tabular-nums` mandatory**, one 44-unit column per place |
| Rule line | 2px `#495057`, spanning the widest row + 8 units each side |
| Operator | Left of the last row, outside the digit columns |
| Carry | Above its column, 0.5× the digit size, emphasis orange |
| Borrow | Struck original 1.5px `#adb5bd`, new value above it at 0.5×, emphasis orange |
| Partial product | Its own row, place-shifted, `muted` until it is the current step |
| Long division | 2px bracket; quotient above, aligned to the dividend's places; each bring-down on its own row |
| Current step | §8a `emphasis` on that column only — never a coloured box around the whole sum |

## 17j. Equation working

| Part | Spec |
|---|---|
| Step stack | One equation per row, **`=` signs vertically aligned across every row** |
| Operation note | Right of the row, `label`/700 `#868e96`, e.g. `− 3 both sides` |
| Changed term | §8a `emphasis` on that term only, in the step where it changes |
| Substitution | The substituted value in concept violet, in both the source and the target |
| Balance model | Two pans (§17h), tiles or counters per term, removed in pairs |
| Solution | Final row boxed: 2px accent, radius 12, accent `tint` |
| Check | An optional final row, `muted`, headed `Check` |

**Never more than the band's step ceiling** (§2.6) on one board. A seven-line solve on a Middle board is two boards.

---
