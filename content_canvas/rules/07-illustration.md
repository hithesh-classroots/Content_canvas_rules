<!-- Content Canvas Rules — v1.0 — 17 August 2026 — part file 8 of 13 -->

> **PART 6 — ILLUSTRATION & GRAPHICS**
> 
> | | |
> |---|---|
> | **Owner** | Content Canvas — **feeds** |
> | **Domain** | Making Stills from Assets (10) |
> | **Governs** | Illustration vs diagram vs photo, flat vector style, the extended hue palette. |
> | **Loaded when** | An illustration or vector graphic is being made. |
> | **Requires** | `00-contract.md` + `01-foundations.md` + `12-rules.md`. Also cites `02-content-components.md` (§9), `03-data-maths-diagrams.md` (§16–17) and `05-interactive.md` (§19–20) |
> | **Version** | v1.0 — 17 August 2026 |

> **What this file does not decide.** Type steps, colours, radii, shadows, spacing, the layout
> contract, motion and state values are defined in `01-foundations.md` and cited here by `§`
> number. If a value you need is not in this file, it is there — do not infer it. `§` refers to
> sections (numbered 0–45); `R` refers to rules (numbered 1–120) in `12-rules.md`. Both numbering spaces are
> permanent: numbers are added, never reassigned.

---
# PART 6 — ILLUSTRATION & GRAPHICS

## 30. Illustration vs diagram vs photo

Three different things, three different rule sets. Choosing wrongly is the most common graphics mistake.

| | Illustration | Diagram | Photo |
|---|---|---|---|
| Purpose | Make an abstract idea concrete or a board welcoming | Carry measurable, checkable information | Show a real object or place |
| Accuracy | Stylised; proportion is expressive | **Exact** — a wrong angle teaches a wrong fact | Literal |
| Rules | This part | §16–17 | §9 |
| Palette | Extended hues (§32) | Semantic accents only | n/a |

**Never illustrate a diagram.** If a student could measure it, read a value off it, or be marked wrong because of it, it is a diagram: it follows §16–17, uses only semantic accents, and carries real geometry.

**When to illustrate:** an abstract process with no photographable form (a fraction being split, a force, a flow) · an empty or waiting state · a mascot's props and scenery · a decorative section divider.

**When not to:** a real object a photo shows better · anything demanding factual accuracy (maps, anatomy, apparatus) · anything that exists as a real asset already. Use `MEDIA[...]` with a placeholder and request the asset.

## 31. Flat vector style

The house style is **flat, geometric, two-tone**. Built from primitives, no rendering tricks.

### 31.1 Construction

- **Primitives only** — circles, rounded rectangles, triangles, arcs, simple paths. If it can't be built from those, it's too detailed for this system.
- **Two stops per form, maximum:** the hue's `base` for the lit faces, its `deep` stop for the turned-away plane. The `light` stop is available only as a *background plane behind* the subject, never as a face of it (§32.1). That is the entire shading model.
- **No gradients.** No mesh, no radial, no linear. A gradient is the fastest way to make a flat set look inconsistent.
- **No drop shadows, no glows, no bevels, no inner shadows, no noise or texture.** Separation comes from the `deep` stop or from a gap.
- **No specular highlights.** No white blobs on spheres.
- **Implied light from the top-left** — so `deep` always falls bottom-right. Consistent across every illustration in a module.
- **Flat projection only.** Never isometric, never perspective, never a vanishing point. The one exemption is a *technical diagram* of a solid (§16c) — which is a diagram, not an illustration (§30).

### 31.2 Geometry

| Property | Value |
|---|---|
| Grid | `viewBox="0 0 100 100"` (or 24 for icon-scale), integers where possible |
| Corner radius | 2–8 user units; nothing razor-sharp unless the subject demands it |
| Outline | None by default. When needed: 2.5 units in the hue's `deep` stop |
| Caps & joins | `round` everywhere |
| Minimum stroke | 1.5 units — thinner disappears when the board scales |
| Minimum shape | 6 units — smaller reads as dirt |

### 31.3 Colour discipline

- **Max 4 hues per illustration**, plus neutrals. **These four are the board's four** (§3.8, rule 5) — an illustrated board has no extra hue budget. If the illustration uses four, the rest of the board is neutrals.
- **The dominant hue is the board's semantic accent**, so the illustration belongs to its board rather than floating on it. **An anchored token never lands on a decorative element** (§34.5): if the board's accent is bound to a referent, the illustration wears it only on the part that depicts that referent.
- The other hues are supporting and decorative — they must carry **no meaning**.
- **Never** use `correct` green or `wrong` red decoratively in an illustration — they are **not in the extended palette at all** (§32), and they are reserved to every scheme on the canvas (§3.8). Those two hues mean something here, and a green leaf next to a wrong answer is a genuine misread. An illustration needing a green takes **teal** or **lime**; one needing a red takes **pink** or **orange**.
- Neutrals for structure: `#f8f9fa` (light plane) · `#ced4da` (mid) · `#495057` (line/deep).

### 31.4 Figures & faces

Match the mascot language — minimal, never realistic:

- Eyes are dots or short arcs. **No pupils with highlights, no eyelashes.**
- One curve for a mouth; a nose only if the silhouette needs it.
- Limbs are rounded rectangles with round caps; hands are circles.
- Bodies are primitives — no anatomy.
- **Skin tones** (use the full range across a module, never one):
  `#ffd8b1` · `#f0b98c` · `#c68863` · `#8d5524` · `#5c3317`
- Hair, clothing and props take extended hues.

### 31.5 Output

