<!-- Content Canvas Rules — v1.0 — 17 August 2026 — part file 13 of 13 -->

> **PART 11 — THE RULES**
> 
> | | |
> |---|---|
> | **Owner** | Content Canvas — **owns outright** |
> | **Domain** | Canvas & Surface Design (8) |
> | **Governs** | The 120 checkable rules, cited `R1`–`R120`. |
> | **Loaded when** | Never. Always loaded alongside the contract. |
> | **Requires** | `00-contract.md` + `01-foundations.md` + `12-rules.md` |
> | **Version** | v1.0 — 17 August 2026 |

> **What this file does not decide.** Type steps, colours, radii, shadows, spacing, the layout
> contract, motion and state values are defined in `01-foundations.md` and cited here by `§`
> number. If a value you need is not in this file, it is there — do not infer it. `§` refers to
> sections (numbered 0–45); `R` refers to rules (numbered 1–120) in `12-rules.md`. Both numbering spaces are
> permanent: numbers are added, never reassigned.

---
# PART 11 — THE RULES

**Cite these as `R1`–`R120`, never with `§`.** Rules live in their own numbering space; `§` refers
only to sections (`§0`–`§45`). Both spaces are permanent: numbers may be added, never reassigned.

1. **Boards are transparent.** No board-level fill, tint or gradient. Surfaces are small, local and opaque.
2. **Roboto, pinned and self-hosted** — italic serif (Times New Roman) only on lowercase algebraic variables, and never on numerals, operators, function names, units or vertex labels (§2.0).
3. **Four sizes: 48 / 36 / 24 / 16** (+ `figure` 44 and `micro` 12 for data). Content is 24; under 24 is a label, never a sentence. A narrated sentence is `statement` 36/500, never 36/800.
4. **Three weights by category:** 800 destination · 700 control · 500 content. **One 800 element per board.**
5. **Colour by procedure (§3.2):** state → subject → type step. A title is never fully accented; an accent never spans a sentence.
6. **One accent per board**, from the semantic table. One token per role.
7. **Three inks.** `#868e96` never carries information needed to answer.
8. **One border: 1px `#e9ecef`.** 2px means selected.
9. **Four radii: 8 / 12 / 16 / 999.**
10. **Two shadows.** Glows belong to primary buttons; media gets none.
11. **One primary button per board.** Hint is always secondary.
12. **`gap`, never margin.** 8 / 14 / 20 / 26 / 40. Padding `24px 34px 20px`, or 44px top with a chip.
13. **Media: fixed box, `object-fit:cover`, no border, no shadow, capped height.**
14. **One visual per board** — media and diagrams never share.
15. **Every board declares a kind and a layout.**
16. **Max 5 list rows** (objectives 3–4), **2 chart series, 5×6 table.**
17. **Colour is never the only signal.**
18. **Minimum hit target 44px**; no hover-only affordances.
19. **Motion is one-shot** and dies under `prefers-reduced-motion`.
20. **A board never scrolls.** If it does, cut content — never shrink type.
21. **No dark boards, no white ink, no warm yellow ink.**
22. **Illustration, diagram and photo are different things** (§30). If a student could measure it, it is a diagram — semantic accents and real geometry only.
23. **Flat vector only:** primitives, two stops per shape, no gradients, no shadows, no highlights, light from the top-left.
24. **Extended hues are decorative** (§32). Max 4 per illustration, dominant = the board's accent, and never `correct` green or `wrong` red for decoration.
25. **Read the whole module before designing any board.** Produce a colour ledger, a visual-model ledger and a per-slide layout verdict first (§33).
26. **Source colours are semantic commitments.** Build the anchor ledger, cap it at three referents, and a term keeps its colour everywhere — the ledger outranks any per-board choice (§34).
25a. **Rank referents before colouring them** (§34.1–34.2): the term the module exists to teach is **primary** concept violet; the term it is defined against is **secondary** emphasis orange; results are **tertiary** action blue. The module title's key noun must be the primary accent.
25b. **A word naming a referent wears that referent's anchor**, not the board's default accent — the word "exponent" and the symbol `n` must be the same colour (§34.6).
26. **Keep the source layout unless it fails hierarchy, readability or information architecture** — and name the failure (§35).
27. **Every content board earns a graphic.** Max 2 sentences, 4 rows, ~40 words, 1 visual. Over budget means split the board (§36.1).
28. **One visual model per module**, introduced once and extended — never a new metaphor per slide (§36.2).
29. **Never show the symbolic rung before the concrete one has appeared** (§36.3).
29a. **A manipulative's grammar must match its operation** — additive is a strip, multiplicative is nesting/branching/area (§36.5). Count the drawn factors against the written expression before shipping the board.
29b. **One declared unit = one drawn size**, on every stage and every board. Ink must track quantity, or the visual reverses the lesson (§36.5).
29c. **A visual may not depict a misconception a later board corrects** (§36.5).
29d. **Every "?" must be answerable from what is drawn**, and every claimed bridge must be shown, not asserted (§36.5).
30. **An embedded applet is part of the canvas.** Every rule applies; §23 says which are non-negotiable.
31. **Never silently rewrite an applet's CSS.** Fix Tier A and notify; request consent for Tier B; override rather than fork.
32. **Applets consume the token bridge**, never hardcoded values.
33. **Every applet bundle loads with a version query** — without it, fixes appear to fail.
34. **Size states role, not enthusiasm** (§2.1a): the board's destination takes the larger step, a recap of prior knowledge takes `body`, and reference material is a caption. Never emphasise a non-anchored term with weight — it stays plain (§2.2).
35. **A measure cap is symmetric `padding-inline`, never `max-width`** (§7.4). On a stretched block, `max-width` moves the block's centre off the board's centre.
36. **Every direct text child of a board's centred column carries `align-self:stretch`** (§7.5a) — shrink-to-fit blocks wrap narrow, keep a one-line box height, and the next sibling paints over line 2. Equations carry `white-space:nowrap`; compared rows stretch to one shared width; decorative overhang stays unclipped.
37. **The shell owns navigation only** (§44a) — nothing the host already draws. A fit routine never measures an element it sizes, and its `ResizeObserver` coalesces through one `requestAnimationFrame`.

