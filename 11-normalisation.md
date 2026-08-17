<!-- Content Canvas Rules — v1.0 — 17 August 2026 — part file 12 of 13 -->

> **PART 10 — NORMALISING AN EXISTING LIBRARY**
> 
> | | |
> |---|---|
> | **Owner** | Content Canvas — **feeds** |
> | **Domain** | Evidence & Gates (9) |
> | **Governs** | The conformance model, snap tables, asset remediation ceilings, the normalisation pass, triage, ownership across authors, records and re-runs. |
> | **Loaded when** | An existing library is being brought into conformance at scale. |
> | **Requires** | `00-contract.md` + `01-foundations.md` + `12-rules.md` |
> | **Version** | v1.0 — 17 August 2026 |

> **What this file does not decide.** Type steps, colours, radii, shadows, spacing, the layout
> contract, motion and state values are defined in `01-foundations.md` and cited here by `§`
> number. If a value you need is not in this file, it is there — do not infer it. `§` refers to
> sections (numbered 0–45); `R` refers to rules (numbered 1–120) in `12-rules.md`. Both numbering spaces are
> permanent: numbers are added, never reassigned.

---
# PART 10 — NORMALISING AN EXISTING LIBRARY

Parts 0–9 tell an author how to build a board correctly. This part is the other direction: **how to take ~2000 modules built by 30+ authors, each with its own colours, boxes, glows and type, and land them all inside this system** — deterministically, at scale, without hand-judging every board.

Everything here is written to be **executable**: a normaliser (script or agent) reads a found value and gets exactly one legal answer. Where a decision genuinely needs a human, the rule says so and routes it, rather than leaving it to taste.

## 37. The conformance model

### 37.1 What "conformant" means

A module is conformant when **every rendered value is traceable to a token in this document** — not when it merely looks similar. Similar-looking is how 2000 modules drifted in the first place.

Four states, and every module is in exactly one:

| State | Definition | Ships? |
|---|---|---|
| **Conformant** | Zero Tier A failures, Tier B score ≥ 90, record complete | Yes |
| **Skinned** | Zero Tier A failures, Tier B outstanding, exceptions registered | Yes, with a registered debt |
| **Quarantined** | Tier A failure that cannot be fixed without a rebuild | Yes, in the legacy skin (§41.4), flagged |
| **Blocked** | Tier A failure that is fixable and unfixed | No |

### 37.2 The two tiers, generalised

Part 5 defined tiers for applets. **The same two tiers govern every asset class** — do not invent per-class severity.

**Tier A — blocks ship.** These break the product, not its consistency:

- A board paints an opaque background, tint or gradient (§0.1)
- Text below the `body` floor, or text that cannot scale (baked into a raster)
- Contrast below 4.5:1 for text, 3:1 for a graphical boundary
- Colour as the only carrier of a state (§0.5)
- A board that scrolls, or content outside the safe area
- A hit target below 44px, or an affordance discoverable only on hover
- A face other than Roboto visible beside canvas text (§2.0)
- A visual that is **factually or pedagogically wrong** (§36.5) — this is Tier A, not cosmetic

**Tier B — align, negotiable.** Radii, shadow steps, border widths and colours, gap values, non-token accents, illustration hues, fluid type sizing, decorative motion.

### 37.3 Scoring

One score per module, so 2000 modules can be ranked and progress measured:

```
Tier A failures ......... count (must be 0)
Tier B score ............ 100 − (weighted failures / total checked × 100)

weights:  colour 3 · type 3 · geometry 2 · spacing 2 · shadow 1 · motion 1
```

Report per module **and per author** — drift is authored, so the per-author view is what actually reduces the backlog.

## 38. The snap tables

**The core of the migration.** A found value is never "close enough": it is classified, then mapped. These tables must produce the same answer on every run, for every module, without reference to how the board looks.

### 38.1 The first rule of snapping: strip, don't translate

**Most found styling carries no meaning, and the default action is removal — not conversion to a token.** Thirty authors produced thousands of decorative glows, tints, gradients and coloured borders that mean nothing. Translating each one to its "nearest token" preserves the noise in a legal palette; deleting it is what actually unifies the library.

Apply this test to every found declaration:

> **Would a student be unable to answer a question on this board if this declaration were deleted?**