- **Inline SVG.** No embedded raster, no `<image>`, no external references.
- `currentColor` for anything that should inherit ink.
- `aria-hidden="true"` when decorative; a real `<title>` when it carries meaning.
- No `<style>` blocks inside the SVG — attributes or inline `style` only.
- Budget: **under 8KB** per illustration. Past that it is over-detailed for this style.
- Strip editor cruft — no `id` soup, no `data-name`, no empty groups.

### 31.6 What the found library got wrong

The violations that recur most, stated so a reviewer can name them:

- **Two stroke weights per illustration, maximum** — one structural (2.5 units), one detail (1.5 units), both per §31.2. A book outline at 2.5 units beside its content bars at 6 reads as two drawings.
- **No 3D, no isometric, no highlights.** An orange box drawn with a lit top face, a gradient body and a rim highlight is a rendering, not an illustration. Flat faces, flat fills (§31.1). Isometric belongs to technical diagrams of solids and nothing else (§16c, R47).
- **No inner glow.** A warm radial bloom inside a shape is a glow (§8a.3) and is stripped.
- **No display or cartoon font in an illustration.** Text inside a graphic uses the system stack at a canvas step, like every other string.
- **Green ticks are the one exception to the green ban** (§31.3). A `ti-check` may be `#40c057` — the `correct` token used as a *state signal*, not as decoration — because a tick *is* a completion signal. The **box around it is not** — it stays `#e9ecef`, and an unchecked box is `#dee2e6` with no fill (§8a.2 `complete`).
- **Illustrated controls follow the real control's spec.** A drawn checkbox, slider or button in a graphic uses §19/§20 geometry — otherwise the student learns one visual language from the picture and meets another in the interaction.

### 31.7 The dark room

An illustration is a **palette resolution like everything else** (§3.1a, `design-system.md §5`) — same viewBox, same geometry, same stops; only the palette moves. A drawing that hardcodes the light-room values above has silently chosen a room.

- **Structural neutrals are roles, not the greys in §31.3** — light plane → `surface2`, mid → `line2`, line/deep → `dim`.
- **A `light` background plane becomes an alpha tint of the same hue**, never the pale hex. A pale plate on `#1a1526` glows, and it is the exact class the audit in `design-system.md §5.7` exists to catch.
- **`base` and `deep` resolve through the ladder** (§3.7), measured against `surface #262038` — ≥3:1 for any shape that carries meaning.
- **Skin tones resolve through the same ladder.** The five stops in §31.4 are the light-room column only.
- **`currentColor` needs no treatment** — it already inherits the room's ink, which is why §31.5 prefers it.

**The measured dark column for the ten hues and the five skin tones is owed to this section and is not yet written.** Until it is, an illustration on a dark board is a Tier B finding (§37) — not a licence to hardcode a light-room hex.

## 32. Extended hue palette

**For illustration only.** These are decorative; they never signal state, and they never appear in text, borders, controls, charts or diagrams — those use §3.2 exclusively.

| Hue | `light` (tint) | `base` (fill) | `deep` (shade) |
|---|---|---|---|
| Pink | `#ffdeeb` | `#f06595` | `#a61e4d` |
| Grape | `#f3d9fa` | `#cc5de8` | `#862e9c` |
| Violet | `#e5dbff` | `#7950f2` | `#5f3dc4` |
| Indigo | `#dbe4ff` | `#4c6ef5` | `#3b5bdb` |
| Blue | `#d0ebff` | `#228be6` | `#1864ab` |
| Cyan | `#c5f6fa` | `#15aabf` | `#0b7285` |
| Teal | `#c3fae8` | `#12b886` | `#087f5b` |
| Lime | `#e9fac8` | `#82c91e` | `#5c940d` |
| Yellow | `#fff3bf` | `#fcc419` | `#e67700` |
| Orange | `#ffe8cc` | `#fd7e14` | `#d9480f` |

**Ten hues.** `correct` green and `wrong` red are **not in this palette** — they are state, permanently (§3.1, §3.8, §34.1). An illustration needing a green takes **teal** or **lime**; one needing a red takes **pink** or **orange**. All ten are Mantine hue scales (shades 1 / 6 / 9), so they sit with the rest of the product rather than beside it.

### 32.1 Using the palette

- **`light`** — background planes *behind* the subject, and negative space enclosed by it. Never a face of the subject itself (§31.1).
- **`base`** — the subject. The one hue a viewer would name.
- **`deep`** — the turned-away plane and outlines. **Not text.** Text inside an illustration follows §3.2 and the three inks (§3.1); text sitting on a `base` fill takes white in the light room and `canvas` ink in the dark room (§3.1a, rule 1).
- **A hue's three stops always travel together.** Never mix one hue's `base` with another's `deep` on the same form.
- **Yellow and lime `base` fail as thin lines** — `#fcc419` is 1.7:1 on white. Use them as fills only; their `deep` stop for anything linear. Neither is ever a text colour — no extended hue is (§32.1, `deep`).

### 32.2 Recommended pairings

Four hues, one dominant, **each at a stated stop**. These read well and stay distinguishable in greyscale. Each set is one of the sanctioned schemes (§3.8) resolved for illustration — not a new combination:

| Set | Hues | Scheme (§3.8) | Feels |
|---|---|---|---|
| Concept | violet `base` · indigo `light` · cyan `base` · yellow `light` | Analogous run | The default. Matches the canvas |
| Warm | orange `base` · pink `base` · yellow `light` · grape `light` | Triad + neutrals | Energetic, celebratory |
| Cool | blue `base` · cyan `light` · teal `deep` · lime `light` | Analogous run | Calm, scientific |
| Earth | orange `base` · lime `light` · teal `deep` · deep neutrals | Triad + neutrals | Geography, biology |

Never more than four. **Adjacent hues only at different stops** (§3.8, rule 3) — violet with indigo, blue with cyan, cyan with teal are legal at different stops and **never both at `base`**. At the same stop they read as one colour at board scale.

---
