<!-- Content Canvas Rules — v1.0 — 17 August 2026 — part file 10 of 13 -->

> **PART 8 — AUTHORING FROM SOURCE CONTENT**
> 
> | | |
> |---|---|
> | **Owner** | Content Canvas — **feeds** |
> | **Domain** | Pedagogy & Arc (1) + Evidence & Gates (9) |
> | **Governs** | The pre-flight pass, colour anchoring, layout verdicts, the highlight doctrine, visual continuity. |
> | **Loaded when** | A module is being recreated from existing source material. |
> | **Requires** | `00-contract.md` + `01-foundations.md` + `12-rules.md` |
> | **Version** | v1.0 — 17 August 2026 |

> **What this file does not decide.** Type steps, colours, radii, shadows, spacing, the layout
> contract, motion and state values are defined in `01-foundations.md` and cited here by `§`
> number. If a value you need is not in this file, it is there — do not infer it. `§` refers to
> sections (numbered 0–45); `R` refers to rules (numbered 1–120) in `12-rules.md`. Both numbering spaces are
> permanent: numbers are added, never reassigned.

---
# PART 8 — AUTHORING FROM SOURCE CONTENT

When a module arrives as an existing deck, PDF or storyboard, **the source is evidence, not raw material.** Its colours and layouts were decided by someone who knew the pedagogy. This part is the pass that must happen **before any board is designed**.

## 33. The pre-flight pass

Read the **entire** module first. Never design board 1 having only read board 1 — anchoring and visual continuity are module-wide properties, invisible slide by slide.

Produce three artefacts before touching a layout:

1. **A colour ledger** (§34) — every colour used in the source, and what it represents.
2. **A visual-model ledger** (§36) — every graphic, and which model it belongs to.
3. **A layout verdict per slide** (§35) — keep, or redesign with a named reason.

If the source is a PDF, extracting text is **not enough** — text extraction discards colour, so a colour ledger built from text alone is guesswork. Render the pages to images and read the anchoring off the pixels.

## 34. Colour anchoring

**A colour in the source is a semantic commitment, not decoration.** If the base is teal on slide 5, it is teal because the author bound that hue to that idea — and a student who learned the binding on slide 5 will carry it to slide 15.

### 34.1 The accent order

Before mapping anything, know the **rank**. The five semantic accents are not peers — they form an order, and a referent's rank in the module decides which one it gets:

| Rank | Token | Hex | Carries |
|---|---|---|---|
| **Primary** | concept | `#7950f2` | **The thing the module exists to teach** |
| **Secondary** | emphasis | `#e8590c` | The supporting term the primary is defined against |
| **Tertiary** | action | `#1c7ed6` | Results, live values, computed outcomes |
| Reserved | correct | `#2b8a3e` | State only — never a referent |
| Reserved | wrong | `#e03131` | State only — never a referent |

**Only three ranks are available for referents.** Green and red are state, permanently. A module needing a fourth referent colour has too many referents (§34.5).

### 34.2 Choosing the primary referent

This is the decision that everything else follows from, and it is **not** a colour question — it is a pedagogy question. Ask, in order:

1. **What is the module's title?** "Introducing **Exponents**" — the exponent is the subject.
2. **What do the learning objectives name most?** All four objectives here mention the exponent; two mention the base.
3. **Which term is being defined, and which is it defined *against*?** The exponent is defined against the base, not the other way round. **The term being defined is primary.**
4. **Which term is new to the student?** They already know what a base number is; the exponent is the new idea.

The referent that wins is **primary**. What it is defined against is **secondary**. Results are always **tertiary**.

**Never rank by which colour looks better, by which referent you happened to read first in the source, or by the source's own hue.** A source deck may put its brightest colour on a supporting term; that is its layout decision, not its pedagogy.

Worked failure: the first ledger assigned base → primary violet and exponent → secondary orange, because the base's coral appeared first when reading the source's fill colours. The result was that a module *called* "Introducing Exponents" rendered the exponent in its second-rank colour — the subject visually subordinate to its own supporting term, on every board. Re-ranked: exponent primary, base secondary, result tertiary.

### 34.2a The comparison-board exception

On a board whose whole job is to contrast **two routes to a number** — the route the student knows against the route being taught — the anchoring changes for that board only:

- The statement naming a route and the **number that route produces** share one token.
- The known route and its result take **secondary**; the taught route and its result (often a `?`) take **primary**.
- **The result token is not used on such a board.** "Which route produced this" outranks "this is a result", and using the result token on both numbers would assert the two are the same kind of answer — which is exactly the confusion the board exists to break.

So `repeated addition` and its `6` are both `#e8590c`; `repeated multiplication` and its `?` are both `#7950f2`. The pairing then reads without a legend, and the student can see which sentence owns which number before reading a word.