- **No** → delete it. This is the answer for the large majority of found shadows, tints, gradients, glows, coloured borders and decorative fills.
- **Yes** → it carries meaning; snap it via the tables below, and record what it means in the module record.

Only ever snap after the strip pass. Snapping first produces a tidy palette full of things that shouldn't be there.

### 38.2 Colour — classify by function, never by hue

**Never map a found colour to its nearest palette hue.** Nearest-hue matching is the single worst failure mode at scale: a decorative mustard becomes `wrong` red, a brand teal becomes `correct` green, and the library ends up full of false state signals. Classify what the colour *does* first, then map inside that role.

**Step 1 — classify by what the declaration paints:**

| Found on | Role |
|---|---|
| A sentence, a caption, a label | Ink |
| A single term inside a sentence | Anchor candidate → §34 |
| A fill behind text | Surface |
| A 1px line, a divider, a table rule | Border |
| A 2px+ line, an outline that changes on selection | State/selected |
| A shape outline, an axis, a construction line in a diagram | Geometry (§16) |
| A fill in an illustration | Extended hue (§32) |
| A shadow, glow or halo | Shadow (§38.5) |

**Step 2 — map inside the role:**

| Role | Mapping |
|---|---|
| Ink — primary | `#212529` |
| Ink — secondary/prose | `#495057` |
| Ink — tertiary/caption | `#868e96` |
| Anchor | The module's ledger token for that referent (§34). **No referent → strip to ink.** |
| Surface | `surface-card` (opaque white) · `surface-sunken` · accent tint at 8–12% |
| Border | 1px `#e9ecef` |
| State/selected | 2px in the relevant accent |
| Geometry | Per §16 — outline 2.5px accent, helper 1.5px `#adb5bd` |
| Extended hue | Nearest of the 12 hues (§32), snapped to its `light`/`base`/`deep` stop |
| Shadow | §38.5 |

**Step 3 — the reserved-colour guard.** After mapping, assert: no green in the `correct` range and no red in the `wrong` range survives anywhere that is not a state. A decorative green must move to the extended `teal`/`lime` hue, not keep `#40c057`. This check runs on every module, every time — it is the one that prevents a student reading a decorative tick-green as "you got it right".

**Step 4 — de-duplicate violets.** `#7950f2`, `#6741d9`, `#5f3dc4`, `#845ef7` and `#9775fa` are all the same role. Collapse to the one token. Same for any hue appearing at multiple shades in one role.

### 38.3 Type

Weight is **not** snapped from the found value — the found value is only a hint. **Reclassify by category** (§2.2): is this string a destination, a control, or content? Then take that category's weight. A library where every author's 600 became 700 is still wrong.

| Found size (rendered px) | Snaps to |
|---|---|
| ≥ 42 | `hero` 48 |
| 30–41 | `title` / `statement` 36 |
| 20–29 | `body` 24 |
| 14–19 | `label` 16 |
| ≤ 13 | `micro` 12 — **only** if it is not a sentence |

**Round toward legibility.** Any string a student reads as a sentence rounds **up**, never down, and never lands below `body`. A fluid `calc(vw + vh)` size is evaluated at 1600×900 and then snapped.

Also: strip every `font-family` declaration (the stack is inherited), every `italic` (not in the system), every `text-transform:uppercase` that isn't on a `label`, and every `letter-spacing` outside the four steps' values.

### 38.4 Geometry

| Found radius | Snaps to |
|---|---|
| 1–10 | 8 |
| 11–14 | 12 |
| 15–24 | 16 |
| ≥ 25, or a pill | 999 |
| A circle | 50% |
| 0 | 0 — legal **only** on `media-bleed` |

| Found border | Snaps to |
|---|---|
| Any width, no state meaning | 1px `#e9ecef` |
| Any width, marks selection | 2px accent |
| Dashed, any pattern | 1.5px `#ced4da` dash `6 4` |
| Inset / double / groove / ridge | Strip |

| Found gap or padding | Snaps to |
|---|---|
| 1–10 | 8 |
| 11–17 | 14 |
| 18–23 | 20 |
| 24–33 | 26 |
| ≥ 34 | 40 |

Margins inside a board are converted to `gap` on the parent (§7), not snapped.

### 38.5 Shadow, glow and gradient

