<!-- Content Canvas Rules — v1.0 — 17 August 2026 — part file 6 of 13 -->

> **PART 4 — INTERACTIVE**
> 
> | | |
> |---|---|
> | **Owner** | Content Canvas — **feeds** |
> | **Domain** | Interaction & Affordance (7) |
> | **Governs** | Sliders, counters, other controls, answer boxes, buttons, feedback. |
> | **Loaded when** | A board carries a control the student operates. |
> | **Requires** | `00-contract.md` + `01-foundations.md` + `12-rules.md` |
> | **Version** | v1.0 — 17 August 2026 |

> **What this file does not decide.** Type steps, colours, radii, shadows, spacing, the layout
> contract, motion and state values are defined in `01-foundations.md` and cited here by `§`
> number. If a value you need is not in this file, it is there — do not infer it. `§` refers to
> sections (numbered 0–45); `R` refers to rules (numbered 1–120) in `12-rules.md`. Both numbering spaces are
> permanent: numbers are added, never reassigned.

---
# PART 4 — INTERACTIVE

## 18. Slider

**Reference implementation: `Slider System.dc.html`. It measures its own contrast at render time across every hue; trust it over any number written here.**

A slider invents **no new visual devices**. The track is a surface, the thumb is a button carrying the same flat base edge (§20.0.1) and spending it on grab, and every colour is generated from the anchor's hue angle (§3.7). That is what keeps five types looking like one control.

### 18.1 Anatomy

| Part | Spec |
|---|---|
| Track | **16px**, radius 999, `oklch(93% .06 h)` — a tint of the accent, never neutral grey |
| Fill | The traversed run, `base` (`48% .19 h`) |
| Notches | **2px**, full track height, at every **interior** stop. `oklch(72% .10 h)` unpassed, `oklch(80% .12 h)` passed |
| Thumb | **40px** circle, neutral face `oklch(96% .022 295)`, 4px base edge `oklch(78% .05 295)` |
| Counter | Fits its digits, 34px tall, radius 12, `base` fill, white 800, **tethered by a tail** |
| Tick labels | 15/700 below the track, active stop 800 in the hue's `text` |
| Inline label | `body`/700 left of the track, vertically centred, never above it |

**The bar leads and the thumb rides it.** A 44px thumb on a 12px track is top-heavy — the handle dominates the thing it moves along. The visual thumb is 40px; **the hit target stays 44px** via the input overlay, so the touch area never shrinks with the styling.

**The track wears the accent.** A grey track with a coloured fill reads as two objects that happen to overlap; one hue family reads as a single control with a filled part and an empty part — which is what it is.

**Markers cut through the bar, they never sit on it.** A dot resting on a track is neither a stop nor a division. A notch divides the bar into the parts being counted, which is usually the maths. Interior stops only — the bar's own ends already mark 0 and max.

**The counter is tethered.** A tail joins it to the thumb, and the chip fits its digits with 12px padding — it never floats free, and it never reserves width it is not using.

### 18.2 The five types

Two switches — **the scale** (none / markers / markers + labels) and **the counter** (off / on) — closed by one rule:

> **The value is shown once** — as labels, or as a counter, never both. Two readouts of the same number make the student check which one to believe.

That rules out the sixth combination and leaves exactly five:

| # | Type | Use when |
|---|---|---|
| 1 | Plain | Continuous, and the value is not the point — an explode-view from 0 to 1. The object it drives is the feedback |
| 2 | Markers | Discrete, few stops. The student counts divisions and reads the value off the object |
| 3 | Markers + labels | Discrete, and the scale itself must be readable — here the labels **are** the readout |
| 4 | Plain + counter | Continuous and the value matters. The counter is the only readout, so it never hides |
| 5 | Markers + counter | Discrete, value matters, but the individual stops need no naming |

**The value is always reachable.** The counter shows it, the labels name it, or the object the slider drives makes it obvious. A slider whose value is nowhere teaches nothing.

**Discrete means notches.** If the input snaps, the divisions are drawn. Above 12 stops drop them — they become texture — and use a counter instead (type 4).

### 18.3 The three states

| State | Treatment |
|---|---|
| Default | As §18.1 |
| Highlighted | The row sits on a plate in `fill2` with `inset 0 0 0 3px` at `base`; row label to 800 |
| Disabled | Achromatic — track `#f1f3f5`, fill `#c9ced4`, notches `#9aa0a6`, thumb edge shortened to **3px with no travel** |

**Highlighted is the surface's own highlighted state** (§20.0.2), not a new device — so it works identically for all five types. The slider itself never changes, and **siblings are never dimmed to fake it**. One highlighted slider per board; two is none.

