<!-- Content Canvas Rules — v1.0 — 17 August 2026 — part file 11 of 13 -->

> **PART 9 — LAYOUT LIBRARY**
> 
> | | |
> |---|---|
> | **Owner** | Content Canvas — **owns outright** |
> | **Domain** | Canvas & Surface Design (8) |
> | **Governs** | The named layouts: title, explanation, media, diagram, data, practice, interactive, feedback. |
> | **Loaded when** | A board needs a layout chosen. |
> | **Requires** | `00-contract.md` + `01-foundations.md` + `12-rules.md` |
> | **Version** | v1.0 — 17 August 2026 |

> **What this file does not decide.** Type steps, colours, radii, shadows, spacing, the layout
> contract, motion and state values are defined in `01-foundations.md` and cited here by `§`
> number. If a value you need is not in this file, it is there — do not infer it. `§` refers to
> sections (numbered 0–45); `R` refers to rules (numbered 1–120) in `12-rules.md`. Both numbering spaces are
> permanent: numbers are added, never reassigned.

---
# PART 9 — LAYOUT LIBRARY

**Pick a layout and fill its slots. Never arrange a board from scratch.** A new arrangement means a new entry here first.

Slot vocabulary: `TITLE` `SUB` `BODY` `LIST` `MEDIA[…]` `DIAGRAM` `CHART` `FORMULA` `CONTROL` `ACTION` `CAPTION` `CALLOUT` `BADGE` `MASCOT`

## A. Title & statement

| ID | Name | Grid | Slots |
|---|---|---|---|
`T01` | Title | Centred | MASCOT → TITLE(hero) → SUB |
`T02` | Title + artefact | Centred | MASCOT → TITLE(hero) → SUB → FORMULA\|DIAGRAM |
`T03` | Title over media | Full | MEDIA[bleed] + TITLE(hero) on scrim |
`T04` | Section divider | Centred | CALLOUT → figure numeral → TITLE |
`T05` | Closing | Centred | TITLE → LIST(ticked) → BADGE row → ACTION |
`T06` | Objectives | Centred | TITLE → LIST(numbered ×3) → ACTION(secondary) |
`T07` | Single statement | Centred | TITLE only, ≤12 words |
`T08` | Quote | Centred | MEDIA[circle] → BODY(36/500) → CAPTION |

## B. Explanation & lists

| ID | Name | Grid | Slots |
|---|---|---|---|
`E01` | Title + prose | Centred | TITLE → BODY |
`E02` | Title + list | Centred | TITLE → LIST |
`E03` | Checklist | Centred | TITLE → LIST(check) |
`E04` | Steps horizontal | Thirds | TITLE → 3× (BADGE + BODY) |
`E05` | Steps vertical | Centred | TITLE → LIST(stepped) |
`E06` | Two-column compare | Half | TITLE → 2× card(TITLE + LIST) |
`E07` | Do vs don't | Half | As E06 with correct/wrong tints |
`E08` | Key–value | Centred | TITLE → table(2 col) |
`E09` | Definition + example | Centred | TITLE → tint(definition) → card(example) |
`E10` | Term grid | Quarters | TITLE → 4× (BADGE + label + BODY) |
`E11` | Prose + callout | Major-left | TITLE → BODY ‖ CALLOUT |
`E12` | Table board | Full | TITLE → table |

## C. Media

| ID | Name | Grid | Slots |
|---|---|---|---|
`M01` | Media left | Half | MEDIA[standard] ‖ TITLE + BODY |
`M02` | Media right | Half | TITLE + BODY ‖ MEDIA[standard] |
`M03` | Media + caption | Centred | TITLE → MEDIA[wide] → CAPTION |
`M04` | Media pair | Half | TITLE → 2× MEDIA[standard] + CAPTION |
`M05` | Media trio | Thirds | TITLE → 3× MEDIA[square] + CAPTION |
`M06` | Media quad | Quarters | TITLE → 4× MEDIA[square] |
`M07` | Media grid 2×2 | Half | 4× MEDIA[square] with inset labels |
`M08` | Full bleed | Full | MEDIA[bleed] + CAPTION band |
`M09` | Portrait + text | Major-right | MEDIA[portrait] ‖ TITLE + BODY |
`M10` | Media + list | Major-right | MEDIA[square] ‖ TITLE + LIST |
`M11` | Before / after | Half | 2× MEDIA[standard] with pill labels |
`M12` | Annotated media | Full | MEDIA[wide] + numbered hotspots + legend |

## D. Diagram & maths

