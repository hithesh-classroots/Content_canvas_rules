<!-- Content Canvas Rules — v1.0 — 17 August 2026 — part file 4 of 13 -->

> **PART 3 — DATA, MATHS & DIAGRAMS**
> 
> | | |
> |---|---|
> | **Owner** | Content Canvas — **feeds** |
> | **Domain** | Making Stills from Assets (10) |
> | **Governs** | Charts, geometry, figures, lattices, graph sheets, number lines, Venn and set diagrams, transformations. |
> | **Loaded when** | A board carries a figure, chart, graph or diagram. |
> | **Requires** | `00-contract.md` + `01-foundations.md` + `12-rules.md` |
> | **Version** | v1.0 — 17 August 2026 |

> **What this file does not decide.** Type steps, colours, radii, shadows, spacing, the layout
> contract, motion and state values are defined in `01-foundations.md` and cited here by `§`
> number. If a value you need is not in this file, it is there — do not infer it. `§` refers to
> sections (numbered 0–45); `R` refers to rules (numbered 1–120) in `12-rules.md`. Both numbering spaces are
> permanent: numbers are added, never reassigned.

---
# PART 3 — DATA, MATHS & DIAGRAMS

## 15. Charts

| Type | Use | Notes |
|---|---|---|
| Bar | Compare discrete values | Radius 8 top only, min width 24, gap = ½ bar |
| Column stack | Parts of a whole over categories | Max 3 segments |
| Line | Change over a continuum | 2.5px, points 8px, no area fill unless area is the point |
| Area | Accumulation | Accent at 15% alpha under a 2.5px line |
| Scatter | Correlation | Points 8px, 2px white ring |
| Pie / donut | One proportion, ≤3 slices | Donut preferred; label directly |
| Pictograph | Counts for younger students | One glyph = one unit, ≤10 glyphs |
| Number line | Position, intervals, negatives | Full width, ticks, marked points |
| Histogram | Distribution | No gap between bars |

Rules: **max 2 series** (concept violet, then action blue) · value labels 16/700 *above* the mark, never inside · no gridlines behind bars · no legend for a single series — label it directly · axes start at zero for bars · one chart per board.

## 15a. The chart set

§15 covers bar, line and scatter. The data cluster also needs these, and each was being drawn differently per author:

| Chart | Spec |
|---|---|
| **Double bar** | Two series only, `gap-inner` between the pair, `gap-row` between categories. Legend above right, swatch 12 units |
| **Pictogram** | One icon = one key value; the key is **mandatory** and sits above the plot. Partial icons clip **vertically from the left**, never scale. Max 10 icons per row |
| **Pie / sector** | Max **6** sectors; below 5% merge into `Other`. Labels outside with 1px leader lines, never rotated. Start at 12 o'clock, largest first, clockwise |
| **Line plot (dot plot)** | Stacked 12-unit dots over a number line (§17a), 4-unit gaps, no connecting line |
| **Frequency table** | §12, with a `Total` row rule 2px `#495057` |
| **Cumulative frequency** | Frequency table plus a running column; the running column is `muted` until it is the point |
| **Box plot** | Box 56 tall 2px accent, median 2.5px `#212529`, whiskers 1.5px with 24-unit caps, outliers 8-unit circles |
| **Histogram** | Bars touching — the absence of a gap is the meaning. Equal class widths, axis labelled with boundaries |

- **The scale starts at zero** on any chart with a bar or an area. A truncated axis on a teaching board misrepresents the data — §36.5 Tier A.
- **Never a 3D chart, never an exploded pie, never a shadow behind a bar.**
- A chart with one series carries no legend — label it directly.

## 16. Geometry