Record every use of this exception in the module ledger. Outside a genuine two-route contrast it does not apply — a board merely *showing* a result uses the result token as normal.

**The check:** the module title's key noun and the primary accent must be the same colour. If they are not, the ranking is wrong.

### 34.3 Building the ledger

1. **Inventory** every coloured run across every slide — headings, terms, labels, shape fills, arrows, callouts.
2. **Group by referent**, not by hue: what does each colour *point at*? (`base` · `exponent` · `result` · `wrong path` · `real-world context`.)
3. **Map each referent to exactly one canvas token** from §3.2 — a permanent binding for the whole module.
4. **Lock it.** Record the ledger beside the module; every board reads from it.

```
module: G08C01M01 Exponents
anchors:
  base ............... concept   #7950f2
  exponent ........... emphasis  #e8590c
  result / product ... ink       #212529
  misconception ...... wrong     #e03131
  correct path ....... correct   #2b8a3e
  real-world ......... concept   #7950f2
```

### 34.4 Resolving conflicts

| Source condition | Resolution |
|---|---|
| One hue used for two different referents | **Split.** Two referents need two tokens, or the notation teaches nothing |
| Two hues used for one referent | **Merge** onto one token — the variation was almost certainly incidental |
| A hue with no discernible referent | Decorative — drop it, or move it to the extended palette (§32) if it is inside an illustration |
| A hue that collides with a reserved meaning (green/red) | **Re-map.** Nothing decorative may wear `correct` or `wrong` |

### 34.5 The anchoring rules

- **A term keeps its colour everywhere it appears** — in a title, in prose, in a diagram label, on a chart axis, inside an applet.
- **The module ledger outranks the per-board accent choice.** §3.2 step 2 picks *which run* is the subject; the ledger picks *which token* that subject wears. A board never re-assigns an anchored hue for local contrast.
- **Anchors survive layout changes.** Redesigning a board (§35) never re-colours it.
- **Introduce an anchor once, explicitly** — the board that first names `base` is the board that first colours it. After that, the colour alone carries the meaning.
- **Cap it at three referent anchors per module** — primary, secondary, tertiary. More than three and the bindings stop being learnable, and there is no fourth rank to give them (§34.1).

### 34.6 A word naming a referent wears that referent's anchor

An anchor binds a **referent**, not a glyph. So *every* representation of that referent carries the same token:

| Representation | Example |
|---|---|
| The symbol | the `n` in `aⁿ` |
| **The word that names it** | "exponent", "power", "raised to" |
| The label or callout | a legend key, a diagram arrow label |
| The heading that introduces it | "Introducing **Exponents**" |

**This is where anchoring most often breaks.** §3.2 step 2 identifies *which run* is the subject, and it is tempting to give that run the board's default accent. But if the run **names an anchored referent**, the ledger has already decided its token — and using the default instead silently reassigns the anchor.

Worked failure: a title board read "Introducing **Exponents**" with the word in concept violet, above `2²` and `2³` whose bases were also violet and whose exponents were orange. The board therefore taught that violet means *exponent* in the heading and *base* two lines below it — on the module's very first slide, before the student had any other evidence.

**The check.** On any board showing both a referent's word and its symbol, verify they match:

```
the word "exponent"  →  emphasis  #e8590c
the symbol  n  in aⁿ →  emphasis  #e8590c   ✓ match
the word "base"      →  concept   #7950f2
the symbol  a  in aⁿ →  concept   #7950f2   ✓ match
```

If a board names two referents, both words take their own anchors — that is the one sanctioned case of two accents in a single heading, because they are two referents and not two emphases.

Corollary: **never accent a word with a token anchored to something else.** If the word being highlighted has no anchor, use the board's accent; if it has one, the ledger wins.

## 35. Layout verdicts

**The default is to keep the source layout.** A layout that survived authoring and review usually encodes a reason — a reading order, a comparison, a reveal. Redesigning by reflex discards that.

### 35.1 The three tests

Judge each source slide. It passes unless it fails one of these:

| Test | Fails when |
|---|---|
| **Hierarchy** | You cannot tell in one second what the slide is about; two elements compete for first read; the most important element is not the largest or the most saturated |
| **Readability** | Text below the `body` step; a wall of prose; measure past ~70 characters; ink on an unscrimmed image; a table doing a chart's job |
| **Information architecture** | Two ideas on one board; the order of elements contradicts the order of the explanation; a comparison whose two sides are not parallel; a reveal spoiled by showing the answer alongside the question |

### 35.2 The verdict

- **Passes all three → keep the layout.** Re-skin it with canvas tokens and change nothing structural. Match the source's element order, split, and emphasis.
- **Fails one → fix that one thing.** A hierarchy failure is usually a type-step change, not a new layout.
- **Fails two or more → pick a different layout** from Part 9, and **name the failure** in the build notes. "I preferred a different arrangement" is not a reason.

