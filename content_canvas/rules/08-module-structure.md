<!-- Content Canvas Rules — v1.0 — 17 August 2026 — part file 9 of 13 -->

> **PART 7 — MODULE STRUCTURE**
> 
> | | |
> |---|---|
> | **Owner** | Content Canvas — **feeds** |
> | **Domain** | Journey Structure (2) + Milestones & Tropes (4) |
> | **Governs** | The three default boards, the module shell, board kinds and families, sequencing. |
> | **Loaded when** | A module is being assembled or re-sequenced. |
> | **Requires** | `00-contract.md` + `01-foundations.md` + `12-rules.md` |
> | **Version** | v1.0 — 17 August 2026 |

> **What this file does not decide.** Type steps, colours, radii, shadows, spacing, the layout
> contract, motion and state values are defined in `01-foundations.md` and cited here by `§`
> number. If a value you need is not in this file, it is there — do not infer it. `§` refers to
> sections (numbered 0–45); `R` refers to rules (numbered 1–120) in `12-rules.md`. Both numbering spaces are
> permanent: numbers are added, never reassigned.

---
# PART 7 — MODULE STRUCTURE

## 44. The three default boards

Every module has these, authored from fixed layouts so students recognise them instantly.

**Introduction (`T01`/`T02`)** — name the thing, show its shape. Mascots + `hero` + one-line subtitle + at most one artefact. No list, no CTA; the nav row's Next is the only action.

> **Converged with Journey Studio's master vault.** This trope is shared. Journey Studio owns the
> *behaviour* — when the board is shown, re-shown, and which rows are ticked (their domains 1, 2, 4).
> This document owns only its *appearance* (domain 8): the layout below, the type steps, the tick
> treatment and the celebration. Where the two disagree on cadence, theirs governs; on rendering,
> this section governs. Do not implement a second objectives trope.

**Learning objectives (`T06`)** — **3 to 4**, each one sentence beginning with a verb. Numbered badges. One secondary: "I already know these". **This board is the module's spine** — it is re-shown after each objective is met, with that row ticked and a ring pulse.

3 is the target; 4 is the ceiling because a 4-row stack plus a title and an action button is already at the height budget (§7.2), and beyond 4 a student stops reading the list. If a module has 5 objectives, it is two modules.

**Closing (`T05`)** — `title` + the objectives now all ticked + rewards row + one primary CTA. Never introduce new content on a closing board.

## 44a. The module shell

When the canvas runs standalone (an authoring preview, a review build, an export) it needs a way to move between boards. That chrome is **not** part of any board and never paints on the canvas.

**Engineering guardrails for the shell's fit routine** — both of these hang the page, not just misdraw it:

- **The element a fit routine measures must not contain anything that routine sizes.** Measuring a container that holds the scaled stage means each measurement changes the thing being measured: the observer refires, and the main thread never yields. Measure a wrapper that is sized by the viewport alone.
- **Coalesce `ResizeObserver` through one `requestAnimationFrame`**, on top of a size guard that ignores sub-pixel deltas. The guard alone is not enough — a ping-pong between two values that round differently fires the observer synchronously forever.

**Never re-create what the host already shows.** In the product the canvas is mounted inside the Teaching Room, which owns module identity (breadcrumb) and position (module progress bar) in its own top chrome. A canvas that draws its own breadcrumb or `4 of 21` counter states those facts twice — and the two copies drift apart the moment either changes. So:

- **Banned in the shell:** breadcrumb, grade/chapter/module label, module title, percentage or `n of m` counter, streak, XP, goals, close button, logo. All host-owned.
- **Allowed in the shell:** board navigation only — the rail, prev/next, keyboard bindings. These exist because the standalone preview has no host to drive the deck; they are a harness, not product UI.
- **Test before adding any shell element:** *"Would this element still be on screen if the canvas were mounted in the Teaching Room right now?"* If yes, the host draws it — leave it out.

| Element | Spec |
|---|---|
| Board rail | Bottom-centre, 8px dots, `gap-tight`, current stretched to a 20px pill: `#6741d9` current · `#d0bfff` seen · `#dcd8e6` unseen. Clickable |
| Prev / next | 46px icon buttons flanking the rail, radius 20, neutral face, 4px base edge, chevron `#6741d9`, disabled at an end |
| Keyboard | ← / → always move by one board |

The counter lives in the shell, never on a board. A board that prints its own position is duplicating the shell.

## 45. Board kinds

Each board declares one kind, which fixes its chip, accent and action row:

| Kind | Chip | Accent | Action row |
|---|---|---|---|
| `intro` | none | concept | none |
| `divider` | the phase (WATCH AND LEARN / DO AND LEARN) | action | none |
| `objectives` | none | concept | secondary |
| `teach` | none | concept | none |
| `explain` | CONCEPT | concept | Hint |
| `explore` | TRY IT | action | Hint + Check |
| `practice` | QUESTION | emphasis | Hint + Check |
| `feedback` | none | correct/wrong | Continue |
| `recap` | none | concept | none |
| `word-problem` | none | emphasis | Hint + Check |
| `challenge` | CHALLENGE | emphasis | Hint + Check |
| `recall` | RECALL | concept | Check |
| `bridge` | none | concept | none |
| `closing` | none | correct | primary |

Author boards with `data-board-kind`, `data-layout` and `data-band` so drift is visible.

## 44b. The board families the library actually needs

Roughly a fifth of the library is named `Practice: …`, another chunk `Challenges on …`, and another `Word Problems on …`. They are three different things and were being built as one.

### Word problem

The most-used layout in the library, and Part 9 had no entry for it.

```
stem ......... body/500, max words = band ceiling (§2.6), left-aligned, measure 720
given/asked .. the quantities lifted out of the stem as a 2-row list, or marked in the stem
model ........ ONE model from Part 3B — the module's model (§36.2)
working ...... §17i or §17j, at most the band's step ceiling
answer ....... a boxed final line, with its unit
```

- **The stem is never re-read to find a number.** Every quantity the student needs is either lifted into the given list or `emphasis`-marked in the stem itself.
- **The unit is part of the answer.** An unlabelled number is not a solution to a word problem.
- **Names and contexts stay neutral and local** — no brands, no aspirational settings, nothing a student needs cultural knowledge to parse.
- If the stem exceeds the band ceiling, the problem is too wordy for the band — rewrite the stem, never shrink the type.

### Practice

Fluency. Many short items, one skill, low reading load.

- **One item per board**, same layout every board, so only the numbers change. A student in fluency should never re-learn the interface.
- Answer box or option row (§19a / §20.0a), Check, feedback (§21), auto-advance.
- **No new notation and no new model** — practice consolidates, it does not teach.
- 6–12 items per module.

### Challenge

Fewer items, multi-step, may combine skills.

- May introduce a **new context**, never new notation.
- Hint pattern (§20.1) is mandatory — max two, revealed in order.
- Working is shown after the answer is judged, never before.
- 3–5 items per module.

### Recall / recap

Named `Recall …` or `Recap …` across the library — it is a **prerequisite check**, not a lesson.

- Draws only on prior modules, introduces nothing.
- Max 3 boards; if it needs more, the prerequisite is a module of its own.

### Optional / booster

Titled `… (Optional)` or `… Booster`. Carries the `ti-plus` marker chip (§14a) in `#868e96`, and **nothing inside it may be a prerequisite for a later module.**

## 45a. Sequencing

- Never three of the same kind consecutively — alternate explain and practise.
- An `explore` board precedes the first `practice` on a concept.
- A `recap` board follows every objective completion.
- Max 12 boards per module; 8 is the target.

---

---