| Element | Spec |
|---|---|
| Shape outline | 2.5px accent, `stroke-linejoin:round` |
| Shape fill | The accent's tint, opaque |
| Ghost / original | 1.5px `#ced4da`, dash `6 4`, no fill |
| Vertex (static) | none |
| Vertex (draggable) | 10px circle, `#fff`, 2.5px accent border, `resting` shadow |
| Side label | 24/800 accent, 12px outside the edge |
| Right angle | 10px square, 1.5px `#adb5bd` |
| Angle arc | 1.5px accent, r=24, label 16/700 at the midpoint |
| Congruence tick | 1.5px, 8px, `#adb5bd` |
| Parallel arrow | 2.5px accent chevron at the edge midpoint |
| Dimension line | 1px `#868e96`, 6px end caps, label 16/700 centred |
| Area shading | Accent tint, or 45° hatch 1px at 6px pitch |

## 16a. Arrows & connectors

Nothing governed these, so arrowhead size, stroke weight and count varied per author — including triple stacked chevrons at three opacities to mean "continues".

| Part | Spec |
|---|---|
| Shaft | Matches the line it belongs to — axis 2px `#adb5bd`, connector 1.5px `#adb5bd`, emphasis 2.5px accent |
| Head | Filled triangle, **length 3× the stroke width**, half-width 2×. One head unless the relation is genuinely bidirectional |
| Curvature | Straight, or a single arc of constant radius. Never an S-curve, never a hand-drawn path |
| Colour | The connector inherits the colour of what it connects. If the two ends differ, it is `#adb5bd` |
| Label | Sits on the shaft midpoint, `label` step, on an opaque chip if it crosses anything |

**Continuation ("the line goes on forever")** is one arrowhead plus the axis extending into the board's fade — **never a train of ghosted chevrons**. Repeating an arrowhead at decreasing opacity reads as three arrows, and it puts information below the `muted` floor (§3.6).

**A connector must connect.** If it does not join two identified things, it is decoration and is deleted.

## 16b. Congruence, equality and construction marking

The notation of the entire congruence/similarity cluster — SSS, SAS, ASA, AAS, HL, similar triangles, special parallelograms, symmetry. Without it, "these two sides are equal" has to be said in words on every board.

| Mark | Spec | Means |
|---|---|---|
| Side ticks | 1, 2 or 3 short 2px strokes across the side's midpoint, 10 units long, perpendicular | Sides with the same count are equal |
| Angle arcs | 1, 2 or 3 concentric 2px arcs at radius 18/24/30 inside the vertex | Angles with the same count are equal |
| Right angle | A 12-unit square at the vertex, 2px, **never an arc** | 90° |
| Parallel marks | 1 or 2 chevrons mid-side, pointing along the line | Sides with the same count are parallel |
| Equal arcs | Ticks across the arc, same rule as sides | Equal arc length |

- **Marks are ink `#495057` by default**, not an accent. They are notation, not emphasis. A mark takes an accent only when that pair *is* the board's current point (§8a `emphasis`).
- **Never reuse a count across different meanings on one board.** If single ticks mean one equal pair, a second pair takes double ticks — not a different colour.
- **Correspondence order is stated in the text**, not implied: `△ABC ≅ △DEF` with vertices drawn in matching positions.
- **Construction and auxiliary lines** are 1.5px `#adb5bd` dashed `6 4` (§5) and always sit *under* the figure.
- **Dimension lines** (for perimeter, area, volume labels): 1.5px `#868e96` with 6-unit end caps, label on the line in `label`/700, offset 14 units clear of the shape.
- **Hatching** for a region under discussion: 45°, 1px accent at `tint` pitch 6 — or a flat `tint` fill. Never both.

## 16c. Solids — the technical isometric exemption

§31 bans 3D, gradients and highlights. Around forty modules are solid geometry — nets, prisms, pyramids, cylinders, cones, spheres, frusta, Euler's formula, front/side/top views, volume and surface area. **They need a legal way to be drawn, and this is it.** It is an exemption for *diagrams of solids only*; decorative illustration stays flat (§30).

