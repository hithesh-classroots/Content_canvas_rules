<!-- Content Canvas Rules — v1.0 — 17 August 2026 — part file 2 of 13 -->

> **PART 1 — FOUNDATIONS**
> 
> | | |
> |---|---|
> | **Owner** | Content Canvas — **owns outright** |
> | **Domain** | Canvas & Surface Design (8) |
> | **Governs** | Type, colour, radius, line, shadow, spacing, layout, motion, states. **The only file that states a literal value** — every other file cites into this one. |
> | **Loaded when** | Never. Always loaded. |
> | **Requires** | `00-contract.md` + `01-foundations.md` + `12-rules.md` |
> | **Version** | v1.0 — 17 August 2026 |

> **What this file does not decide.** Type steps, colours, radii, shadows, spacing, the layout
> contract, motion and state values are defined in `01-foundations.md` and cited here by `§`
> number. If a value you need is not in this file, it is there — do not infer it. `§` refers to
> sections (numbered 0–45); `R` refers to rules (numbered 1–120) in `12-rules.md`. Both numbering spaces are
> permanent: numbers are added, never reassigned.

---
# PART 1 — FOUNDATIONS

## 1. Grid & safe area

| | Units |
|---|---|
| Canvas | 1600 × 900 |
| Safe area | 1456 × 812 (margin 72 sides, 44 top, 44 bottom) |
| Columns | 12, each 96 wide |
| Gutter | 40 |
| Baseline | 8 |

Legal splits — a board uses exactly one:

| Split | Columns | Use |
|---|---|---|
| Full | 12 | Titles, single diagrams, full-width charts |
| Half | 6 / 6 | Visual ↔ text, comparisons |
| Major-left | 8 / 4 | Diagram with a legend or readout |
| Major-right | 4 / 8 | Thumb with explanation |
| Thirds | 4 / 4 / 4 | Three steps, three media |
| Quarters | 3 / 3 / 3 / 3 | Four thumbs or stats |
| Centred | 8, offset 2 | Single statements, formulas, prose |

Everything sits on the 8-unit baseline. Nothing bleeds past the safe area except `media-bleed` (§9.4).

## 2. Type

**Two faces, and the second one is only for variables.**

### 2.0 The stacks

**Everything except algebraic variables** — declared once on `body`, never re-declared:

```css
font-family: Roboto, "Helvetica Neue", Arial, sans-serif;
```

**Roboto is pinned, not inherited from the OS. This clause governs every other font reference in this document and in `Design System.md`; anything describing a system stack is superseded.** Self-hosted and subset (Latin + §13.2–13.3 glyphs) at weights 500 / 700 / 800, `font-display: swap`, with a `<link rel="preload">` so the download starts before the CSS is parsed rather than after.

The reason it is pinned rather than left to the system stack: §0.4 (a board never scrolls), §7a.2 (≥ 55% fill) and §2.6 (words per band) are all *measurements*. On a variable stack a board authored on macOS can overflow on Windows, because SF Pro, Segoe UI and Roboto have different widths and x-heights. A pinned face makes a board that fits fit everywhere.

**Algebraic variables** — the one exception:

```css
font-family: "Times New Roman", Tinos, "Liberation Serif", Georgia, serif;
font-style: italic;
```

Italic serif for variables is the convention of every maths textbook and every typeset paper, and it earns its exception: it makes `a` the *unknown* visibly different from `a` the letter, and `x` visibly different from `×`. Tinos and Liberation Serif are metric-compatible with Times New Roman and cover Linux and Android.

**Monospace** — column arithmetic and code only: `"Roboto Mono", ui-monospace, SFMono-Regular, Menlo, monospace`.

Numerals use `font-variant-numeric: tabular-nums` anywhere figures are compared or stacked.

### 2.0a What is a variable — and what is not

The italic serif applies to **lowercase single letters standing for a quantity**: `x y z a b c n k r t`, and their subscripted forms (`x₁`, `aₙ`).

It applies **everywhere that letter appears** — in the expression, in the prose about it, and in the label on a diagram. `aⁿ` in a formula and "the value of *a*" in the sentence below it are the same referent, so they wear the same face (§34.6).

**Everything below stays Roboto upright.** Each line is a real convention, not a preference:

| Not a variable | Why |
|---|---|
| Numerals — `2³`, `27` | A number is not an unknown |
| Operators — `+ − × ÷ =` | Upright, always |
| Function names — `sin cos tan log` | Upright roman: `sin x`, never *sin x* |
| Units — `cm kg s °` | Upright, or `5 s` reads as *5 × s* |
| Point and vertex labels — `A B C`, `△ABC` | Uppercase, geometry not algebra |
| Set names — `N W Z Q` | Uppercase |
| Multi-letter names — `area`, `max` | Two letters would read as a product |
| Constants named by word — `π` | π is upright; it is a fixed value |

**A variable never carries an anchor colour and the italic at the same time** unless it is that board's focal point (§0.6). The face already distinguishes it; adding hue makes two signals for one fact.