| ID | Name | Grid | Slots |
|---|---|---|---|
`D01` | Diagram + legend | Major-left | DIAGRAM ‖ legend keys |
`D02` | Diagram + formula | Half | DIAGRAM ‖ FORMULA + variable legend |
`D03` | Diagram compare | Half | 2× DIAGRAM with pill labels, relation glyph between |
`D04` | Diagram + callouts | Full | DIAGRAM centred + numbered callouts pinned |
`D05` | Formula focus | Centred | TITLE → FORMULA(figure) → CAPTION |
`D06` | Derivation | Centred | TITLE → rows of FORMULA, changed term accented |
`D07` | Number line | Full | TITLE → number line → CAPTION |
`D08` | Coordinate plane | Centred | TITLE → plane + plotted data |
`D09` | Plane + readout | Major-left | plane ‖ value cards |
`D10` | Construction steps | Thirds | TITLE → 3× DIAGRAM showing progressive construction |
`D11` | Shape family | Quarters | TITLE → 4× DIAGRAM + label |
`D12` | Proof two-column | Half | TITLE → statements ‖ reasons table |
`D13` | Column arithmetic | Centred | TITLE → §17i stack → CAPTION |
`D14` | Working + model | Half | §17j step stack ‖ the module's model (Part 3B) |
`D15` | Solid + net | Half | §16c solid ‖ its unfolded net, faces labelled alike |
`D16` | Transformation | Half | pre-image ‖ image, mapping arrows across the gutter (§17c) |
`D17` | Congruence pair | Half | 2× figure with §16b marks + correspondence statement below |
`D18` | Model bridge | Half | 2× model of the SAME quantity + the equality between them (§36.2) |
`D19` | Structure diagram | Centred | TITLE → factor / probability tree (§17g) |
`D20` | Instrument read | Major-left | §17h instrument ‖ TITLE + reading |

## E. Data

| ID | Name | Grid | Slots |
|---|---|---|---|
`G01` | Chart full | Full | TITLE → CHART → CAPTION |
`G02` | Chart + readout | Major-left | CHART ‖ value cards |
`G03` | Chart + prose | Half | CHART ‖ TITLE + BODY |
`G04` | Chart pair | Half | TITLE → 2× CHART with labels |
`G05` | Stat row | Quarters | TITLE → 4× (figure + label) |
`G06` | Pictograph | Full | TITLE → glyph rows + key |
`G07` | Table + chart | Half | frequency table ‖ its chart, same category order both sides |
`G08` | Distribution | Full | TITLE → line plot or box plot over one §17a axis |

## E2. Word problem, practice & challenge (§44b)

| ID | Name | Grid | Slots |
|---|---|---|---|
`W01` | Word problem — model | Half | STEM + given/asked ‖ MODEL |
`W02` | Word problem — working | Half | STEM ‖ §17i/§17j working → boxed answer |
`W03` | Word problem — stacked | Centred | STEM → MODEL → boxed answer + unit |
`P01` | Practice — options | Centred | STEM → option row (§20.0a) → CHECK |
`P02` | Practice — entry | Centred | STEM → answer box + unit (§19a) → CHECK |
`P03` | Practice — on a model | Half | MODEL ‖ STEM + answer box |
`P04` | Practice — drag | Full | STEM → drop zones → token tray |
`C01` | Challenge | Centred | STEM → workspace → HINT + CHECK |
`C02` | Challenge — multi-part | Centred | STEM → (a)(b)(c) rows, each with its own answer box |
`R01` | Recall | Centred | TITLE → prior model at `muted` → one question |

## F. Interactive

| ID | Name | Grid | Slots |
|---|---|---|---|
`I01` | Slider + shape | Centred | TITLE → DIAGRAM → CONTROL(slider) + live value |
`I02` | Slider + chart | Half | CHART ‖ CONTROL + readout |
`I03` | Slider pair | Centred | DIAGRAM → 2× CONTROL, one live value each |
`I04` | MCQ | Centred | TITLE(stem) → LIST(options) → ACTION |
`I05` | MCQ with media | Half | TITLE → 4× MEDIA[square] options → ACTION |
`I06` | Numeric input | Centred | TITLE → CONTROL(input) + unit → ACTION |
`I07` | Match pairs | Half | TITLE → 2 columns of rows + connectors |
`I08` | Sort / order | Centred | TITLE → draggable rows |
`I09` | Drag to bins | Half | TITLE → tokens ‖ 2–3 drop zones |
`I10` | Tap the shape | Full | TITLE → DIAGRAM with tappable regions |
`I11` | Plot the point | Centred | TITLE → plane, tap to place |
`I12` | Build the formula | Centred | TITLE → FORMULA with empty slots + token tray |

## G. Feedback

| ID | Name | Grid | Slots |
|---|---|---|---|
`F01` | Answer reveal | Centred | state band → answer(figure) → BODY → ACTION |
`F02` | Worked solution | Centred | TITLE → LIST(stepped: FORMULA + reason) |
`F03` | Hint reveal | Centred | The origin board with the hint panel expanded |
`F04` | Objective earned | Centred | Ticked LIST + ring pulse + reward badges |
`F05` | Misconception | Centred | wrong band → "why" tint panel → correct path → ACTION |

**60 layouts.** Rules: one visual kind per board · never nest layouts · vary consecutive kinds · sum children against the 285px budget before shipping.

---