| Part | Spec |
|---|---|
| Projection | **Isometric**, 30° axes. Never perspective, never a vanishing point |
| Faces | **Three flat tones, no gradient**: top `#f1f3f5`, left `#dee2e6`, right `#ced4da`. Accent solids use that accent at 0.16 / 0.10 / 0.06 |
| Edges | Visible 2px `#495057`; **hidden 1.5px `#adb5bd` dashed `6 4`** — hidden edges are shown, always, or the solid is unreadable |
| Curved solids | Two silhouette lines plus a 1.5px ellipse at each end; the far half of the ellipse is dashed |
| Vertex | 6px `#495057` dot, label `label`/700 placed outward from the body |
| Face label | Centred on the face, `label`/700, ink — never rotated to "sit on" the face |
| Cutaway / section | 45° hatch 1px accent, pitch 6 |

**Still banned inside a solid:** rim highlights, inner glow, drop shadow, reflection, texture, a light source that is not top-left.

**Nets** unfold with the base fixed, folds as 1.5px `#adb5bd` dashed, cut edges 2px `#495057` solid, and each face carrying the same label it has on the assembled solid — the label is what makes the net readable as *that* solid.

## 16d. The figure system

**`Shape System.dc.html` is a different thing** — it holds surfaces and buttons (§20.0). This section is about *figures*: every 2D and 3D figure in the library is built the same way: **a vertex set, an edge set, a face set.** Not a drawn path — a described object. That is what makes a shape re-labellable, re-colourable, state-switchable and checkable.

### 16d.1 Vertices

| Part | Spec |
|---|---|
| Position | **Snapped to the lattice** (§16e). A vertex at a non-lattice point is a drawing, not a figure |
| Dot | 6px, the edge's stroke colour. Drawn only when the vertex is named, counted or dragged |
| Label | `label`/700, placed **outward along the exterior angle bisector**, 14 units clear |
| Naming | Capitals, anticlockwise from the lower-left. Images take primes (§17c) |
| Draggable | 12px hit dot, 44px hit area, `attention` on first appearance only |

### 16d.2 Edge variants

Six, and the dash pattern is what distinguishes them — never the colour alone:

| Variant | Stroke | Dash | Means |
|---|---|---|---|
| `edge-subject` | 2.5px `base` accent | — | The figure under discussion |
| `edge-ink` | 2px `#495057` | — | A figure present but not the subject |
| `edge-emphasis` | 3px `base` accent | — | **One** edge being measured or named right now |
| `edge-hidden` | 1.5px `#adb5bd` | `6 4` | Behind a solid (§16c) — always drawn |
| `edge-construction` | 1.5px `#adb5bd` | `2 6` | Auxiliary line, mirror line, axis of symmetry, altitude |
| `edge-ghost` | 1.5px `#ced4da` | `4 4` | A previous position or a pre-image |

**Three distinct dash patterns, three distinct meanings.** `6 4` is hidden, `2 6` is construction, `4 4` is ghost. Reusing one pattern for two meanings is what makes a busy geometry board unreadable.

### 16d.3 Face variants

| Variant | Fill | Use |
|---|---|---|
| `face-none` | transparent | **Default.** Perimeter, angles, classification — anything where the interior is not the point |
| `face-tint` | accent at 0.12 | The region under discussion: area, a counted region |
| `face-solid` | accent at 0.85 | A *quantity* of the whole — shaded fraction parts, filled bars |
| `face-shade` | `#f1f3f5` | Context: a figure that is present, uncoloured, and not the subject |
| `face-hatch` | 45°, 1px accent, pitch 6 | Subtracted, overlapped or double-counted regions |
| `face-muted` | `#f1f3f5` at `muted` | Out of scope (§8a) |

**A face is transparent unless the interior carries meaning.** Filling every shape because a fill is available is how a geometry board becomes a colour chart.

### 16d.4 Shape states