### 2.1 The four sizes

| Role | Size | Line-height | Tracking |
|---|---|---|---|
| `hero` | 48 | 1.05 | −0.025em |
| `title` | 36 | 1.2 | −0.015em |
| `body` | 24 | 1.5 | 0 |
| `label` | 16 | 1.3 | 0 (+0.09em when uppercase) |

`hero` and `title` never appear together. A board uses at most three of the four. **Nothing a student reads as a sentence goes below `body`.**

**`hero` and `figure` never appear together either.** At 48 and 44 they are 4px apart, which reads as an inconsistency rather than a distinction. They do not collide in practice: `hero` belongs to the introduction and closing boards (§44), `figure` to data and working boards. If a board seems to need both, the larger one is the board's destination and the other is content — set it at `title`.

### 2.1a Size states role, not enthusiasm

The step is decided by a line's **job on this board**, never by its length or its warmth:

- **The board's destination takes the larger step** — the question it exists to raise, the claim it lands on. On a board asking "So what is repeated multiplication?", that question is the destination even though the recap above it is the longer sentence.
- **A recap of prior knowledge takes `body`.** "You already know that…" is setup, not payload. Setting it at `title` inverts the board: the student's eye lands on what they already know.
- **Reference material is a caption, never a message.** Unit keys ("each □ = 1"), legends, axis labels and source notes sit at `label` or below, in `#868e96`, and never share a line with the board's question. If a legend needs the question's step to be noticed, the visual isn't legible enough — fix the visual.

### 2.1b Title vs narration — the test that decides the step

A prominent line at the top of a board is **not automatically a title.** Apply this test:

| | Title | Statement (narration) |
|---|---|---|
| Form | A noun phrase that *names* the board | A full sentence that *says something* |
| Example | "Area of a trapezoid" · "What you will be able to do" | "One pair of opposite sides is parallel now. You have formed a trapezoid." |
| Step | `title` 36 / **800** | `statement` 36 / **500** |
| Ink | `#212529` | `#495057` |
| Accent | at most one word | the key term, at 800 |

**`statement` (30 / 500) is the one sanctioned use of 30px at content weight.** It exists because setting a whole narrated sentence at 800 spends all of a board's emphasis on connective words — "one pair of", "you have formed a". **Bold is expensive: it buys attention only while it stays scarce.**

A statement carries exactly one accented term at 800 — the thing the sentence exists to deliver.

Two additions for maths and data only:

| Role | Size | Use |
|---|---|---|
| `figure` | 44 | A single result or live value that *is* the content of the board |
| `micro` | 12 | Axis ticks on a dense chart, superscripts. Never a sentence, never prose |

### 2.2 Three weights — and what decides them

Weight encodes **what kind of thing the text is**, never how important it feels. The categories are mutually exclusive, so every string has exactly one correct weight:

| Weight | Category | Test | Examples |
|---|---|---|---|
| **800** | **Destination** — what the eye lands on first, plus highlighted terms | "Is this the single most important element, or one word being marked?" | Board title · highlighted term · badge numeral · a result |
| **700** | **Control** — text inside interactive or navigational chrome | "Is it inside a button, chip, tab, axis or legend, and ≤4 words?" | "Check answer" · "Hint" · eyebrow chips · axis ticks |
| **500** | **Content** — anything read as a sentence | "Would you read it aloud as a sentence?" | Prose · subtitles · list items · options · captions |

**At most ONE 800 element per board.** Weight creates hierarchy only when most text isn't heavy. A board whose title is 800, whose three list rows are 700 and whose button is 700 has no hierarchy — everything shouts.

- **A list item is content, not a label.** Objectives, bullets, MCQ options are `body`/500 even when short.
- **Never use weight for emphasis.** Size says which step it is; colour says whether it carries meaning. Weight only says what kind of text it is.
- **When every ledger token is spoken for, a non-anchored term stays unemphasised.** Weight-in-ink is *not* a fallback. If "addition" and "multiplication" have no anchor because base/exponent/result own all three tokens, they are set as plain content — the sentence's structure does the work. Reaching for 800 to compensate reintroduces exactly the shouting this rule exists to prevent, and it makes the term look anchored when it isn't.
- **No 400, no 600.** 400 is too light at classroom distance; 600 is indistinguishable from 700 and only invites drift.
- A highlighted word goes 800 **at the same size** — the only place 800 repeats, capped at one word per sentence.

### 2.3 The matrix

If a string isn't here, it's wrong:

| Element | Size | Weight | Ink |
|---|---|---|---|
| Title (title board) | 38 | 800 | `#212529` |
| Title (content board) | 30 | 800 | `#212529` |
| Statement (narrated sentence) | 30 | 500 | `#495057` |
| Subtitle | 20 | 500 | `#495057` |
| Prose | 20 | 500 | `#495057` |
| List item / option | 20 | 500 | `#495057` |
| Highlighted term | 20 | 800 | accent |
| Result / live value | 44 | 800 | accent |
| Eyebrow chip | 14 | 700 | accent |
| Button label | 14 | 700 | `#fff` or accent |
| Caption / helper | 14 | 500 | `#868e96` |
| Axis tick / legend / dimension | 14 | 700 | `#868e96` or accent |
| Badge numeral | 14 | 800 | `#fff` |
| Dense axis tick | 12 | 700 | `#868e96` |