| Found | Action |
|---|---|
| Any shadow with blur ≤ 8 | `resting` |
| Any shadow with blur > 8 | `raised` |
| A coloured glow, not on a primary button | **Strip** |
| A coloured glow on a primary button | That button's accent |
| Any `inset` shadow | Strip |
| Multiple stacked shadows | Collapse to one step |
| Any shadow on media, or on a tint panel | Strip |
| A gradient on a board background | Strip (Tier A, §0.1) |
| A gradient on a surface or text | Strip; the flat token replaces it |

Text shadows, `filter: drop-shadow` and `backdrop-filter` are all stripped — none exist in this system.

### 38.6 State, opacity and glyphs

| Found | Action |
|---|---|
| Any opacity value | Snap to the ladder: <0.20 → strip the element · 0.20–0.42 → `excluded` · 0.43–0.75 → `muted` · >0.75 → `full`. Tints snap to 0.12 / 0.08 |
| A faded element that still carries information | Raise to `muted` and desaturate; if it fails 4.5:1, it goes to `full` |
| A coloured fade (faded orange, faded green) | Desaturate to the grey ladder (§3.6) |
| A glow carrying meaning | Strip; re-express as the state's own treatment (§8a.2) |
| A glow meaning "act here" | Snap to `attention`, capped at one per board |
| A drawn hand, pointer or tap graphic | Delete |
| Scale-to-highlight | Strip the scale; apply `emphasis` |
| A pulse or blink that loops | Cap at two iterations, or strip |
| `-`, `–`, `—` used as a minus | `−` (U+2212) |
| `x`, `*` as multiplication · `/` as division | `×` · `÷` |
| `<=`, `>=`, `!=`, `...` | `≤`, `≥`, `≠`, `…` |
| Uppercase outside a `label` | Sentence case |
| A coloured fraction bar | Ink `#495057` |
| Sign encoded in colour (negative red, positive blue) | Strip the colour — the glyph carries it (§3.3) |

**The state audit is per element, not per declaration.** For each element ask which of the ten states (§8a.1) it is in, then apply that row of the matrix wholesale — do not translate the author's chosen treatment. Translating preserves ten dialects in legal tokens; classifying produces one language.

## 39. Asset classes and their remediation ceilings

**A rule you cannot enforce on an asset is not a rule — it is a rebuild request.** Each class has a ceiling on what normalisation can reach, and the ceiling determines the route, not the severity of the finding.

| Class | Styling reachable? | Ceiling | Route |
|---|---|---|---|
| Board markup (HTML/CSS) | Fully | Everything | Normalise in place (§40) |
| Inline SVG | Fully | Fills, strokes, type, geometry | Token-map every paint attribute |
| Linked SVG file | Fully, but shared | Same, with copy-on-write | Copy per module before editing; never edit a shared asset in place |
| Photograph | Not needed | Framing only | `MEDIA[...]` box + `object-fit:cover` + scrim if ink sits over it (§9, §3.5) |
| Raster with baked-in text | **No** | Cannot be fixed | **Tier A.** Text in a raster cannot scale, translate, be read aloud or meet contrast. Re-author as markup, or quarantine |
| Raster with baked-in chrome (old card, glow, gradient) | **No** | Crop only | Crop to the content; if the chrome cannot be cropped away, re-author or quarantine |
| Screenshot of a slide | **No** | — | Treat as a source deck (§33), not as an image. Rebuild as boards |
| PDF page | **No** | — | Render, read colour and layout as evidence (§33), rebuild as boards |
| Slide deck (PPT/Slides) | Via extraction | — | Extract text, colour and layout; rebuild per Part 8 |
| Video | **No** | Framing only | Fixed box, token radius, poster frame, no restyle, no shadow |
| HTML simulation, own stylesheet | Via override | Tier A always, Tier B with consent | Part 5 — audit, bridge, override layer |
| HTML simulation, styles in JS | Via config | Whatever the config exposes | Request a token-config hook; until then, override what CSS can reach |
| `<canvas>` / WebGL simulation | **CSS cannot reach it** | Only what its JS config exposes | §39.1 |
| Third-party embed (YouTube, GeoGebra, H5P) | Chrome only | The frame around it | Normalise the frame; register the interior as an exception |
| Icon font other than Tabler | Fully | — | Map glyph-by-glyph to Tabler; no second icon set survives |
| Embedded font file | Fully | — | Delete; the canvas serves Roboto and the applet inherits it (§2.0) |

### 39.1 Canvas and WebGL simulations

