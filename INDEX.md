# Content Canvas Rules — split index

**v1.0 — 17 August 2026.** Split per PART from `Content Canvas Rules.md`, which remains the
single source. These files are generated: **do not edit them.** Fix the source and re-split.

Part boundaries are **frozen** — parts may be appended, never renumbered, resequenced or merged.

## Always loaded

`00-contract.md` · `01-foundations.md` · `12-rules.md`

Three files, and no board or job is exempt from them. `01-foundations.md` is **the only file that
states a literal value** — every other file cites into it by `§` number. That is what stops thirteen
files from drifting apart, and it is mechanically checkable.

## Citation spaces

| Sigil | Space | Lives in |
|---|---|---|
| `§` | Sections, numbered 0–45 | all files |
| `R` | Rules, numbered 1–120 | `12-rules.md` |

Both are permanent. Numbers are added, never reassigned; gaps are kept deliberately.

## Routing

| File | Part | Owner | Domain | Load when |
|---|---|---|---|---|
| [`00-contract.md`](00-contract.md) | 0 — THE CONTRACT | **owns** | Canvas & Surface Design (8) | always |
| [`01-foundations.md`](01-foundations.md) | 1 — FOUNDATIONS | **owns** | Canvas & Surface Design (8) | always |
| [`02-content-components.md`](02-content-components.md) | 2 — CONTENT COMPONENTS | **owns** | Canvas & Surface Design (8) | prose, list, table or formula on the board |
| [`03-data-maths-diagrams.md`](03-data-maths-diagrams.md) | 3 — DATA, MATHS & DIAGRAMS | feeds | Making Stills from Assets (10) | figure, chart, graph or diagram on the board |
| [`04-model-library.md`](04-model-library.md) | 3B — THE MODEL LIBRARY | feeds | Pedagogy & Arc (1) | manipulative or worked model on the board |
| [`05-interactive.md`](05-interactive.md) | 4 — INTERACTIVE | feeds | Interaction & Affordance (7) | a control the student operates |
| [`06-applets.md`](06-applets.md) | 5 — EMBEDDED INTERACTIVES | feeds | Interaction (7) + Canvas (8) in an iframe | an applet is embedded or being onboarded |
| [`07-illustration.md`](07-illustration.md) | 6 — ILLUSTRATION & GRAPHICS | feeds | Making Stills from Assets (10) | an illustration is being made |
| [`08-module-structure.md`](08-module-structure.md) | 7 — MODULE STRUCTURE | feeds | Journey Structure (2) + Tropes (4) | a module is assembled or re-sequenced |
| [`09-authoring-from-source.md`](09-authoring-from-source.md) | 8 — AUTHORING FROM SOURCE | feeds | Pedagogy (1) + Evidence & Gates (9) | recreating a module from source material |
| [`10-layout-library.md`](10-layout-library.md) | 9 — LAYOUT LIBRARY | **owns** | Canvas & Surface Design (8) | a board needs a layout chosen |
| [`11-normalisation.md`](11-normalisation.md) | 10 — NORMALISING A LIBRARY | feeds | Evidence & Gates (9) | bringing an existing library into conformance |
| [`12-rules.md`](12-rules.md) | 11 — THE RULES | **owns** | Canvas & Surface Design (8) | always |

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

Content Canvas **owns domain 8 outright** — colour, type, spacing, layout, states. It **feeds**
domains 1, 2, 3, 4, 7, 9 and 10, and **touches nothing in domain 6** (the applet runtime contract:
event API, completion semantics, script load order). Part 5 is domains 8 and 7 applied inside an
iframe — appearance and controls — never the runtime.

Where a downstream consumer holds a stricter line than a rule here, that is recorded at the point of
divergence, not diverged from quietly.