The §8a matrix, expressed for figures — this is the highlighted / dehighlighted set:

| State | Edge | Face | Labels |
|---|---|---|---|
| **Highlighted** (`emphasis`) | `edge-subject` 2.5px accent | `face-tint` | Full, in the accent's `deep` stop |
| **Default** | `edge-ink` | `face-none` | Full, ink |
| **Shade only** | 2px `#ced4da` | `face-shade` | Hidden — the shape is scenery |
| **Dehighlighted** (`muted`) | 1.5px `#ced4da` | none | `#adb5bd` |
| **Excluded** | 1.5px `#e9ecef` | none | Removed |
| **Ghost** | `edge-ghost` | none | Primed, `muted` |
| **Selected** | 2px accent | accent 0.12 | Full |

- **State changes stroke and fill only** — never the vertex positions, never the size (§8a.2). A figure that grows when highlighted moves everything around it.
- **One highlighted figure per board** (§0.6). If two figures are compared, the comparison itself is the subject: both take `edge-subject`, and the *difference* between them takes `edge-emphasis`.
- A dehighlighted figure keeps its shape and loses its colour — it never blurs, shrinks or fades below `muted`.

## 16e. Grids & lattices

A shape is only re-drawable if its vertices sit on a defined lattice.

### 16e.1 The 2D lattice

| Part | Spec |
|---|---|
| Authoring space | An SVG `viewBox` in **lattice units**, not pixels — so the figure scales with the board and never carries pixel sizes inward |
| Pitch | 20 units, the working unit for every vertex |
| Minor line | 1px `#e9ecef` |
| Major line | Every 5th, 1px `#dee2e6` |
| Axis | 2px `#adb5bd` with arrowheads (§16a) |
| Origin | 6px `#495057` dot, labelled `O` |

**Visible when** the grid is being counted or read from — area by unit squares, coordinates, translations by vector, slope. **Hidden when** it is only construction scaffolding. A visible grid that nobody reads is texture, and it competes with the figure.

Vertices snap to the pitch. A figure needing half-pitch vertices is drawn at half pitch throughout, never mixed.

### 16e.2 The isometric lattice

| Part | Spec |
|---|---|
| Axes | 30° / 150° / vertical |
| Cell | 20-unit edge — the unit cube |
| Lines | 1px `#e9ecef`, all three directions when visible |
| Face tones | Top `#f1f3f5` · left `#dee2e6` · right `#ced4da` (§16c) |

**One light source, from the top-left, for every solid on every board.** Two solids lit differently on one board is the fastest way to make a page look assembled by two people.

Use for unit cubes, volume by counting, nets, prisms, spatial visualisation and front/side/top views — where the third dimension must be counted. **Not** for a solid whose shape alone is the point; a 2D silhouette with a labelled dimension is clearer.

### 16e.3 Dot lattice

For pattern work, arrays, polygon construction and geoboard tasks: 4px `#dee2e6` dots at 20-unit pitch, no lines. Reads as guidance rather than as a chart, so it never competes with the figure drawn on it.

## 17. The graph sheet

**Reference implementation: `Graph System.dc.html`. It measures its own contrast at render time across every hue; trust it over any number written here.**

### 17.0 Three tiers, deliberately far apart

Grid, axes and plot must never be mistaken for one another. **The grid recedes, the axes hold, the plot leads** — narrow those gaps and a graph becomes a decorated page rather than a diagram.

| Tier | Spec | Reasoning |
|---|---|---|
| Minor grid | 1px `#f0f2f7`, every unit | A ruler, not content. If you notice it before the data, it is too strong |
| Major grid | 1px `#e4e8f0`, every 5th | Orientation only |
| Axes | **2px `#495057`**, arrowheads at all four ends | The frame of reference is never implied |
| Ticks | 1.5px `#adb5bd`, every unit — **3px long when numbered, 5px when not** | A tick is a locator; with a number beside it, it only has to mark *where* |
| Plot | 2.5px in the anchor's `base` | The only saturated thing on the sheet, which is why it leads |

