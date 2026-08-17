<!-- Content Canvas Rules — v1.0 — 17 August 2026 — part file 8 of 13 -->

> **PART 6 — ILLUSTRATION & GRAPHICS**
> 
> | | |
> |---|---|
> | **Owner** | Content Canvas — **feeds** |
> | **Domain** | Making Stills from Assets (10) |
> | **Governs** | Illustration vs diagram vs photo, flat vector style, the extended hue palette. |
> | **Loaded when** | An illustration or vector graphic is being made. |
> | **Requires** | `00-contract.md` + `01-foundations.md` + `12-rules.md` |
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
| Palette | Extended hues (§31) | Semantic accents only | n/a |

**Never illustrate a diagram.** If a student could measure it, read a value off it, or be marked wrong because of it, it is a diagram: it follows §16–17, uses only semantic accents, and carries real geometry.

**When to illustrate:** an abstract process with no photographable form (a fraction being split, a force, a flow) · an empty or waiting state · a mascot's props and scenery · a decorative section divider.

**When not to:** a real object a photo shows better · anything demanding factual accuracy (maps, anatomy, apparatus) · anything that exists as a real asset already. Use `MEDIA[...]` with a placeholder and request the asset.

## 31. Flat vector style

The house style is **flat, geometric, two-tone**. Built from primitives, no rendering tricks.

### 31.1 Construction

- **Primitives only** — circles, rounded rectangles, triangles, arcs, simple paths. If it can't be built from those, it's too detailed for this system.
- **Two stops per shape, maximum:** the hue's `base` for the form, its `deep` stop for the turned-away plane. That's the entire shading model.
- **No gradients.** No mesh, no radial, no linear. A gradient is the fastest way to make a flat set look inconsistent.
- **No drop shadows, no glows, no bevels, no inner shadows, no noise or texture.** Separation comes from the `deep` stop or from a gap.
- **No specular highlights.** No white blobs on spheres.
- **Implied light from the top-left** — so `deep` always falls bottom-right. Consistent across every illustration in a module.
- **Flat or 2D-isometric projection.** Never true perspective, never vanishing points.

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

- **Max 4 hues per illustration**, plus neutrals.
- **The dominant hue is the board's semantic accent**, so the illustration belongs to its board rather than floating on it.
- The other hues are supporting and decorative — they must carry **no meaning**.
- **Never** use `correct` green or `wrong` red decoratively in an illustration. Those two hues mean something on this canvas, and a green leaf next to a wrong answer is a genuine misread.
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

- **Two stroke weights per illustration, maximum** — one structural, one detail. A book outline at 6px beside its content bars at 10px reads as two drawings.
- **No 3D, no isometric-with-gradients, no highlights.** An orange box drawn with a lit top face, a gradient body and a rim highlight is a rendering, not an illustration. Flat faces, flat fills (§31.1).
- **No inner glow.** A warm radial bloom inside a shape is a glow (§8a.3) and is stripped.
- **No display or cartoon font in an illustration.** Text inside a graphic uses the system stack at a canvas step, like every other string.
- **Green ticks are the one green exception.** A `ti-check` may be `#40c057` because a tick *is* a completion signal. The **box around it is not** — it stays `#e9ecef`, and an unchecked box is `#dee2e6` with no fill (§8a.2 `complete`).
- **Illustrated controls follow the real control's spec.** A drawn checkbox, slider or button in a graphic uses §19/§20 geometry — otherwise the student learns one visual language from the picture and meets another in the interaction.

## 32. Extended hue palette

**For illustration only.** These are decorative; they never signal state, and they never appear in text, borders, controls, charts or diagrams — those use §3.2 exclusively.

| Hue | `light` (tint) | `base` (fill) | `deep` (shade) |
|---|---|---|---|
| Red | `#ffe3e3` | `#fa5252` | `#c92a2a` |
| Pink | `#ffdeeb` | `#f06595` | `#a61e4d` |
| Grape | `#f3d9fa` | `#cc5de8` | `#862e9c` |
| Violet | `#e5dbff` | `#7950f2` | `#5f3dc4` |
| Indigo | `#dbe4ff` | `#4c6ef5` | `#3b5bdb` |
| Blue | `#d0ebff` | `#228be6` | `#1864ab` |
| Cyan | `#c5f6fa` | `#15aabf` | `#0b7285` |
| Teal | `#c3fae8` | `#12b886` | `#087f5b` |
| Green | `#d3f9d8` | `#40c057` | `#2b8a3e` |
| Lime | `#e9fac8` | `#82c91e` | `#5c940d` |
| Yellow | `#fff3bf` | `#fcc419` | `#e67700` |
| Orange | `#ffe8cc` | `#fd7e14` | `#d9480f` |

All twelve are Mantine hue scales (shades 1 / 6 / 9), so they sit with the rest of the product rather than beside it.

### 32.1 Using the palette

- **`light`** — background planes, large fills, negative space inside a form.
- **`base`** — the subject. The one hue a viewer would name.
- **`deep`** — the turned-away plane, outlines, and any text on a `base` fill.
- **A hue's three stops always travel together.** Never mix one hue's `base` with another's `deep` on the same form.
- **Yellow and lime `base` fail as text or thin lines** — `#fcc419` is 1.7:1 on white. Use them as fills only; their `deep` stop for anything linear.

### 32.2 Recommended pairings

Four hues, one dominant. These read well and stay distinguishable in greyscale:

| Set | Hues | Feels |
|---|---|---|
| Concept | violet · indigo · cyan · yellow | The default. Matches the canvas |
| Warm | orange · pink · yellow · grape | Energetic, celebratory |
| Cool | blue · teal · cyan · lime | Calm, scientific |
| Earth | orange · lime · teal · deep neutrals | Geography, biology |

Never more than four. Never two adjacent hues as the two most prominent (indigo + violet, cyan + teal) — they read as one colour at board scale.

---