### 2.4 Superscripts & subscripts

Maths content is full of them, and they are **not** a type step — they scale off their parent:

| | Value |
|---|---|
| Size | **0.5× the parent's size**, rounded to the nearest whole px |
| Weight | Inherits the parent's |
| Ink | The parent's, unless the exponent *is* the subject — then the accent |
| Alignment | `vertical-align: super` / `sub`; never a raised baseline hack |

In `aⁿ` the base and exponent are **different roles**: the base is the concept accent, the exponent the emphasis accent. Never colour both the same — that is the whole thing the notation teaches.

A superscript never falls below **12 rendered px** (21 authored). If halving the parent breaks that floor, the parent is too small for notation.

### 2.6 Grade bands

The library runs from *Count Objects Using Fingers* to *Two-Point Form: Derivation and Application*. **One type scale and one density cannot serve both.** Every board declares a band, and the band sets the ceilings:

| Band | Grades | Min body | Max words/board | Max elements | Max steps shown |
|---|---|---|---|---|---|
| **Early** | K–2 | `body` 24 | 8 | 5 | 1 |
| **Middle** | 3–5 | `body` 24 | 20 | 8 | 3 |
| **Upper** | 6–8 | `body` 24 | 28 | 12 | 5 |
| **Senior** | 9–10 | `body` 24 | 38 | 16 | 7 |

**Every band's minimum is `body`** — there is no band-specific size. A board scales to fit the viewport, so a rendered px value was never a physical size: the same board is larger on a monitor than on a tablet. A band minimum was always a statement about **proportion**, not legibility. (The earlier table set Early at 24 against a body of 20, naming a size that was not in the scale at all.)

**Early is the one exception, and it needs no new token: Early sets its sentences at `title` 36, not `body` 24.** It carries 8 words and 5 elements, so it has the room, and a Grade 1 board should read larger in proportion to its board. Its labels stay at `label` 16.

### 2.6a What the word ceiling counts

The ceiling counts words a student must hold **simultaneously** — not words on the board.

A 21-word word-problem stem is **one** reading task: read left to right, once, then set aside. The same 21 words spread across seven diagram labels is **seven** tasks, each re-read every time the eye returns to the figure. Counting those as equal is what makes a raw word count the wrong measure.

- **Counted against the ceiling:** labels, tick and axis labels, option text, list rows, callouts, chips, button labels, legend keys — anything scanned, re-read, or held while looking at something else.
- **Not counted:** a single continuous passage read once — a word-problem stem, a definition, a narrated statement. It counts as **one element** against the element ceiling instead, and is capped separately at **30 words**. One such passage per board.

Without this split the rules contradict themselves. §44b requires a word-problem board to carry a stem *and* a given/asked list *and* a model *and* working *and* an answer, while a realistic stem alone runs 20–25 words — so at Upper's ceiling of 28 that board is unbuildable. With the split, the stem is one element and the 28 governs the annotation load, which is what the ceiling was always for.

**The 30-word cap is not a target.** A passage over 30 words is too wordy for any band — rewrite it, never shrink the type (§7a.2).

- **Early boards carry no prose paragraph** — a caption, a number, and the object, with sentences at `title` 36. Instructions are spoken by the tutor, not printed.
- **Early and Middle hit targets are 56px**, not 44 — smaller fingers, and the object *is* the control.
- The `label` step is not used for anything a student must read in Early; it is for the author's chrome only.
- Above the band's element ceiling, the board splits (§0.3). The ceiling counts *countable things a student must attend to*, not tick marks or gridlines.

A module's band comes from its curriculum placement, is written in the module record (§43.1), and is a **Tier A** check — a Grade 1 board carrying a Senior board's 38 words is unreadable to its own audience whatever size it is set at.

## 3. Colour — the decision procedure

Colour has been the least disciplined part of the canvas, so it is specified as a **procedure**, not a palette. Run it on every text run.

### 3.1 The palette

**Ink** — three, no fourth:

| Token | Hex | Contrast on canvas |
|---|---|---|
| `ink` | `#212529` | 15.9:1 |
| `ink-body` | `#495057` | 8.9:1 |
| `ink-muted` | `#868e96` | 3.5:1 — **labels ≥14 only, never sole-source information** |

**Accents** — one active per board. Ink and fill columns are **not interchangeable**; the light end of each scale fails as text:

| Role | Ink | Fill / stroke | Tint surface |
|---|---|---|---|
| Concept (the thing being taught) | `#7950f2` | `#7950f2` | `#f3f0ff` |
| Action (interactive, live) | `#1c7ed6` | `#228be6` | `#e7f5ff` |
| Emphasis (the unknown) | `#e8590c` | `#fd7e14` | `#fff4e6` |
| Correct | `#2b8a3e` | `#40c057` | `#ebfbee` |
| Wrong | `#e03131` | `#fa5252` | `#fff5f5` |

Banned: `#fab005` / `#ffd43b` as ink · white ink · any hue not above · a second violet (`#6741d9`, `#5f3dc4`, `#845ef7` are all the same role as `#7950f2` — pick the one token).

### 3.2 The procedure

For each text run, in order. **Stop at the first rule that applies.**

**Step 1 — Does the run carry a STATE?**
Correct → `#2b8a3e`. Wrong → `#e03131`. A live value that changes as the student interacts → `#1c7ed6`. **Stop.**

**Step 2 — Is this run the SUBJECT of the board?**
The subject is the one term or figure the board exists to teach or ask about. It takes the board's accent at weight 800.
- The concept being taught → `#7950f2`
- The unknown being solved for → `#e8590c`

**At most one subject run per board.** If two things look like the subject, the board has two ideas. **Stop.**

**Step 3 — Otherwise, ink follows the type step.**
`hero`/`title` → `#212529`. `body` → `#495057`. `label` → `#868e96`.

That's the whole procedure. Three steps, deterministic, same answer every time.

### 3.3 What this forbids — read this before styling a title

- **A title is never fully accented.** Titles are `#212529`, with at most one accented word inside. A title set entirely in violet (with a second, lighter violet on one word) is wrong twice over: it accents a whole run, and it uses two tokens for one role.
- **An accent never spans a sentence.** Accents mark one word or one number.
- **Two accents never appear in one run.** "…a shape we already know — a **parallelogram**" is one accented word inside `#212529`, not a violet sentence with a lighter violet word.
- **`ink-muted` never carries information needed to answer.**
- **Sign is never colour-coded with a state colour.** Rendering negative numbers red-orange and positive blue teaches a student who has learnt red = wrong that every negative number is an error. If a board's subject *is* sign, negative takes concept violet and positive takes action blue, and it is registered in the module ledger. Otherwise the minus glyph carries the meaning on its own.
- **A label naming a state takes that state's accent**, not grey — a quiz eyebrow is `#e8590c`, never `#868e96`.

### 3.4 Surfaces

Local and opaque only (§0.1):

| Token | Value | Use |
|---|---|---|
| `surface-plain` | transparent | **Default** |
| `surface-card` | `#ffffff` | Groups content that must read as one unit |
| `surface-sunken` | `#f8f9fa` | List rows, inert containers |
| `surface-tint` | the accent's tint | Semantic panels and chips only |
| `surface-scrim` | `rgba(255,255,255,.72)` | **Only** over media, to carry ink |

A card asserts that its contents are one unit. It is not a wrapper.

### 3.5 Ink over media

Media is the one place ink cannot be trusted against its background:

1. Prefer a caption **outside** the image.
2. If ink must sit on the image, put it on a `surface-scrim` panel — never directly on pixels.
3. Never white ink; the scrim exists so ink stays dark.

### 3.6 The opacity ladder

Opacity was unspecified, so authors used ~0.30, 0.35, 0.40 and 0.45 for the same job. **Five steps, one meaning each. No value between them.**

| Step | Value | Meaning |
|---|---|---|
| `full` | 1 | Default. Everything a student reads is here |
| `muted` | 0.55 | Present but not in scope right now — still readable, still contrast-checked |
| `excluded` | 0.30 | Explicitly not part of the current set/answer/step |
| `tint` | 0.12 | An accent used as a surface fill behind text |
| `hairline-tint` | 0.08 | The faintest legal fill |

**Below `muted`, an element is decorative and may not carry information a student needs.** If something at `excluded` still has to be read — a label, a value, a set member — it is not excluded, it is `muted`, and it must pass 4.5:1 like any other text.

`muted` and `excluded` are **achromatic**: they desaturate to `#868e96` / `#adb5bd` rather than fading the element's own colour. A faded orange still reads as orange and keeps competing for attention; a faded grey does not.

Never apply opacity to a whole board or a whole region to "push it back" — see §8a.4.

### 3.7 The shade ladder — a recipe, not a list

**Reference implementation: `Shape System.dc.html`. It measures its own contrast at render time; trust it over any number written here.**

A fixed list of hues cannot answer *"what if this board needs a tenth term?"* — and every hand-assembled palette drifts, because a human picks each value. So a variant is **one number: a hue angle**. Lightness and chroma are constants, and the five stops are generated from the angle:

| Stop | `oklch()` | Painted on |
|---|---|---|
| `fill` | `92% .12 h` | Surface at rest — the term's own chip |
| `fill2` | `84% .155 h` | Nested surface, chart band, stronger tint |
| `base` | `48% .19 h` | Highlight stroke, button face, plotted marker |
| `edge` | `36% .165 h` | A button's base edge — the face's own hue, darker |
| `text` | `40% .155 h` | Label on that fill |