**Losing the depth is how disabled says "not yet."** Geometry is kept and the control is never hidden — removing it reflows the board.

**Disabled keeps the value legible.** Its *control label* may dim, because an inactive control is WCAG-exempt. Its **tick labels and counter may not** — those are the value, not the control (§20.0.2).

### 18.4 Layout

- Label left of the track, vertically centred, never above it.
- Track length 320 min, 480 max; vertical 240–360.
- **Tick labels clear the thumb, not the track.** The thumb plus its base edge reaches 32px below the track top, so a label row tucked under the track sits beneath it — and it strikes the *active* stop, the one the student is reading.
- End labels carry the unit if there is one, and so does the counter. Never a bare number where a unit exists.

## 18a. Counter

**Reference implementation: `Counter System.dc.html`. It measures its own contrast at render time across every hue; trust it over any number written here.**

A counter is **two buttons and one surface** — nothing new. Same 20px radius, same flat base edge (§20.0.1), same generated hue (§3.7).

### 18a.1 Anatomy

| Part | Spec |
|---|---|
| Value | 72×96 min, radius 20, `oklch(88% .155 h)`, numeral `figure` 38/800 in `deep`, `tabular-nums` |
| Lift | `0 5px 14px -9px rgba(70,46,146,.4)` — a soft ambient shadow, **never a base edge** |
| Minus / plus | 56px buttons, radius 20, 4px base edge, glyph in the hue's `text` |
| Glyphs | **4px rounded bars** at 22px — never an icon stroke |
| Shell | Optional, radius 20, `fill` tint, `12px 16px` padding |

**The value always leads**, and it leads *by hierarchy, never by volume*: larger, one step darker, lifted. A saturated tile shouts on a board whose subject is elsewhere, and this element appears on every counter, so it sets the room's volume.

**Loud buttons around a plain number are forbidden** — that makes the student read the controls before the quantity, which is backwards on a board about the quantity.

**One hue family, no grey.** A button's face is always one step lighter than whatever it sits on — the accent's `fill` when bare, white on a shell — and its edge derives from the same hue. Grey handles beside a tinted value tile read as two unrelated controls that happen to be adjacent.

**The value is a surface**: read, never pressed, so it carries no base edge — that would make it look tappable.

**Glyphs are bars, not icons.** A 1.5px icon stroke disappears at classroom distance on a control meant to be used quickly.

### 18a.2 The two types

One switch — **the shell** — because the value always leads, so there is no second axis.

| # | Type | Use when |
|---|---|---|
| 1 | Bare | The counter stands alone on the board. Buttons take the accent's `fill` tint |
| 2 | Held | A `fill` shell groups the three into one object. Buttons go **white** — always one step lighter than what they sit on. Use when the counter shares a board with other controls |

### 18a.3 The three states

| State | Treatment |
|---|---|
| Default | As §18a.1 |
| Highlighted | The shell becomes a plate in `fill2` with `inset 0 0 0 3px` at `base` |
| Disabled | Achromatic — value `#c9ced4`, buttons `#f1f3f5`, edges 3px with **no travel**, lift removed |

**A bare counter grows a shell when highlighted** — the one case where a plate appears from nowhere, because a highlight has to enclose something.

**Disabled keeps the value legible.** Glyphs may dim (inactive controls are WCAG-exempt); the numeral may not — it is the value, not the control (§20.0.2).

### 18a.4 Limits and sizing

- **At a floor or ceiling, one button disables — never the counter.** Disabling wholesale tells the student they broke it; one flat button tells them which way is still open.
- **The value never resizes.** A minimum width sized for the largest value in range, `tabular-nums`. A counter that widens from `9` to `10` shifts everything beside it.
- **One counter per board carries the accent.** A second competes with the first for the same job.

## 19. Other controls

| Control | Spec |
|---|---|
| Option row | Row + 32px letter badge; `2px` accent border when selected |
| Media option | `media-square` + letter badge top-left on a scrim |
| Numeric input | See §19a — an answer box is its own component, not a row entry |
| Toggle | Track 44×24 radius 999; knob a **20px-diameter** circle. The knob is a button (§20.0) and carries its base edge |
| Stepper | See §18a — a counter is its own component, not a row entry |
| Drag token | Radius 20, neutral face, 4px base edge — it is a button that happens to move |
| Drop zone | 1.5px dashed `#adb5bd`, radius 12, tint fill on hover |
| Match pair | Two columns of rows; 2.5px accent connector once linked |
| Hotspot | 32px circle, accent at 40%, pulses once on board entry |