A drawn-pixel simulation is the one asset class where the override layer is powerless — there are no elements to select. Rules:

1. **Never attempt a CSS fix.** It will appear to succeed on the frame and change nothing inside.
2. **The palette must come from a config object** the host can set — the JS equivalent of the token bridge (§26). Request one from the owner: an exported `setTokens({ink, concept, emphasis, action, surface, border})` or equivalent.
3. **Until that hook exists**, the simulation is *Skinned* at best. Register it; do not report it as conformant.
4. **Tier A findings inside a canvas** (a wrong visual, unreadable text, colour-only state) make the module **Blocked**, not Skinned. Pedagogical correctness is not negotiable against implementation difficulty.
5. The **frame** around it is always normalised — radius, border, shadow, caption, and the transparent board behind it.

### 39.2 Detailed HTML simulations at scale

Part 5's per-applet protocol works for one applet; for hundreds:

- **Fingerprint before auditing.** Hash each simulation's stylesheet. Identical hashes across modules are the *same* asset — audit once, fix once, apply everywhere. In a 2000-module library, a few hundred distinct simulations typically account for the majority of instances.
- **Group by vendor/author**, then negotiate once per group rather than once per instance (§42).
- **Version-pin every override** to the stylesheet hash it was written against. When the hash changes, the override is stale and the module returns to the audit queue automatically (§29).
- **Never fork a simulation to restyle it.** A fork stops receiving the owner's pedagogy fixes, which is a worse outcome than a cosmetic non-conformance.

## 40. The normalisation pass

Ordered, and the order matters — each step depends on the last. **The pass must be idempotent: running it twice changes nothing the second time.** That is what makes it safe to run across 2000 modules and re-run after every rule change.

```
0  INVENTORY   list every asset by class (§39); hash every stylesheet and shared asset
1  READ        the whole module, all boards, before changing anything (§33)
2  LEDGER      build the colour ledger (§34) and the visual-model ledger (§36.4)
3  STRIP       delete every declaration that fails the §38.1 test
4  STRUCTURE   board background → transparent; margins → gap; assign a layout (Part 9)
5  TYPE        reclassify weight by category; snap sizes; strip families, italics, tracking
6  COLOUR      classify by function; map by role; run the reserved-colour guard
7  GEOMETRY    snap radius, border, gap
8  SHADOW      snap or strip
9  CONTENT     run the §36.5 accuracy audit on every visual — this is where Tier A lives
10 FIT         verify no board scrolls, with the chat panel open (§0.4, §7.6)
11 SCORE       compute Tier A count and Tier B score (§37.3)
12 RECORD      write the module record (§43.1); register every exception
```

**Steps 0–2 are read-only and must complete before step 3.** A normaliser that starts editing while still discovering the module will re-decide anchors mid-pass and produce a module that contradicts itself — this is exactly how the first pass on `Exponents Module` went wrong.

**Step 9 cannot be automated.** Everything above it can be. Route step 9 to a human or a reviewing agent with the module's ledgers in hand (§41.2).

### 40.1 Idempotency requirements

- Every decision that involved judgement is **written to the module record** (§43.1), and re-read on the next pass instead of re-decided.
- Snap functions are **pure** — same input, same output, no reference to the current rendering.
- A stripped declaration is recorded as stripped, so a later pass doesn't reinstate it from the source asset.
- Assert at the end of a second run: **zero diffs**. A non-zero diff means a snap function is unstable or a decision wasn't recorded.

## 41. Triage and routing at scale

2000 modules cannot all be hand-fixed. Route by **cost**, not by how bad it looks.

### 41.1 The four routes

| Route | Criteria | Who |
|---|---|---|
| **Auto** | Every finding is a snap-table entry or a strip | Normaliser, no review |
| **Assisted** | Auto, plus ≤ 3 findings needing a judgement call | Normaliser proposes, human confirms the 3 |
| **Consent** | Findings inside an asset owned elsewhere | §42 |
| **Rebuild** | Tier A that no override can reach: text in rasters, wrong visuals, dark boards baked into assets | Authoring queue, per Part 8 |

Report the split before starting. In a drifted library the Auto route typically covers most modules; concentrating effort on Rebuild is what actually moves the conformance number.

### 41.2 What must never be automated

- The §36.5 content-accuracy audit — a wrong visual looks fine to a linter.
- Choosing the primary referent (§34.2) — it is a pedagogy decision.
- The layout verdict (§35.1) — keep or replace the source layout.
- Deleting content to make a board fit (§7.6).