**Why OKLCH and not HSL.** Its lightness is *perceptual*: `L 40%` is equally dark at 95° (yellow) as at 255° (blue). In HSL it is not, which is precisely why hand-picked scales drift across the hue circle — and why yellow previously had no legal text stop in this system. It has one now.

**What the constants do and do not guarantee.** They keep every hue in one narrow band, and the band clears every threshold. They do **not** make WCAG contrast hue-invariant: that ratio is built on luminance, and chroma moves luminance, so each ratio lands in a *range*. Measured across the eight ladder hues:

| | Threshold | Measured |
|---|---|---|
| text on fill | ≥ 4.5 | 5.9 – 7.1 |
| base on fill | ≥ 3.0 | 3.2 – 4.1 |
| white on base | ≥ 4.5 | 5.2 – 7.3 |

**A newly generated angle is spot-checked at the low end of the band** — teal sits closest to the floor.

**Chroma, not lightness, is what makes a chip visible.** The canvas is a near-neutral lavender (chroma ≈ .02), so a surface separates from it by being *coloured*, not by being *dark*. Fill-on-canvas luminance ratio is only ≈ 1.3 and that is correct — judge a fill by eye against `#eee9fd`, the canvas's darkest stop, never by that number. The first version of this rule set `fill` to L 95.5% and it was invisible on a real board; the obvious repair, darkening it, made every board heavy and adult. Raising chroma and giving lightness back is the fix.

#### 3.7.1 The default ladder

Eight angles pre-solved, taken **in order**, so the first term on any board in the library is violet and nobody chooses:

| # | Name | `h` | | # | Name | `h` |
|---|---|---|---|---|---|---|
| 1 | Violet | 295 | | 5 | Pink | 350 |
| 2 | Orange | 55 | | 6 | Grape | 320 |
| 3 | Blue | 250 | | 7 | Gold | 95 |
| 4 | Teal | 190 | | 8 | Azure | 220 |

Need a ninth? **Generate it.** Any angle is legal provided it is ≥ 25° from every other hue on the board and outside the two reserved arcs. Below 25° two terms stop being tellable apart.

#### 3.7.2 The two reserved arcs

**`15–40°` means _wrong_. `130–170°` means _correct_.** They are never an anchor, never a selection, never decoration. A board wanting a green-ish anchor takes Teal (190°); a red-ish one takes Pink (350°).

#### 3.7.3 The neutral

`oklch(96% .022 295)` face on an `oklch(78% .05 295)` edge — the brand angle at near-zero chroma. **Not white.** A white face on a grey edge reads as an absence of design, and it is the state every answer option rests in, so it is the most-seen shape in the library.

### 3.8 Colour schemes — the sanctioned combinations

**Pick one scheme per board and stay inside it.** These five are the whole set; a combination not listed here is a new entry, added before use.

| Scheme | When | Palette |
|---|---|---|
| **Anchor triad** (default) | Any board with referents — most boards | violet `#7950f2` · orange `#e8590c` · blue `#1c7ed6` |
| **Monochrome depth** | One concept with parts — place-value columns, fraction parts, nested sets | One hue at `light` / `base` / `deep` |
| **Complementary opposition** | Genuine opposites — before/after, input/output, gain/loss | violet + orange · blue + orange · teal + pink |
| **Analogous run** | An ordered sequence of related categories — chart series, sorted groups, stages | blue → cyan → teal · violet → grape → pink |
| **Triad** | Three coordinate, non-ordered categories. **Maximum three** | violet + teal + orange · blue + pink + lime |

**Six composition rules, all checkable:**

1. **60 / 30 / 10.** Neutral dominates the board, one hue carries the structure, one accent marks the focal point. A board split evenly between two hues has no subject.
2. **Never two hues at `base` with equal area.** One drops to `light`, or shrinks. Equal-weight competing hues is the single most common cause of a "busy" board.
3. **Adjacent hues only at different stops.** Blue with cyan, violet with grape, green with lime — legal at different stops, never both at `base`. At the same stop they read as a mistake rather than a distinction.
4. **Warm advances, cool recedes.** The subject takes the warm hue; context takes the cool one. If the background is warmer than the subject, the board fights itself.
5. **Maximum four hues plus neutrals**, on any board, in any scheme.
6. **The greyscale test.** Convert the board to greyscale: every distinction that carried meaning must still be visible. If two categories collapse to the same grey, they were separated by hue alone — which fails §0.5 and fails ~8% of students.

**Reserved and unavailable to any scheme:** `correct` green and `wrong` red. A scheme that needs a green picks teal or lime; one that needs a red picks pink or orange.

## 4. Radius

| Value | Use |
|---|---|
| 8 | Chips, tags, bar tops |
| 12 | Rows, badges, counter chips |
| 16 | Cards, panels, media boxes |
| **20** | **Surfaces and buttons** — both families of the shape system (§20.0), including answer options and inputs |
| 999 | Pills, tracks, dots |
| 50% | Circles — points, avatars, and the slider thumb (§20.0, the one carve-out) |