Minimum hit target **44px**. Every control has a visible resting state — nothing is discoverable only by hovering, because there is no hover on tablet.

## 19a. Text & answer boxes

The control a student touches most, and it had one line of spec. Every state is defined here, because an undefined state is an invented one.

| Part | Spec |
|---|---|
| Box | Radius 20, `#fff`, 1px `#e9ecef`, min 44px tall |
| Width | Sized to the **expected answer length** — 3 units per character, min 88, max 320. A full-width box for a two-digit answer tells the student the answer is long |
| Value | `figure` 44/800 `#212529` when numeric, `body` 24/500 when prose. Centred for numeric, left-aligned for prose |
| Placeholder | Never a hint or an example answer. Either empty, or a `label` naming the unit |
| Unit | **Outside** the box, `label` 16/700 `#868e96`, 8 units right — never inside, never typed by the student |
| Caret | Accent |

| State | Treatment |
|---|---|
| Resting | As above |
| Focused | 2px accent border. No glow, no shadow change, no size change |
| Filled | 1px `#e9ecef` — the value carries the weight |
| Correct | 2px `#40c057`, fill `#ebfbee`, `ti-check` **outside** the box, right |
| Wrong | 2px `#e03131`, fill `#fff5f5`, `ti-x` outside, right. **The student's value stays** — clearing it removes the thing they need to look at |
| Disabled | `#f1f3f5` fill, `#adb5bd` value, 1px `#e9ecef` |

**An answer box never shakes, flashes or pulses on a wrong answer.** The border and the icon are the signal; motion on failure reads as punishment.

## 20. Buttons

| Kind | Style | Use |
|---|---|---|
| Primary | `base` fill at the board's anchor angle, white 800, radius 20, `20px 34px`, 5px base edge (§20.0.1) | Check, Continue, Start |
| Secondary | Neutral face `oklch(96% .022 295)`, radius 20, `#212529` 800, 4px neutral base edge | Hint, Show steps, Try again |
| Ghost | transparent, accent 16/700, no edge — the only button without depth | Reveal, Expand |
| Text link | `#868e96` 16/700, underline 3px offset | Skip |

**Labels are sentence case** — "Check answer", "Plot integers". Never `YES` / `NO` / `SAME OR DIFFERENT?`; uppercase belongs to the `label` step only (§2.1).

### 20.0 Surfaces and buttons — the two shape families

**Reference implementation: `Shape System.dc.html`, which measures its own contrast at render time.** This section supersedes the earlier per-component geometry: everything that holds content or is pressed is one of these two families, and nothing else exists.

One base shape — the rounded rectangle at **20px radius**, for both — and both **fit to content**. Radius therefore carries no meaning. **Depth does.**

**One carve-out: the slider thumb is a circle** (§18). It is a button in every other respect — same face, same base edge, same press travel — but it slides continuously along a track, and a rounded rectangle reads as a thing that occupies *positions*. The shape has to say "this moves freely", which only a circle does. Nothing else in either family is exempt.

| | Surface | Button |
|---|---|---|
| Sits | Flat on the page | Raised on a solid edge |
| Fill | `fill` at rest | Face + `edge` beneath it |
| Stroke | **None at rest** | None |
| Padding | `18 / 26` | `20 / 34`, min height 64 |
| Label | 700, hue's `text` | 800 |
| Pressed | — | Face travels down by the edge height |

**Why depth and not radius.** It reads at any size, in greyscale, to any age, at a glance — a pill-vs-rectangle distinction does not survive being scaled into a diagram, and a border-weight distinction does not survive a screenshot.

#### 20.0.1 The base edge — a sanctioned exception to §8a.5

§8a.5 bans bevels. **A button's base edge is not a bevel and is required**, and the distinction is exact:

- A **bevel** fakes three dimensions on a static surface with a gradient body, a lit top face and an inner highlight. It decorates. Still banned, everywhere.
- A **base edge** is a *flat solid offset* — `box-shadow: 0 5px 0 <edge>` — in the face's own hue at `L 36%`. No blur, no gradient, no highlight. It encodes the interaction: **pressing spends it.** The face translates down by exactly the edge height and lands level with the page, then returns.

That travel *is* the affordance, and for a 10–14 audience it is the single most legible "this can be pressed" signal available. Nothing else about a press changes — no scale, no bounce, no colour flash.

#### 20.0.2 Surface — four states

A surface is never pressed, so it has no selected state.