**The origin is a drawn dot** (3px ink), because it is a coordinate like any other. Its **`0` has one permanent home**: left of the y-axis and below the x-axis, clear of both — never centred on the axis line, and never in the y-tick column where the `−1` label collides with it.

**The first unit below the x-axis is reserved for tick labels. Nothing is plotted there.** Moving the labels cannot fix a collision in that band — a marker at `y = −1` spans it whichever side the label sits.

### 17.1 The two sheets

| Sheet | Use when |
|---|---|
| **Labelled** | A value must be read off the plane. Tick numbers, the origin's `0`, named objects |
| **Unlabelled** | The *shape* is the lesson — symmetry, slope, direction, growth |

**Both name their axes.** Dropping the numbers never means dropping `x` and `y`.

### 17.2 The five plottables

The drawn form carries the maths, so form and meaning are locked together:

| # | Kind | Form |
|---|---|---|
| 1 | Point | 4.5px filled dot with a 2px white ring |
| 2 | Line | Runs to both edges, **arrowhead at each end** |
| 3 | Segment | **Endpoint dots, no arrowheads** |
| 4 | 2D shape | Stroked boundary, **10% fill**, vertices marked |
| 5 | 3D shape | Isometric (§16c) — three flat tones, one top-left light source, **opaque** faces |

**Arrowheads continue; endpoint dots stop.** That single distinction separates a line from a segment, and it is the maths — never draw one with the other's ending.

**A point is small.** It marks a *coordinate*, so precise beats prominent — 4.5px, never scaled up to draw attention.

**A ring separates, and a vertex must not be separated.** A standalone point takes a white ring so it reads over gridlines. An **endpoint or a vertex takes none** — it belongs to the line it terminates, and a ring cuts a gap so the segment appears to stop short of itself.

**A fill is 10%** so gridlines still count *through* the shape, because the count is usually the point.

**A solid sits wholly inside one quadrant**, clear of the tick row — otherwise it occludes the axis it is measured against. Derive its anchor from its own projected extent; a hardcoded anchor drifts the moment the sheet is rescaled.

### 17.3 The three states

| State | Treatment |
|---|---|
| Default | 2.5px stroke, 10% fill, 4.5px dots |
| Disabled | 1.5px `#ced4da`, no fill, 3.5px dots, labels `#9aa0a6`. **Keeps its position** — it is still true |
| Highlighted | 3.5px stroke, 18% fill, a soft halo behind linework, and a **two-ring ripple behind a point** |

**State never moves *or resizes* a point.** A bigger dot covers more of the plane and quietly changes what the point says, so a highlighted point keeps its exact size and gains a ripple behind it instead.

**A highlighted object gets a halo, not a different colour** — its identity has to survive the emphasis. One highlighted object per sheet.

**Labels sit clear of what they name** — never on a dot, never across a line, never inside the axis-furniture band.

## 17a. Number line

**Reference implementation: `Number Line System.dc.html`. It measures its own contrast at render time across every hue; trust it over any number written here.**

A number line adds **no new devices** — it is the graph sheet’s axis on its own with the grid removed: the same 2px ink, the same arrowhead construction (§16a), the same generated hue (§3.7) for anything marked.

### 17a.1 The two sets

**The ends declare the set**, drawn and never captioned — it is the first thing a student reads.

| Set | Ends |
|---|---|
| **Whole numbers** | A 3px square cap at zero, one arrowhead right. The cap *is* the rule: nothing exists left of zero in this set |
| **Integers** | An arrowhead at each end. The line continues forever both ways, and the heads say so |

**Stacked lines on one board share the same unit width**, or the comparison between them is a lie. That is the whole point of an “extending the number system” board, so both sets are laid out on the same span.

### 17a.2 The line