**20px is not a step in a size ramp; it is a family marker.** Everything a student reads content from or presses is 20px, so radius carries no meaning between the two — depth does (§20.0). Nothing else on a board may use 20.

## 5. Line & border

**One border: 1px `#e9ecef`.** An accent-bearing border uses that accent at 40% alpha, still 1px. **2px in a solid accent means selected** — the width jump *is* the affordance, so nothing else uses 2px.

| Role | Width | Colour |
|---|---|---|
| Shape outline | 2.5 | accent |
| Construction / helper | 1.5 | `#adb5bd` |
| Dashed original / ghost | 1.5, dash `6 4` | `#ced4da` |
| Dimension leader | 1 | `#868e96` |
| Grid line, minor | 1 | `#e9ecef` |
| Grid line, major | 1 | `#dee2e6` |
| Axis | 1.5 | `#adb5bd` |
| Data line | 2.5 | accent |
| Vector / arrow | 2.5 + 8px head | accent |
| Divider | 1 | `#e9ecef` |

## 6. Shadow

```
resting  0 2px 6px -3px rgba(70,46,146,.16)
raised   0 10px 24px -12px rgba(70,46,146,.30)
```

Coloured glows only on a primary button, in its own accent. **No shadow on media** — an image already has an edge. No shadow on a tint panel.

## 7. Spacing

**Margins are banned inside a board** — `gap` only (`margin:0 auto` for centring is the sole exception). Margin chains don't collapse predictably and break when a child is conditionally hidden.

### 7.1 Gap scale

| Token | Units | Between |
|---|---|---|
| `gap-tight` | 8 | Icon and label; numeral and unit |
| `gap-inner` | 14 | Items in one group — rows, legend entries |
| `gap-block` | 20 | Stacked blocks — title → body |
| `gap-surface` | 26 | Before a distinct surface that closes a board |
| `gap-region` | 40 | Board halves — visual ↔ text |

### 7.2 Board padding

```
padding: 24px 34px 20px;      /* base */
padding: 44px 34px 20px;      /* boards that render an eyebrow chip */
```

The chip is `position:absolute` at `top:16px`, so **only a board that renders one needs the clearance.**

**The height budget is real.** A rendered board is ~329 CSS px tall, ~285 after padding. Sum the children before changing any gap or padding.

### 7.3 Inner padding

| Surface | Padding |
|---|---|
| Chip | `6px 12px` |
| Row (comfortable) | `14px 18px` |
| Row (compact) | `10px 16px` |
| Card / panel | `20px 24px` |
| Formula card | `12px 26px` |
| Tint panel | `14px 16px` |
| Button | `12px 22px` |
| Input | `10px 14px` |

### 7.4 Measure

Prose 560 · list 720 · two-column 820 total.

**Express a measure cap as symmetric `padding-inline`, never `max-width`.** This is a correctness rule, not a preference. A board-level text block is a child of a `column` + `align-items:center` flex parent, so it carries `align-self:stretch` (§7.5a). Stretch pins the box's **left** edge to the content edge; a `max-width` then clamps the width from that pinned edge — so `text-align:center` centres about *that box's* midpoint, which sits left of the board's. Different caps on different blocks produce different offsets, and nothing on the board shares an axis.

```
padding-inline = (content width − cap) / 2

cap 969  → 257px      cap 1246 → 118px      cap 1419 → 31px
(on the standard 1482 content width: 1600 − 2×59)
```

The box stays full width, so its centre **is** the board's centre.

### 7.5 Alignment

- **Centred** boards: titles, single statements, formulas, single visuals.
- **Left-aligned** boards: anything with more than two lines of prose, all lists, all tables.
- Never centre a list's text. Centre the *block*, left-align its contents.
- Numerals that are compared are right-aligned and tabular.

### 7.5a Every text block needs a resolved cross size

A board's inner wrapper is `display:flex; flex-direction:column; align-items:center`. **Any direct text child must carry `align-self:stretch`** — give every one of them a shared class rather than patching them individually.

Without it the child is **shrink-to-fit**: it wraps at that narrower width but its box stays *one line tall*, so the next flex sibling is laid out as if line two doesn't exist and paints straight over it. The symptom looks like a spacing bug and isn't — it is a cross-size bug, and it appears the moment any string grows by one word, so it will not show up on the copy you authored with.

Corollaries:

- **An equation carries `white-space:nowrap`.** A formula that wraps out of its own card border is worse than one that overflows the safe area — it reads as two equations.
- **Rows being compared stretch to one shared column width** and centre their own contents. Shrink-to-fit rows each land on a different axis, which silently asserts they are different kinds of object.
- **Decorative overhang must be unclipped.** A ring, halo or focus outline drawn at a negative inset needs no `overflow` on any ancestor — or the inset reserved as padding. `overflow-y:auto` clips **both** axes, so adding it to a stack crops every ring inside it.