### 41.3 Batch order

Normalise in this order, because each stage makes the next cheaper:

1. **Shared assets first** — one shared SVG or simulation fixed removes the finding from every module that uses it.
2. **Then by author** — one author's habits are one set of snap decisions, and the per-author score gives them a feedback loop.
3. **Then by chapter** — so cross-module anchor conflicts (§43.2) surface as a set.
4. **Rebuilds last**, prioritised by module traffic.

### 41.4 The legacy skin

A quarantined module still has to ship. Give it a **named legacy skin**: the transparent canvas, Roboto, the ink and surface tokens applied at the board level, and its unreachable interior left alone.

The skin is a **holding state, not a tier** — it never becomes acceptable, it is never used for new content, and every module wearing it is on the rebuild queue with a reason recorded. Its purpose is that the library reads as one product while the backlog is worked, instead of one hard boundary per legacy module.

## 42. Ownership and consent across 30+ authors

§24's per-applet consent protocol does not scale to thousands of instances. Extend it:

- **Tier A needs no consent.** Fix and notify — the module is broken, and asking permission to unbreak it wastes a cycle. The notification names the rule and the fix.
- **Tier B is consented in batches.** One broadcast per author or vendor group listing every finding across all their assets, with the proposed diff, a **10-working-day window**, and a stated default (apply on silence). Thirty authors × one broadcast beats hundreds of individual requests, and gives each author one coherent view of their own drift.
- **A rule change re-opens nothing already consented.** When this document changes, the affected modules re-enter the queue via the drift check (§43.3), not by revoking earlier agreements.
- **Escalation is pedagogical, not aesthetic.** An author who refuses a Tier B change keeps the value and it is registered as an exception. An author who refuses a Tier A fix escalates to whoever owns the curriculum — never resolved by overriding them silently.
- **Author-facing output is the score plus the top three findings** (§37.3). "Your 14 modules score 62; your three most common findings are non-token violets, 6px radii, and coloured glows" changes future authoring. A list of 400 line-items does not.

## 43. Records, registry and re-runs

### 43.1 The module record

One per module, beside it, machine-readable. This is what makes the pass idempotent and the library auditable:

```
module:        G08C01M01
author:        <name>            source: <path>
pass:          2026-08-11        rules-version: <this doc's version>
state:         conformant | skinned | quarantined | blocked
tier-a:        0
tier-b-score:  94

assets:
  <path> ..... class: inline-svg    ceiling: full      state: normalised
  <path> ..... class: canvas-sim    ceiling: config    state: skinned

ledgers:
  colour ..... primary: exponent #7950f2 · secondary: base #e8590c · tertiary: result #1c7ed6
  model ...... array/tile, boards 6·7·12·19

decisions:                       # judgement calls — re-read, never re-decided
  primary referent ... exponent (§34.2: module title + 4/4 objectives)
  layout verdict ..... b03 replaced — source layout failed hierarchy (§35.1)
  §34.2a exception ... b03 comparison board, result token unused

stripped:                        # so a later pass does not reinstate them
  b04 .... coloured glow on formula card
  b09 .... panel gradient

exceptions:                      # registered debts, each with an owner and a reason
  b11 .... canvas sim, no token hook — owner notified 2026-08-04
```

### 43.2 The subject anchor registry

Anchors are per module, but a referent that recurs across a chapter **must keep one token throughout that chapter**. A student meeting "base" in orange in module 1 and violet in module 3 has been taught that colour means nothing.

- One registry per subject, listing every referent and its token.
- A module claims a token for a referent; the next module reuses it.
- A conflict is resolved in favour of the **earlier module in the learning sequence**, not the newer file.
- Across *different* subjects, reuse is fine — no student meets both in one lesson.

### 43.3 Drift detection and re-runs

- **On every rule change**, re-run steps 5–8 and 11 (the pure snap steps) across the library. They are deterministic, so this is cheap and needs no consent.
- **On every asset hash change**, the module re-enters the audit queue automatically (§39.2).
- **Sample continuously** — a random 2% of conformant modules re-scored each week catches regressions that a one-time pass cannot.
- **Never mark a module conformant without a record.** An unrecorded pass cannot be re-run, cannot be audited, and will be re-decided differently next time.

---