A slide that is only *plain* has not failed. Plain is often correct.

## 34a. The highlight doctrine

§0.6 says every board has exactly one focal point. This is **how you find it** — a procedure, not a judgement, because with 30 authors a judgement produces 30 answers.

### 34a.1 Key takeaways are the baseline

Before any board is designed, the module declares **3–5 key takeaways** — the sentences a student should be able to say afterwards. Not objectives ("learn to identify…"), but claims:

```
takeaways:
  T1  An exponent counts how many times the base is multiplied by itself.
  T2  The base and the exponent play different roles — 2³ is not 3².
  T3  Repeated multiplication grows far faster than repeated addition.
```

These go in the module record (§43.1) **before board 1 exists**, and everything else refers back to them. They are the module's truth set: if it isn't in the takeaways, it isn't what the module is for.

### 34a.2 The takeaway test — five steps per board

1. **State the board claim** in one sentence: *"After this board, the student knows ___."* If you cannot write it, the board has no point.
2. **Map the claim to a takeaway.** Every board serves at least one. **A board serving none is cut or merged** — this is the rule that removes filler, and it removes a surprising amount.
3. **Find the delta.** What part of the claim was *not* already true before this board? A board's job is the delta, never the whole claim.
4. **Take the shortest span carrying that delta.** One or two words, one number, one region, one edge. Not the sentence, not the topic word.
5. **Colour it by rank** — the anchor of the referent it names (§34.1–34.2). Primary if it is the module's subject, secondary if it is what the subject is defined against, tertiary if it is a result.

**Worked example.** Board claim: *"After this board, the student knows that 2³ means 2×2×2, not 2×3."* → serves **T2**. Delta: the *distinction* between the two readings — T1 already established what an exponent counts. Shortest span: `2 × 2 × 2` and `2 × 3`, the two expressions themselves. Rank: the exponent is primary, so the correct reading takes concept violet and the misreading takes neutral ink — never `wrong` red, because it is a misconception being examined, not an answer being judged.

### 34a.3 What is never the highlight

- **The topic word repeated from the title.** If the board is titled "Exponents", the word *exponent* in the body is not news.
- **A connective** — "is", "the", "and", "when". Grammar is not a delta.
- **A term already highlighted on an earlier board.** It is known now; highlighting it again spends the budget on old information and tells the student nothing changed.
- **A whole sentence.** If the delta really is the whole sentence, the board is carrying two ideas (§0.3).
- **Anything not traceable to a takeaway.** That is the test's whole purpose.

### 34a.4 The highlight budget

Highlighting works only while it stays scarce — the same economics as weight (§2.2):

- **A term is highlighted twice in a module: on the board that introduces it, and on the board that recaps it.** Not on the boards in between, where it is context.
- **One highlight per board** (§0.6). A second competes and both are lost.
- **Each takeaway keeps one colour for the whole module**, via the anchor ledger. T1's terms are always violet; T3's always orange.

### 34a.5 The highlight ledger

Recorded per board, beside the colour ledger, so the whole module can be audited in one read:

```
board  claim                                    takeaway  highlight            token
b03    repeated multiplication ≠ repeated add.   T3       "repeated mult."     primary
b05    the small number counts the factors       T1       "how many times"     primary
b08    base and exponent are different roles     T2       "base" / "exponent"  sec / pri
b13    2³ is not 2×3                             T2       "2 × 2 × 2"          primary
```

Three audits fall straight out of this table and all three are mechanical:

- **A takeaway with no board** — the module claims something it never teaches.
- **A board with no takeaway** — filler; cut it.
- **A term highlighted on five boards** — the budget is blown, and none of the five reads as important.

### 34a.6 No bland boards — and no decorative colour

A board carrying no accent at all is a **Tier B failure: an undecided board.** It means nobody named what it was for.

But the fix is never to add colour. Colour is *found*, not applied:

> Run the takeaway test. If it yields a span, that span takes the accent and the board is fixed. **If it yields nothing, the board has no claim — the fix is to cut or merge it, not to paint it.**

This is the difference between a board that looks designed and one that looks decorated, and it is the reason §0.6 is in the contract rather than in a style section. Colour marks meaning; a board with no meaning to mark should not exist.

## 36. Visual continuity

### 36.1 Every content board earns a graphic

**Text-only boards are a failure of authoring, not a style choice.** If a board carries an idea, it carries a visual that makes the idea legible: a diagram, an array, a chart, an annotated media frame, a formula treated as an object.

Budget per content board:

| | Limit |
|---|---|
| Sentences | 2 |
| List rows | 4 |
| Words on the board | ~40 |
| Visuals | 1 |

Over budget means **split the board**, not shrink the type (§7.6).

Exempt: `T01`/`T04` dividers, `T06` objectives, `T05` closing — those are structural, and their job is words.