| State | Treatment |
|---|---|
| Default | `fill` alone |
| Highlighted | `inset 0 0 0 3px` at `base` — **inset**, so the shape does not grow and nothing reflows |
| Negative | The wrong arc (25°) used as itself |
| Disabled | `#f1f3f5` fill, label stays `#495057` |

**The stroke appears in exactly one state.** That is what makes it mean something — and it is why a surface carries no border at rest.

**Disabled removes colour, never legibility.** A surface still carries a term the student must read, so its label stays ink; only a *button* may dim its label, and only because an inactive control is WCAG-exempt.

#### 20.0.3 Button — six states

| State | Face | Edge | Label |
|---|---|---|---|
| Default | neutral `96% .022 295` | `78% .05 295` | ink |
| Highlighted | `base` | `edge` | white |
| Selected | `fill` | `edge` | `text` |
| Correct | `fill 145°` | `edge 145°` | `text 145°` + `ti-check` |
| Wrong / negative | `fill 25°` | `edge 25°` | `text 25°` + `ti-x` |
| Disabled | `#f1f3f5` | `#dfe3e7`, **3px, no travel** | `#adb5bd` |

- **Correct and wrong are one state each, shared with negative.** They appear only after an answer is judged — never as a selection, never as an anchor.
- **Selected is a tinted face, never a solid one** — a solid fill collides with the judged states, so the student reads "I chose this" as "I got it right".
- **Losing the travel is how disabled says "not yet."**
- **The outcome icon lives in a reserved slot outside the face**, present in every state, so no state is wider than another (§19a).

#### 20.0.4 Choice groups

Every option in a group is **identical at rest** — same width, same face, same edge, same weight. Nothing may hint at the answer before it is judged: an option styled differently from its siblings has told the student the answer before they thought about it.

An answer option is a **button**, not a surface. Its label is 800 like any button; what keeps it from reading as a call to action is the neutral face, not a lighter weight.
| Disabled | `#f1f3f5`, `#adb5bd`, 1px `#e9ecef` |
| Correct / wrong | §21 |
| Group | One row, `gap-inner`, equal widths. Max 4 |

Three rules that the found examples all broke:

1. **Every option in a group looks identical when resting.** A green "Natural numbers" pill beside two plain text labels tells the student which one is the answer before they think.
2. **Selection is a border and a tint, never a fill colour change.** A green-filled selected option collides with `correct` (§34.1), so the student reads "I chose this" as "I got it right" — before the answer is judged.
3. **No option is emphasised by an `attention` ring.** Attention points at *where to act*, and in a choice group that is the whole group.

| Icon | 44px, radius 20, transparent, `#6b6580` 20px | Audio, flag |

**One primary per board.** Action row at the board bottom, `gap-inner`, primary rightmost. Hint is always secondary — it must never compete with Check.

**Banned on every button, without exception:** gradient fills · text shadow · a lit top face or inner highlight · outer glow that is not `attention` (§8a.3) · a drawn hand or pointer beside it · scale or bounce on press. The flat base edge of §20.0.1 is the one form of depth a button carries, and its travel is the entire press.

### 20.1 Hint pattern
A two-state secondary button, never a modal:

- Collapsed: secondary button, `ti-bulb` + "Hint".
- Expanded: replaced **in place** by a tint panel (`#fff4e6`, radius 12, `14px 16px`), text 24/500, `ti-bulb` 20px `#e8590c`.

Max **two** hints per board, revealed in order, never automatically.

### 20.2 Option-set hygiene

The visual properties of an option set leak the answer. Five rules, all mechanically checkable:

- **Options are within ±20% of each other's length.** The longest option is the correct one far more often than chance, and students learn that before they learn the maths.
- **The correct option's position is uniform across a module.** Count them: if the answer is third on five boards of eight, re-order.
- **No `All of the above` / `None of the above`** — they test reading, not the concept.
- **Options are parallel in form** — all numbers, all phrases, or all diagrams. A single odd-form option is either obviously right or obviously wrong.
- Distractors carry the **predictable misconception** for that skill (the additive reading of an exponent, the un-simplified fraction), so a wrong answer is diagnostic rather than random.

## 21. Feedback

- **Correct:** row border → 2px `#40c057`, fill `#ebfbee`, text `#2b8a3e`, `ti-check` badge, ring pulse once.
- **Wrong:** row border → 2px `#fa5252`, fill `#fff5f5`, text `#e03131`, `ti-x` badge. **No shake, no buzz.**
- The correct row is always revealed alongside a wrong answer.
- Explanation appears below the options as a tint panel, 24/500.
- Never disable retry without showing the answer.

---

---