| Part | Spec |
|---|---|
| Axis | 2px `#495057`, running **into** the arrowhead’s base — never stopping short of it |
| Tick | 1.5px `#adb5bd`, **5 units either side** |
| Zero | 2.5px ink tick, label 800 — the only emphasised tick by default |
| Tick label | 12/700 `#6b6390` **below** the line, `tabular-nums` |
| Spacing | Equal, always. A broken or compressed scale never appears on a teaching line — the spacing *is* the quantity |
| Range | Symmetric about the region being taught; never more than 17 ticks |

**Every number prints its minus as `−` (U+2212), never a hyphen** (§13.2). `String(-3)` emits U+002D, so a tick label and a marked value 50px apart will silently disagree — route every number through one formatter.

**Only the marks take a hue.** Axis, ticks and numbers stay ink at every angle. That is why a line reads identically whichever hue it counts in, and why two lines in different hues can share one board.

**Tick labels are never colour-coded by sign** (§3.3).

### 17a.3 The two marks

| Mark | Form |
|---|---|
| **Point** | 5px filled dot with a 2px white ring |
| **Region** | A 6px accent rule along the axis plus a band behind it, with endpoint markers |

**Filled means in, hollow means out.** A region’s endpoints carry interval notation — the one place in this system an unfilled marker is legal, and it is maths, so it is never restyled for looks.

**A point wears a ring; an endpoint does not.** A point sits *on* the axis and the ring lifts it clear; an endpoint belongs to the band it terminates, so a ring would cut a gap in it (§17.2).

**Labels go above, ticks below** — two permanent rows, so a marked value and its tick number can never be confused.

**Direction chips** (“Negative integers”) are chips per §14 below the axis, aligned to the region they name — never solid blocks in a hue chosen for sign.

### 17a.4 The three states

| State | Treatment |
|---|---|
| Default | 5px dot, **5% band**, 6px rule |
| Disabled | `#ced4da`, 3.5px dot, **no band** — and it keeps its position, because it is still true |
| Highlighted | Ripple behind the point, **26% band**, 9px rule |

**A default band only has to show the region exists; a highlighted one has to single it out.** At 10% against 20% the highlight read as the same region slightly warmer — hence 5% and 26%.

**State never moves or resizes a mark.** A point highlights with a ripple behind it, a region by deepening its band. A mark that shifts when emphasised has changed the value it names.

**Disabled keeps the value legible.** The achromatic stroke, smaller dot and absent band carry the signal — a marked value is the *value*, not the control (§20.0.2).

**One highlighted mark per line.** Two is none.

## 17b. Set & Venn diagrams

**Reference implementation: `Venn & Set System.dc.html`. It measures its own contrast at render time across every hue; trust it over any number written here.**

A set diagram adds **no new devices** — regions are figures (§16d), and the two things that can be marked are the same pair the number line uses (§17a): a **region** and a **member**.

### 17b.1 The three relations

Given two sets, either one contains the other, or they share some members, or they share none. **There is no fourth case** — the set of diagrams is closed by the mathematics, not by preference.

| Relation | Drawn as | Because |
|---|---|---|
| **Nested** (A ⊂ B) | Rounded rectangles, one inside the next | Every label needs a flat band of its own, and the ring between two concentric circles gives none |
| **Overlapping** (A ∩ B ≠ ∅) | Two circles | The lens is the subject, and only a curve reads as a region belonging to both |
| **Disjoint** (A ∩ B = ∅) | Two circles apart | The gap *is* the claim, so nothing is drawn between them |

The relation is drawn, never captioned. Nesting stops at **four levels** — past four the innermost band is too thin to hold a label, and the stack splits across two boards.

### 17b.2 Anatomy