### 7.6 Making a board fit

In order. Only the last two touch design tokens:

1. **Check the padding variant** — no chip on the 44px variant wastes 24px.
2. **Make the repeating stack the flexible child** — `flex:0 1 auto; min-height:0; overflow-y:auto` on the row list. Everything the student must always see (title, action) stays `flex:none` **outside** it, so it can never scroll away. This is what makes residual overflow *reachable* rather than destroyed by the board's `overflow:hidden`.
3. **Cut content.**
4. **Switch rows to compact** — `10px 16px` at 1.35 leading. The only sanctioned deviation from §7.3.
5. **Never** shrink a type step or drop a weight category.

**A scroll container clips both axes.** `overflow-y:auto` computes `overflow-x` to `auto` too, so **any decoration overhanging its element is cropped** — celebration rings, focus glows, badges pinned outside a row. Therefore:

- Draw decorations **inside** the element's box (`inset:0`, stroke inset by half its width) — never at a negative inset.
- Give a scrolling stack `padding:4px` so soft shadows still have room.
- Match a decoration's corner radius to the element it traces (a 12px row needs `rx:12`, not 16).

This shipped as a real regression: the objectives ring was drawn at `inset:-3px`, and making the stack scrollable cropped it flat at the left edge.

**Measure with the chat panel open.** The board is ~585px wide then; a list item wraps and a row goes 49 → 76.

## 7a. The layout contract

§7 governs the space *around* things — padding, gaps, the safe area. Nothing governed the space *between* them, which is why boards have passed review with correct margins and colliding interiors.

### 7a.1 Nothing overlaps

**No two elements on a board may overlap.** Not slightly, not at the corners, not "it looks fine at this size". A label clipping a figure by 2px is a defect.

The only sanctioned overlaps are elements drawn *behind* another by design:

- a highlight ripple behind a point, member or numeral (§17a.4, §17b.4)
- a fill behind its own boundary
- a counter tail meeting its thumb (§18.1)
- `media-bleed` past the safe area (§9.4)

**Absolute positioning is the cause.** A board laid out with flex and grid *cannot* collide; a board laid out with `position:absolute` and hand-picked coordinates collides the moment a string gets longer, a hue changes the metrics, or the chat panel opens. Absolute positioning is legal only inside a diagram's own coordinate space — an SVG `viewBox` where the geometry is computed (§16e) — never for board-level layout.

### 7a.2 A board is at least half full

**Content occupies ≥ 55% of the safe area's height.** Below that the board reads as unfinished: a card with a sentence floating in it.

**Four board kinds are exempt from the floor, and instead carry a ceiling — but not the same one:**

| Kinds | Ceiling | Why |
|---|---|---|
| `divider` | **40%** | A chip and a title. It is a pause, and a pause filled to half has stopped being one |
| `feedback` | **50%** | The F01 layout this document prescribes is a verdict icon, the expanded answer, and the why — three elements that cannot land under 40% |
| `intro`, `section` | **60%** | §44's T02 explicitly allows a title board one specimen of the thing. A hero, a subtitle and one artefact lands near 55%, which is correct, not overfull |

Their job is to mark a beginning, a transition or a verdict — §44 states outright that a title board has "no list, no CTA". A spare board is what makes the boards around it feel dense. For all four, the requirement is that the content is optically centred (§7a.3) and under the ceiling.

**A ceiling is per kind, not per group.** Two kinds share a ceiling only when they carry the same number of elements — the first version of this rule gave one number to all four and failed on the intro and the feedback board in turn.

For every other kind, if a board cannot reach 55%, one of three things is true:

1. It is **under-explained** — the missing content is the fix (a model, a worked step, a labelled figure).
2. It belongs **merged with its neighbour** (§0.3).
3. It has **no claim at all** and should be cut (§34a.6).

**Never scale content up to fill the space.** Type comes from the four steps (§2) and a figure's size from its own rules; inflating either is how a 90px numeral ends up beside 24px body text.

The band's element and word ceilings (§2.6) are the upper bound. Between that ceiling and this floor is the legal range — outside it in *either* direction, the board is wrong.

### 7a.3 One vertical rhythm

A board's blocks sit on **one gap value**, chosen from §7 and held for the whole board. Two blocks 24 apart and the next pair 41 apart reads as a mistake even when nobody can name it.

- **Optically centred, not mathematically.** A stack with a heading on top carries more weight above its centre, so it sits 4–8 units lower than a true centre.
- **A board-level text block is full width with symmetric `padding-inline`**, never `max-width` on a stretched child — stretch pins the left edge and `max-width` then centres the text about the block's own midpoint rather than the board's.
- **Sibling groups use `gap`, never margins** (§7).

## 8. Motion

| Duration | Curve | Use |
|---|---|---|
| 150ms | `ease` | Hover, colour |
| 340ms | `cubic-bezier(.2,.8,.3,1)` | Element enter/exit |
| 600ms | `cubic-bezier(.4,0,.2,1)` | Board transition, shape morph |
| 900ms | `ease` | Draw-on (a line, a stroke, a path) |