**State, and the components that carry it:**

37a. **Ten states, one treatment each, on every element class** (§8a). One state per element at a time; `emphasis` is the only one that may use colour; `complete` is a tick, never a green fill; no state changes an element's size or position.
37b. **Five opacity steps** (§3.6). Below `muted` (0.55) an element is decorative and may not carry information a student needs. Fades are achromatic.
37c. **One glow exists** (§8a.3): `attention` — one per board, two pulses, never colour-coded, never meaning state. Every other glow, bevel, gradient and text shadow is stripped (§8a.5).
37d. **Sign is never colour-coded with state colours** (§3.3) — red negatives teach a student that every negative number is wrong.
37e. **A choice button is content, not an action** (§20.0a): every option looks identical at rest, and selection is a border plus a tint, never a fill.
37f. **Every state of an answer box is specified** (§19a) — and a wrong answer keeps the student's value, with no shake, flash or pulse.
37g. **A set keeps one colour across the whole module** (§17b); boundaries are always stroked, and nested fills repaint rather than stack.
37h. **One glyph per operator** (§13.2) — `− × ÷ ≤ ≥ ≠ …`. A fraction bar is ink, never its own hue (§13.1).

**How this document is kept true:**

110. **One fact, one section, one number.** A section number is unique across the whole document. When a component gets a dedicated section, every earlier row describing it is **deleted**, not left beside its replacement — a superseded spec that stays in the file is indistinguishable from a current one.
111. **A component section names its reference implementation, in one wording** — *"it measures its own contrast at render time across every hue; trust it over any number written here."* The file is the source of truth; this document is its description, and a description drifts.
112. **A carve-out is stated where the general rule is stated** (§20.0's circular slider thumb), never left as a silent contradiction in a distant table.

**The gate:**

113. **Nothing ships unchecked** (§0.7). Twelve checks per board, groups A and B blocking. A rule nothing evaluates is a preference.
114. **Nothing overlaps** (§7a.1), and board-level layout is flex or grid — absolute positioning belongs inside a computed coordinate space, never on a board.
115. **A board is at least half full and no fuller than its band allows** (§7a.2, §2.6) — except `divider` (≤40%), `feedback` (≤50%), `intro` and `section` (≤60%), because a spare board is what makes the boards around it feel dense. **A ceiling is per kind, not per group.** Under the floor a content board is under-explained, mergeable, or claimless — and the fix is never to scale content up.

**Curriculum coverage (K–10):**

46. **Every board declares a grade band** (§2.6). The band sets minimum type, word count, element count and step count — a Grade 1 board at Senior density is a Tier A failure.
47. **Solids are drawn in technical isometric** (§16c) — three flat tones, hidden edges dashed, no gradient or highlight. This is the *only* exemption to §31's flat-vector rule, and it covers diagrams of solids, never illustration.
48. **Congruence is marked, not narrated** (§16b): ticks for equal sides, arcs for equal angles, a square for the right angle, chevrons for parallel — in ink, never in accent unless that pair is the current point.
49. **A transformation always shows its pre-image** (§17c), image primed, centre and mirror line drawn.
50. **Pick a model from Part 3B**, and draw it the way that entry specifies, every time. A model not in the library is a new entry, written before it is used.
51. **Column arithmetic is aligned by place** (§17i) with `tabular-nums`; carries and borrows are annotations in emphasis orange, never a recoloured whole sum.
52. **Equation working aligns every `=`** (§17j), one operation per row, the changed term emphasised in the row where it changes.
53. **A fraction's whole is one size across the whole module** (§17e), and partitions are geometrically equal.
54. **A chart's scale starts at zero**, a pictogram always carries its key, and a pie never exceeds 6 sectors (§15a).
55. **Practice consolidates, challenge extends, recall checks** (§44b) — none of the three introduces new notation, and a word problem's every quantity is either lifted out or marked in the stem.
56. **The module id is the identity; the title is a label** (§43.4). Normalise, fingerprint and resolve duplicates before any pass.
57. **Reveal order is frame → given → one step at a time → result** (§8b), 120ms apart, and **nothing already revealed moves when the next thing appears.**
58. **Every diagram carries a one-sentence description** of what it shows (§9.5). A diagram-only board without one is Tier A.
59. **A figure is drawn to its stated measurements**, or it is labelled `Not to scale` (§9.6).
60. **A second model is allowed to contrast or to bridge — never for variety** (§36.2). A bridge shows the same quantity, at the same whole size, with the equality written between.
61. **An option set must not leak its answer** (§20.2): equal-length options, uniform correct position, parallel form, misconception-bearing distractors.
62. **Loading and failure are designed states** (§8c), and a failed applet never blocks the module.

**Shape, colour and highlight:**

63. **Every board has exactly one focal point** (§0.6), traceable to a key takeaway. If nothing on a board deserves the accent, **the board has no claim — cut it, never paint it.**
64. **A module declares 3–5 key takeaways before board 1** (§34a.1). Every board maps to one; a board mapping to none is filler.
65. **The highlight is the shortest span carrying the delta** (§34a.2) — what was not already true before this board. Never the topic word, never a connective, never a term already highlighted.
66. **A term is highlighted twice per module** — introduction and recap (§34a.4). Highlighting works only while it is scarce.
67. **A fill and its stroke are two stops apart** (§3.7), and text on a fill takes that fill's `deep` stop — never ink black, never white.
68. **One colour scheme per board, from the five** (§3.8): anchor triad, monochrome depth, complementary opposition, analogous run, triad. 60/30/10, max four hues, and it must survive greyscale.
69. **Never two hues at `base` with equal area**, and adjacent hues only at different stops (§3.8).
70. **A shape is a vertex set, an edge set and a face set** (§16d) — snapped to a lattice (§16e), never a drawn path.
71. **Three dash patterns, three meanings** (§16d.2): `6 4` hidden, `2 6` construction, `4 4` ghost. A face is transparent unless its interior carries meaning.
72. **State changes stroke and fill only** (§16d.4) — never vertex positions, never size. A dehighlighted figure keeps its shape and loses its colour.

**Shapes, surfaces and buttons — the closed set:**

73. **Two families, one shape** (§20.0). A surface is flat and holds content; a button is raised and is pressed. Both are 20px radius and fit to content, so **depth is the family signal**, not radius.
74. **A colour variant is a hue angle** (§3.7) — five stops generated from it at fixed lightness and chroma. A ninth colour is generated, never invented, and it will already match.
75. **Chroma makes a chip visible, not darkness** (§3.7). The canvas is near-neutral, so a surface separates by being coloured. Judge a fill by eye against `#eee9fd`; its luminance ratio is meaningless here.
76. **Two arcs are reserved** (§3.7.2): 15–40° is *wrong*, 130–170° is *correct*. Hues on one board sit ≥25° apart, four maximum.
77. **A surface has no stroke at rest** (§20.0.2). The stroke appears in exactly one state — highlighted — inset so nothing reflows.
78. **The base edge is the affordance** (§20.0.1). A flat solid offset in the face's own hue; pressing travels the face down by exactly its height. No scale, no bounce, no colour flash — and no bevel, which is still banned everywhere else.
79. **The neutral is not white** (§3.7.3). It is the brand angle at near-zero chroma, because it is the most-seen shape in the library.
80. **Every option in a group is identical at rest** (§20.0.4), and correct/wrong appear only after judging — never as a selection.
81. **A generated angle is spot-checked** (§3.7). The lightness constants narrow the contrast band; they do not pin it, because chroma moves luminance.

**Sliders:**

82. **A slider invents nothing** (§18). The track is a surface, the thumb is a button with the same base edge, and every colour is generated from the anchor's hue angle.
83. **The value is shown once** (§18.2) — as labels or as a counter, never both. That single rule closes the set at five types.
84. **Markers cut through the bar** (§18.1), 2px at interior stops only — never a dot resting on the track. They divide the bar into the parts being counted.
85. **The track wears the accent** (§18.1). A grey track with a coloured fill reads as two objects overlapping; one hue family reads as one control.
86. **The counter is tethered** (§18.1) by a tail, fits its digits, and never reserves width it is not using.
87. **The bar leads and the thumb rides it** (§18.1) — track 16px, thumb 40px, hit target 44px regardless of how the thumb is styled.
88. **Highlighted is the surface's highlighted state** (§18.3), and siblings are never dimmed to fake it. One highlighted slider per board.
89. **A disabled slider keeps its value legible** (§18.3). Its control label may dim; its tick labels and counter may not.
90. **Tick labels clear the thumb, not the track** (§18.4) — the base edge reaches 32px below the track top, and the stop it would strike is the active one.

**Counters:**

91. **A counter is two buttons and one surface** (§18a) — same radius, same base edge, same generated hue as everything else.
92. **The value always leads, by hierarchy not volume** (§18a.1): larger, one step darker, lifted. Loud buttons around a plain number are forbidden.
93. **One hue family, no grey** (§18a.1). A button's face is one step lighter than what it sits on; its edge comes from the same hue.
94. **The value is a surface** (§18a.1) — no base edge, because it is read and never pressed. Its lift is elevation, not an affordance.
95. **Glyphs are 4px bars** (§18a.1), not icon strokes — a 1.5px stroke disappears at classroom distance.
96. **A limit disables one button, never the counter** (§18a.4), and the value never resizes as its digits grow.

**Graph sheets:**

97. **Three tiers, far apart** (§17.0): grid barely above the paper, axes in ink with arrowheads, plot in the only saturated colour on the sheet.
98. **Arrowheads continue, endpoint dots stop** (§17.2) — the one distinction that separates a line from a segment, and it is the maths.
99. **A ring separates, and a vertex must not be** (§17.2). A standalone point is ringed; an endpoint or vertex never is, or the stroke shows a gap.
100. **A point is small and never resizes** (§17.2–17.3) — it marks a coordinate, and it highlights with a ripple behind it, not by growing.
101. **The first unit below the x-axis belongs to the tick labels** (§17.0). Nothing is plotted there, and a solid sits wholly inside one quadrant.
102. **Both sheets name their axes** (§17.1) — dropping the numbers never means dropping `x` and `y`.
103. **Disabled keeps its position** (§17.3). It is out of scope, not untrue.

**Number lines:**

104. **The ends declare the set** (§17a.1) — a square cap at zero for whole numbers, arrowheads both ways for integers. Drawn, never captioned.
105. **Stacked lines share one unit width** (§17a.1), or the comparison between them is a lie.
106. **Filled means in, hollow means out** (§17a.3) — interval notation, never restyled for looks.
107. **Only the marks take a hue** (§17a.2). Axis, ticks and numbers stay ink at every angle.
108. **Every number prints `−` (U+2212)** (§17a.2) — `String(-3)` emits a hyphen, and a tick label 50px from a marked value will silently disagree.
109. **A default band is 5%, a highlighted one 26%** (§17a.4) — set closer and the highlight reads as the same region, slightly warmer.

**Normalising existing content (Part 10):**

38. **Conformant means every value traces to a token** (§37.1) — not that the board looks similar. Similar-looking is how the library drifted.
39. **Strip before you snap** (§38.1). If deleting a declaration would not stop a student answering the board, delete it. Converting decoration to its nearest token preserves the noise in a legal palette.
40. **Classify colour by function, then map by role** (§38.2) — never by nearest hue. Nearest-hue matching turns decorative greens into `correct` and mustards into `wrong`. The reserved-colour guard runs on every pass.
41. **Weight is reclassified by category, never snapped from the found value** (§38.3). Sizes round toward legibility and never land below `body`.
42. **An unreachable rule is a rebuild request, not a rule** (§39). Text baked into a raster is Tier A and cannot be styled away; CSS never reaches a canvas — only its token config does.
43. **The pass is read-only until the ledgers exist** (§40), and **idempotent** — a second run produces zero diffs. Every judgement call is recorded and re-read, never re-decided.
44. **Content accuracy, referent ranking, layout verdicts and cutting content are never automated** (§41.2). Everything else can be.
45. **A referent keeps one token across a chapter** (§43.2), and **no module is conformant without a record** (§43.3).
### 43.4 Module identity

The registry is keyed on module identity, so identity has to be clean before a pass can be idempotent. The current library is not:

- Near-duplicate titles differing only in punctuation or spacing (`Bar Diagram. Word Problems` / `Bar Diagram.Word Problems`)
- Exact duplicates (`Growing number patterns` twice, `A Few More Challenges`)
- Trailing whitespace, embedded newlines, stray quote characters
- Typos (`Adition of Unlike Fractions`)
- ASCII substitutes for maths glyphs in titles (§13.3)

Before step 0 of the pass (§40):

1. **Normalise** — trim, collapse internal whitespace, strip quotes and newlines, apply §13.3 to the title.
2. **Fingerprint** — casefold and remove punctuation; identical fingerprints are candidate duplicates.
3. **Resolve** — a human decides merge, rename or keep-both. Never automatic: `Practice: GCF` and `Practice Problems: GCF` may be genuinely different modules.
4. **Assign a stable id** (`G08C01M01`) that never changes again. **The title is a label; the id is the identity.** A registry keyed on titles re-splits every time an author fixes a typo.

Record the original title in the module record so a rename is traceable.
