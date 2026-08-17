<!-- Content Canvas Rules — v1.0 — 17 August 2026 — part file 1 of 13 -->

> **PART 0 — THE CONTRACT**
> 
> | | |
> |---|---|
> | **Owner** | Content Canvas — **owns outright** |
> | **Domain** | Canvas & Surface Design (8) |
> | **Governs** | Every board, every job. The seven non-negotiables. |
> | **Loaded when** | Never. Always loaded. |
> | **Requires** | `00-contract.md` + `01-foundations.md` + `12-rules.md` |
> | **Version** | v1.0 — 17 August 2026 |

> **What this file does not decide.** Type steps, colours, radii, shadows, spacing, the layout
> contract, motion and state values are defined in `01-foundations.md` and cited here by `§`
> number. If a value you need is not in this file, it is there — do not infer it. `§` refers to
> sections (numbered 0–45); `R` refers to rules (numbered 1–120) in `12-rules.md`. Both numbering spaces are
> permanent: numbers are added, never reassigned.

---
# PART 0 — THE CONTRACT

Five non-negotiables. Everything else in this document is subordinate to these.

## 0.1 The canvas is transparent

**No board ever paints a background.** The 16:9 frame sits on the room's own surface — the lavender→cream gradient plus its dot lattice, ambient blobs, and answer-feedback light leak — and the board must let all of it through.

```css
/* every board root */
background: transparent;
```

Consequences that are easy to get wrong:

- **No white board fills, no tints, no gradients at board level.** A board-level fill hides the room's ambient light and breaks the answer-feedback leak, which is painted *behind* the canvas and depends on being visible through it.
- **No dark boards.** Ever. There is no dark surface anywhere in the canvas system, which is also why white ink is banned.
- **Surfaces are local, never global.** A card, a row, a tint panel — these are small, deliberate, opaque islands *on* the transparent board. If a surface spans the full board, it is a background, and it is wrong.
- **Opaque, not alpha, for local surfaces.** Use `#ffffff`, not `rgba(255,255,255,.8)`. Alpha surfaces let the dot lattice show through the card and make text muddy.
- **Test on all three:** the top of the gradient (`#eee9fd`), the middle (`#f8f5fe`), and the bottom (`#fdfaf0`). A board must read on all of them.

## 0.2 The design canvas is 1600 × 900

Author at **1600 × 900 units**; the room scales the whole board to fit.

**Two scales exist, and confusing them is the most common authoring error.** Every size in Parts 1–4 is a **rendered** value — what it measures on a ~924px-wide board. At the 1600-unit authoring scale, multiply by **1.73**:

| Token | Rendered | Authored (×1.73) |
|---|---|---|
| `hero` | 48 | 83 |
| `title` / `statement` | 36 | 62 |
| `body` | 24 | 42 |
| `label` | 16 | 28 |
| `figure` | 44 | 76 |
| `micro` | 12 | 21 |
| gaps 8 / 14 / 20 / 26 / 40 | — | 14 / 24 / 35 / 45 / 69 |
| board padding `24 34 20` | — | `42 59 35` |
| chip-variant top 44 | — | 76 |
| radii 8 / 12 / 16 | — | 14 / 21 / 28 |
| border 1px · selected 2px | — | **2px · 4px** |
| measure 560 / 720 / 820 | — | 969 / 1246 / 1419 |

**Hairlines are the trap:** a literal `1px` border at authoring scale renders at 0.58px and disappears on some displays. Use **2px** authored for a 1px rendered hairline.

A board authored at render scale (≈924 wide) uses the rendered column directly. Pick one scale per file and never mix.

## 0.3 A board holds one idea

One idea, one layout, one primary action. If a board needs "and also", it is two boards.

## 0.4 A board never scrolls

`scrollHeight === clientHeight`, measured **with the chat panel open** (the board is ~63% width then, and text wraps). §7.6 gives the fix order.

## 0.5 Colour is never the only signal

Every state carried by colour is also carried by weight, an icon, or a shape. ~8% of students cannot separate the correct-green from the wrong-red.

## 0.6 Every board has exactly one focal point

**A board with nothing highlighted has not decided what it is about.** Every board carries exactly one element in `emphasis` — a term, a number, a region or a figure — and that element is traceable to one of the module's key takeaways (§34a).

Not one *per region*, not "at least one": **one**. Two focal points are two boards.

The converse is the sharper half: **if no element on a board deserves the accent, the board has no claim — cut it or merge it.** Colour is never added to relieve blandness; it is placed on the thing the board exists to say. A board that cannot name that thing is a board with nothing to teach.

## 0.7 Nothing ships unchecked

Every rule below this line describes a board that is *right*. **None of them detects a board that is wrong** — and a rule nothing evaluates is a preference. This is the gate.

**Twelve checks, run per board, before it ships.** They are ordered so an early failure makes the later ones moot. Any failure in group A or B is Tier A (§23) and blocks the board; group C is fixed in the same pass.

**A · Does it hold together**

1. **Nothing overlaps** — §7a.1. Measure it; do not eyeball it.
2. **It does not scroll** — `scrollHeight === clientHeight`, with the chat panel open (§0.4).
3. **It is at least half full** — content occupies ≥ 55% of the safe area's height (§7a.2). Four kinds invert this with a ceiling instead: `divider` 40%, `feedback` 50%, `intro` and `section` 60%.
4. **One gap value, optically centred** — §7a.3.

**B · Does it say one thing**

5. **Exactly one focal point, and you can name the takeaway it serves** (§0.6, §34a.2). Zero is an undecided board; two is two boards.
6. **Within the band's ceilings** — words, elements, steps (§2.6). The word count is of words held *simultaneously*; one continuous passage counts as one element instead (§2.6a).
7. **Nothing below the `muted` floor carries information** a student needs (§3.6).
8. **Every state is one of the ten**, applied from the matrix rather than invented (§8a.1).

**C · Is it in the system**

9. **Every colour** comes from a hue angle (§3.7) or the semantic set (§3.2). No hand-picked hex.
10. **Every type value** is one of the four steps at 500 / 700 / 800 (§2), and the face is Roboto — italic serif only on lowercase algebraic variables (§2.0). No fluid sizing, no in-between weight, no third face.
11. **Every radius** is from the ladder (§4); every shadow from §6.
12. **The ban sweep** — no gradient but a primary button's own vertical pair; no bevel but a button's base edge (§20.0.1); no text shadow; no glow but `attention` (§8a.3); no uppercase outside the `label` step.

**Record the pass.** An unchecked board is not "probably fine" — it is unchecked, and across 2000 modules that difference *is* the backlog. The check is cheap: eleven of the twelve are mechanical, and the twelfth (check 5) is one sentence the author had to write anyway.

---