One-shot only; nothing loops except a live indicator. Stagger a list by 60ms per row, maximum 5 rows. Everything decorative dies under `prefers-reduced-motion`.

## 8a. The state model

The single largest source of drift across authors. States were never defined, so every author invented a treatment: a green glow for "in the set", grey at 35% for "not in the set", an orange ring for "tap this", a green gradient for "you picked this". **One state, one treatment, on every element class.**

### 8a.1 The ten states

| State | Meaning |
|---|---|
| `default` | Nothing special is true of this element |
| `emphasis` | The element under discussion **right now** |
| `muted` | Present, not in scope this moment |
| `excluded` | Explicitly not a member of the current set / not part of the answer |
| `selected` | The student chose this |
| `disabled` | Not available yet, or not choosable |
| `complete` | Finished, done, already covered |
| `attention` | Act here next |
| `correct` / `wrong` | Outcome of a judged answer (§21) |

**One state per element at a time.** They never stack — a selected item that is also correct shows `correct`, and nothing else.

### 8a.2 The matrix

Element class down, state across. This table is the whole rule:

| | Text / numeral | Shape / region | Marker / point | Control |
|---|---|---|---|---|
| `default` | ink `#212529`/`#495057` | 1px `#e9ecef`, no fill | 8px, `#495057` | §20 resting |
| `emphasis` | its anchor colour + 800, **same size** | 2.5px accent outline, `tint` fill | 12px in accent | — |
| `muted` | `#868e96` at `muted` | outline → `#ced4da` | 8px `#adb5bd` | reduced-contrast label |
| `excluded` | `#adb5bd` at `excluded` | outline → `#e9ecef`, no fill | 6px `#dee2e6` | — |
| `selected` | — | 2px solid accent | 12px accent, 2px white halo | 2px accent border, `tint` fill |
| `disabled` | `#adb5bd` | 1px `#e9ecef` | — | `#f1f3f5` fill, `#adb5bd` label, `not-allowed` |
| `complete` | ink + `ti-check` before it | 1px `#e9ecef` | filled `#495057` | tick, label unchanged |
| `attention` | — | — | — | §8a.3 |
| `correct` / `wrong` | — | — | — | §21 |

Three rules the matrix depends on:

1. **`emphasis` is the only state that may use colour.** `muted`, `excluded`, `disabled` and `complete` are achromatic. A state rendered in a hue competes with the anchors and is read as meaning.
2. **`complete` is a tick, never a green fill.** Green is permanently `correct` (§34.1). A green "done" tile teaches a student that finishing is the same signal as answering correctly.
3. **No state changes an element's size, weight or position** — except `emphasis` on text, which goes to 800 at the *same* size, and `attention`'s one-shot pulse. Scaling an element to highlight it reflows everything around it, and the reflow reads as an error.

### 8a.3 Attention — the one sanctioned glow

Glow was found carrying three different meanings in one module: "tap here", "you selected this", and "this is in the set". **A glow may never carry meaning.** Exactly one glow exists:

```
ring   2px solid <the element's own accent>, offset 3px
halo   0 0 0 6px <same accent at 0.18>
motion pulse 1.4s ease-out, TWO iterations, then it stops
```

- **At most one `attention` element per board**, and only on the thing the student must act on next.
- It **stops on its own** and never returns without a new prompt. A permanent pulse is decoration.
- It is **never colour-coded** — it takes the accent of the element it sits on, so it says *where*, never *what*.
- **No drawn hand cursors, pointers or tap graphics.** The control's own state is the affordance. If a gesture genuinely needs demonstrating, it is a one-shot motion of the object itself, not a cartoon hand parked on the board.

Every other glow, halo, bloom and `drop-shadow` is stripped (§38.5).

### 8a.4 Receding content

A common pattern: prior content shrinks and fades as new content arrives. **Legal only if the receded content is no longer needed.**

- If the student still has to read it, it does not recede — it moves, at `full`, or it leaves the board.
- If it is scenery, it goes to `excluded` (0.30) and **its text is removed**, not faded. Faded text is a contrast failure wearing a design decision.
- Never scale a region below 0.6 to make room. Two boards is the right answer (§0.3).

### 8a.5 Text shadow, gradient and bevel are banned

Not "discouraged" — they appear on numerals, titles and buttons across the library and there is no case where they are correct:

- **No `text-shadow`**, anywhere, on anything. Ink on the canvas needs no lift.
- **No gradient fill** on a button, surface, shape or text. Flat tokens only (a primary button's own vertical pair is the sole exception, §20).
- **No bevel, inner shadow, emboss or 3D edge.** A thick coloured bottom edge on a *static* shape is a bevel. The one exception is a button's base edge (§20.0.1) — a flat solid offset that the press spends — which is an interaction model, not decoration.
- **No cartoon or display font.** The system stack is inherited and never re-declared (§2).

---
