# Content canvas rules - index

**v1.0 - 17 August 2026.** Everything that renders **inside the 16:9 content canvas**: a
slide-master set, where an author picks a layout, fills its slots, and the result is
correct by construction. `design-system.md` governs the page shell around it - top chrome,
chat window, dock - and is a different space (below).

**THESE FILES ARE THE SOURCE. Edit them here.** They arrived as a split generated from a
single `Content Canvas Rules.md`, and that monolith does not travel with them: two copies
of one rulebook drift, and the estate has the scars. Written by Hithesh
(`hithesh-classroots/Content_canvas_rules`, deprecated 2026-08-17 in favour of this
directory), who holds write access here.

**Part boundaries are frozen** - parts may be appended, never renumbered, resequenced or
merged. A part number is its name in every citation, the same rule the journeyisation
rulebook keeps its numbering gaps for.

## Always loaded

`00-contract.md` · `01-foundations.md` · `12-rules.md`

Three files, and no board or job is exempt from them. **`01-foundations.md` is the only
file that states a literal value** - every other file cites into it by `§` number. That is
what stops thirteen files from drifting apart, and it is mechanically checkable.

## Citation spaces

Four spaces here, and they are **not interchangeable**. Numbers are permanent in each:
added, never reassigned; gaps kept deliberately.

| Cite as | Space | Lives in |
|---|---|---|
| `[canvas §N]` | Sections, `§0`-`§45` | `00-` .. `12-` |
| `[canvas RN]` | Rules, `R1`-`R120` | `12-rules.md` |
| `[shell §N]` | Sections, `§1`-`§4` | `design-system.md` |

**`shell` is separate because it collides.** `design-system.md` numbers its own sections
`1. Foundations · 2. Components · 3. Layout & z-order · 4. Rules`, against canvas
`§1 Grid · §2 Type · §3 Colour · §4 Radius`. Cited in one space, `§3` means two different
things. Verified at import: 71 canvas sections and 4 shell sections, no duplicate **within**
a space.

**Never cite bare `§` here.** `[contract §7.10]` is the applet runtime contract and
`[canvas §7.10]` does not exist - the estate already writes bare `§7.4` meaning the
contract, and a bare `§` from here on is ambiguous by construction. The registry is
`sources/domains/CITATIONS.json`.

## Routing

| File | Part | Owner | Domain | Load when |
|---|---|---|---|---|
| [`00-contract.md`](00-contract.md) | 0 - THE CONTRACT | **owns** | Canvas & Surface Design (8) | always |
| [`01-foundations.md`](01-foundations.md) | 1 - FOUNDATIONS | **owns** | Canvas & Surface Design (8) | always |
| [`02-content-components.md`](02-content-components.md) | 2 - CONTENT COMPONENTS | **owns** | Canvas & Surface Design (8) | prose, list, table or formula on the board |
| [`03-data-maths-diagrams.md`](03-data-maths-diagrams.md) | 3 - DATA, MATHS & DIAGRAMS | feeds | Making Stills from Assets (10) | figure, chart, graph or diagram on the board |
| [`04-model-library.md`](04-model-library.md) | 3B - THE MODEL LIBRARY | feeds | Pedagogy & Arc (1) | manipulative or worked model on the board |
| [`05-interactive.md`](05-interactive.md) | 4 - INTERACTIVE | feeds | Interaction & Affordance (7) | a control the student operates |
| [`06-applets.md`](06-applets.md) | 5 - EMBEDDED INTERACTIVES | feeds | Interaction (7) + Canvas (8) in an iframe | an applet is embedded or being onboarded |
| [`07-illustration.md`](07-illustration.md) | 6 - ILLUSTRATION & GRAPHICS | feeds | Making Stills from Assets (10) | an illustration is being made |
| [`08-module-structure.md`](08-module-structure.md) | 7 - MODULE STRUCTURE | feeds | Journey Structure (2) + Tropes (4) | a module is assembled or re-sequenced |
| [`09-authoring-from-source.md`](09-authoring-from-source.md) | 8 - AUTHORING FROM SOURCE | feeds | Pedagogy (1) + Evidence & Gates (9) | recreating a module from source material |
| [`10-layout-library.md`](10-layout-library.md) | 9 - LAYOUT LIBRARY | **owns** | Canvas & Surface Design (8) | a board needs a layout chosen |
| [`11-normalisation.md`](11-normalisation.md) | 10 - NORMALISING A LIBRARY | feeds | Evidence & Gates (9) | bringing an existing library into conformance |
| [`12-rules.md`](12-rules.md) | 11 - THE RULES | **owns** | Canvas & Surface Design (8) | always |
| [`design-system.md`](design-system.md) | - (peer document) | **owns** | Canvas & Surface Design (8), host half | the page shell, chat, dock or mascots are in question |