### 36.2 One visual model per module

The single most common failure in recreated content: **a different metaphor on every slide.** Tiles, then a pie, then a bar chart, then a number line — each fine alone, together teaching nothing, because the student spends every board learning to read a new picture instead of the idea.

- **Choose one model for the module** and declare it in the ledger. For exponents: the **array/tile model** (a factor per row).
- **Introduce it once**, at its simplest, and **extend it** — 2² as two rows, then 2³ as three, then the cube. Each board builds on the last board's picture.
- **The model's parts keep their anchored colours** across every appearance.
- **A second model is permitted for exactly two reasons**, and never for variety:
  - **To contrast** — a wrong model beside the right one, on a single board, then dropped.
  - **To bridge** — the *same quantity* shown in two models simultaneously, because the equivalence **is** the lesson. This covers the whole fraction ↔ decimal ↔ percentage ↔ ratio cluster, and *Connecting Fractions and Decimals*, *Repeated addition is multiplication*, *Connection of Ratios and Fractions* and their kin.

  A bridge board uses layout `D18` and obeys three constraints: **both models show the same quantity** · **the whole is the same physical size in both** · **the equality is written between them**, not implied by adjacency. Once bridged, the module continues in the *destination* model — a bridge is a crossing, not a permanent pairing.
- **Never restart.** If board 12 needs a picture the model cannot express, the model was wrong from board 1 — change it everywhere, not just there.

### 36.3 The concreteness ladder

Within one model, progress in this order and never skip a rung:

| Rung | Form | Example |
|---|---|---|
| Concrete | Countable objects | 8 physical tiles in 3 groups of 2 |
| Representational | The same arrangement, drawn | A 3×2 grid of squares with bracketed labels |
| Symbolic | Notation alone | 2³ = 8 |

A board may show two adjacent rungs side by side — that pairing *is* the teaching. It may never show only the symbolic rung before the concrete one has appeared.

### 36.4 The visual-model ledger

```
module: G08C01M01 Exponents
model:  array / tile  (one row per factor)
parts:
  tile ........... concept tint fill, concept 2.5px outline
  row bracket .... helper 1.5px
  factor label ... concept 800
  count label .... emphasis 800
progression:
  b06 concrete ......... 3 groups of 3, numeric
  b07 representational . general a x a x a
  b12 concrete+symbolic  3 groups of 2 -> 2^3 = 8
  b19 symbolic ......... powers of 2 in a table
```

### 36.5 Content accuracy — the audit every manipulative must pass

A visual that is beautiful and wrong is worse than no visual: it teaches confidently. Run all six checks **before** drawing, and again on the finished board.

**1. The manipulative's grammar must match the operation.**

| Operation | Legitimate grammar | Never |
|---|---|---|
| Repeated addition | A strip or row of units, grouped | — |
| Repeated multiplication | Nesting, branching/doubling tree, area, volume | A strip |
| Comparison of magnitudes | Shared baseline, one unit size | Two different unit sizes |

Repeated multiplication is a doubling *of a doubling* — it is not one-dimensional, so it cannot borrow the additive grammar. Drawing `2 × 2 × 2` as three groups of two depicts `2 × 3`, and a linear arrangement guarantees an additive reading no caption can undo.

**2. Count the factors against the drawing.** A doubling tree for `2 × 2 × 2` opens on the **base** (2 units) and doubles twice — two arrows, three factors. Opening on a single unit with three arrows depicts `1 × 2 × 2 × 2`, which is not the expression written beside it.

**3. One declared unit = one drawn size.** Every instance of a unit is the same dimensions and the same stroke, across every stage and every board. Shrinking units to fit a later stage breaks the link between ink and quantity — 8 units drawn small read as *less* than 6 drawn large, reversing the very growth the board exists to teach. If the last stage doesn't fit at full unit size, reduce the number of stages, not the unit.

**4. A visual may not depict a misconception a later board corrects.** Check every manipulative against the whole module (§33). If board 13 says "2³ is *not* 2 × 3", then no earlier board may draw 2³ as three groups of two — otherwise the module teaches the trap first and penalises it four boards later.

**5. Every "?" must be answerable from what is drawn.** A withheld answer is only productive if the student can reason to it from the board. If the visual makes the *wrong* answer the natural reading, the "?" isn't a question — it's a trap. Test by answering it yourself using only the drawing.

**6. A claimed bridge must be shown, not asserted.** If a line says "repeated addition *is* multiplication", both forms appear on the board — `2 + 2 + 2 = 2 × 3 = 6`, not just the addition. A title asserting an equivalence whose second half is missing leaves the student to take it on faith.

**And define the unit once.** State what one unit means on its first appearance, as a caption (§2.1a), then carry that unit unchanged. Never redefine it, never restyle it, and never restate the definition on a later board — a re-explained unit reads as a *different* unit.

---