| Part | Spec |
|---|---|
| Boundary | **2px** in the set's hue at `base`. Always stroked — a set without an edge cannot be pointed at |
| Fill | **Opaque**, painted over its parent. Outermost `oklch(90% .075 h)` → innermost `oklch(96% .03 h)` |
| Label | The hue's `deep` stop (`oklch(32% .10 h)`) at the `body` step, weight 700 |
| Label position | In its own band — never over a nested child, never over a member, never rotated to follow a curve |
| Members | Ink `#212529`, weight 700, at full opacity **in every state** |

Four rules the anatomy depends on:

1. **Fills repaint, never stack.** Every region is opaque. Three translucent regions produce a fourth and fifth colour that mean nothing, and leave the innermost set darkest — implying the most-nested set matters most, which is the opposite of the mathematics. *An alpha fill cannot satisfy this: alpha stacks by definition.*
2. **Depth decreases inward.** Outermost deepest, innermost lightest, six lightness points across the whole stack. Enough to read the nesting, not enough for any level to dominate — and it keeps the smallest region the most legible.
3. **Labels sit in top bands, members in bottom bands.** Each ring gets a strip at its top for the name and one at its bottom for what that ring adds, so a student reads down the diagram and gets the sets in order.
4. **Only regions take the hue.** Members, and the ink they are set in, stay neutral at every angle — which is why two diagrams in different hues can share a board.

### 17b.3 Hue

One hue angle generates every value (§3.7). **Overlapping and disjoint sets share a single hue**, and the lens is that hue one step deeper (`oklch(88% .085 h)`) — a lens cannot wear two hues at once without inventing a third meaning.

**Per-set hues are for nested diagrams only**, where regions never overlap: maximum four, and only when those sets are anchored individually elsewhere in the module. Otherwise one hue for the whole diagram.

**Set anchors are module-level, not board-level.** If "Natural numbers" is violet on board 3 it is violet on board 12, in its label, its boundary and its fill (§34, §43.2). A set that changes colour between boards has taught the student that colour means nothing.

### 17b.4 The three states

| | Boundary | Fill | Label | Members |
|---|---|---|---|---|
| **Default** | 2px `base` | as above | `deep`, 700 | ink |
| **Disabled** | 2px `#ced4da` — the set is still a set | none | `#868e96` | **ink, unchanged** |
| **Highlighted** | 3px `base` | `oklch(82% .13 h)` | `deep`, 800 | ink |

- **A region highlights by deepening; a member highlights by rippling** — two discs behind it in the set's own hue at 10% and 16%. Neither moves, resizes or changes shape. A region that grows changes what it claims to contain; a member that grows looks like a different value.
- **One highlight per diagram**: one region and one member at most. Two highlighted regions is a comparison, and a comparison has to be stated in words as well.
- **Disabled removes colour, not legibility.** Members are the value; the region around them is the annotation. Same line as the disabled slider (§18.3), the disabled counter (§18a.3) and the disabled number line (§17a.4).

## 17c. Transformations — pre-image and image

Dilation, reflection, rotation, translation, series of transformations, similarity. One convention, or a student cannot tell which figure is the answer.

| Part | Spec |
|---|---|
| Pre-image | 2px `#adb5bd`, no fill, vertices `A B C` |
| Image | 2.5px accent, accent at `tint` fill, vertices `A′ B′ C′` (prime, U+2032) |
| Mapping | One 1.5px `#adb5bd` dashed arrow per corresponding vertex, or **one** arrow for the whole figure — never a mix |
| Mirror line | 1.5px `#adb5bd` dash `6 4`, labelled at its end |
| Centre of rotation / dilation | 8px `#495057` dot, labelled, always drawn |
| Rotation | A single arc arrow at the centre carrying the angle and direction |
| Scale factor | On the board as `k = 2`, and in a `label` on one mapping arrow |
| Series | Each stage keeps its own prime count — `A′`, `A″`. Intermediate stages take §8a `muted` |

**The pre-image never disappears.** A transformation board that shows only the result has removed the thing being taught.

---