`design-system.md` is deliberately unnumbered: it is a peer document, not PART 13 of a
document it is not part of.

## Worked routing examples

| Job | Files to load |
|---|---|
| Redesign one explanation board with a diagram | core + `10-layout-library` + `02-content-components` + `03-data-maths-diagrams` |
| Redesign a practice board with a slider | core + `10-layout-library` + `05-interactive` |
| Onboard a legacy applet | core + `06-applets` |
| Recreate a module from a source deck | core + `09-authoring-from-source` + `08-module-structure` + `10-layout-library` |
| Normalise 2,000 existing modules | core + `11-normalisation` + `06-applets` |
| Make an illustration for a board | core + `07-illustration` |

## Ownership

Content Canvas **owns domain 8 outright** - colour, type, spacing, layout, states. It
**feeds** domains 1, 2, 4, 7, 9 and 10, and **touches nothing in domains 3, 5 or 6** -
pacing and timing, voice and language, and the applet runtime contract (event API,
completion semantics, script load order) are the studio's alone. Part 5 is domains 8 and 7
applied inside an iframe - appearance and controls - never the runtime.

Where the studio holds a **stricter** line than a rule here, that is recorded at the point
of divergence, never diverged from quietly. There is one today: the transparent field.
`[canvas §0.1]` and `[canvas §23]` require it; `probe-transparency` additionally asserts
computed background and `color-scheme` in **both** themes, because a mismatch makes Chrome
opacify the whole iframe. See `[domains] 8`.

## Known open, carried from import (2026-08-17)

Three citations resolve to nothing. They are upstream's to fix and are recorded here rather
than silently tolerated - the estate shipped 12 broken links once by not writing them down:

| Cite | Cited by | State |
|---|---|---|
| `§9.4` | `01-foundations.md` ×2 | no such section |
| `§14a` | `08-module-structure.md` | no such section - the `ti-plus` marker chip |
| `§20.0a` | `08-module-structure.md`, `10-layout-library.md`, `12-rules.md` | no such section - and `R37e` depends on it |

**These are OURS to carry now, not upstream's to fix.** The files were copied here and that
repo is being deprecated, so a fix in his copy would land somewhere nothing reads. What is
genuinely still his is the *intent* - only the author knows what `§20.0a` was meant to say,
and `R37e` leans on it - so these stay recorded rather than invented. Ask when convenient;
do not guess a section into existence.

**A SECOND DEFECT CLASS, found by a seat reading the published law 2026-08-18: two ORPHANED
TABLE ROWS in `05-interactive.md` §20.0.4.** After *"...not a lighter weight."* three rows
(`Disabled` / `Correct / wrong` / `Group`) appear with no header, and after the numbered list a
lone `Icon` row is stranded mid-prose. They render as literal pipes or a broken table.

**It is NOT our splice.** The same rows sit at the same line numbers - 258 and 268 - in the
upstream monolith AND in Hithesh's own `05-interactive.md`. Our copy is byte-faithful; the
headers were lost before the files ever reached this repo. Recorded rather than reconstructed:
the `Icon` row has three columns and the other three have two, so they belong to two different
tables, and inventing headers is the same failure as inventing a section. Ask, do not guess.

**THE R-RANGE HAS BEEN SWEPT, so `R26` is not a sample - it is the whole finding.** A seat
reasonably asked whether R26 was simply the first collision anyone had probed. Two independent
sweeps say no: **all 511 locators** in `CITATIONS.index.json` across all 8 spaces yield exactly
**one** collision, and a direct scan of `12-rules.md` that does not use the index at all finds
**129 rule ids spanning R1-R115, no gaps, and `26` the only duplicate** (lines 51 and 54).
The permanence guarantee - *"numbers are added, never reassigned"* - is broken in exactly one
place, and the resolver refuses that one by name rather than choosing.

Also: `12-rules.md` says `R1`-`R120` in three places while the highest rule is **115**
(129 ids counting letter suffixes), and rule number `26` is used twice - *"Source colours
are semantic commitments"* and *"Keep the source layout unless it fails hierarchy"* - in a
space declared permanent.
