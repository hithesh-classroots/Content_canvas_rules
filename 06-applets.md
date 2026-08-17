<!-- Content Canvas Rules — v1.0 — 17 August 2026 — part file 7 of 13 -->

> **PART 5 — EMBEDDED INTERACTIVES (APPLETS)**
> 
> | | |
> |---|---|
> | **Owner** | Content Canvas — **feeds** |
> | **Domain** | Interaction & Affordance (7) + Canvas (8), inside an iframe |
> | **Governs** | Boundary rule, the two conformance tiers, change consent, onboarding audit, token bridge, override layer, cache discipline, manifest. **Touches nothing in the runtime contract (domain 6).** |
> | **Loaded when** | A board embeds an applet, or an applet is being onboarded. |
> | **Requires** | `00-contract.md` + `01-foundations.md` + `12-rules.md` |
> | **Version** | v1.0 — 17 August 2026 |

> **What this file does not decide.** Type steps, colours, radii, shadows, spacing, the layout
> contract, motion and state values are defined in `01-foundations.md` and cited here by `§`
> number. If a value you need is not in this file, it is there — do not infer it. `§` refers to
> sections (numbered 0–45); `R` refers to rules (numbered 1–120) in `12-rules.md`. Both numbering spaces are
> permanent: numbers are added, never reassigned.

---
# PART 5 — EMBEDDED INTERACTIVES (APPLETS)

A real module embeds many applets, simulations and widgets. Most arrive as an iframe with **its own stylesheet**, often authored by another team or vendor, often versioned outside this repo. This is the largest source of drift on the canvas, so it gets its own protocol.

## 22. The boundary rule

**An iframe inside the content canvas is part of the content canvas.** Separate authorship does not exempt it. The student cannot see the boundary — they see one lesson, and a widget with its own violet and a 550 weight reads as a bug.

Every rule in this document therefore applies to applet content. What differs is not *whether* they apply, but *how you are permitted to enforce them* (§24).

## 23. Two tiers of conformance

Sort every finding before touching anything.

### Tier A — non-negotiable, blocks ship

These break the product, not just its consistency:

| Requirement | Why it blocks |
|---|---|
| `html`, `body` and the applet root are `background: transparent` | An opaque applet background hides the room's gradient, dot lattice and the answer-feedback light leak (§0.1) |
| No dark surface, no white ink | There is no dark surface in the system; white ink becomes unreadable the moment the background is fixed |
| Sentences ≥ 24px, labels ≥ 16px | Classroom legibility |
| Hit targets ≥ 44px | Tablet is the primary device |
| No hover-only affordance | There is no hover on tablet |
| Colour is never the only signal | Colour-vision accessibility |
| `prefers-reduced-motion` honoured | Vestibular accessibility |
| Not Roboto | A vendor's Arial, Inter or webfont is instantly visible beside Roboto (§2.0) |

### Tier B — align, but negotiable

Cosmetic conformance. Fix with consent or ownership; never block a lesson on it:

- Exact hue tokens (a vendor's `#5f3dc4` vs our `#7950f2`)
- Radius and shadow ladders
- Gap and padding scales
- Weight categories (550 → 500/700/800)
- Fluid `calc(vw + vh)` sizing → the four fixed steps

## 24. The change-consent protocol

**Never silently rewrite an applet's stylesheet.** Its author may have pedagogical or technical reasons for a value, and it may be maintained elsewhere — a silent edit is lost at their next release.

1. **Audit** against §25; produce findings split into Tier A and Tier B.
2. **Fix Tier A immediately** and notify the owner. These are defects, not preferences — shipping an opaque or illegible applet is not an option.
3. **Request consent for Tier B**, quoting the exact declarations and the tokens they should become. One request per applet, not per property.
4. **If granted**, patch at source and record it in the manifest.
5. **If refused, or the source is not ours**, apply an override layer (§27) — never fork the applet.
6. **Re-audit on every version bump.** A vendor update silently reintroduces its own tokens.

## 25. The onboarding audit

Twelve checks before an applet ships. This is the list that would have caught every problem in the current parallelogram applet:

| # | Check | Fail looks like |
|---|---|---|
| 1 | Root, `html`, `body` transparent | `background: #1f1f1f` |
| 2 | No board-level gradient or tint | a `radial-gradient` on the container |
| 3 | Font stack inherited | `font-family: Arial` |
| 4 | Every `font-size` on the 4-step scale | `calc(1.5vw + 1.45vh)` |
| 5 | Every `font-weight` in 500/700/800 | `font-weight: 550` |
| 6 | Title ink is `#212529`, not an accent | a fully violet title |
| 7 | One token per accent role | `#5f3dc4` *and* `#7950f2` for the same job |
| 8 | Fills opaque, not alpha | `rgba(121,80,242,.20)` shape fill |
| 9 | Grid and axis lines on the §5 table | violet-tinted gridlines |
| 10 | Controls ≥ 44px and visible at rest | a 24px thumb with no resting affordance |
| 11 | Bundle loaded with a version query | a `<script src>` with no `?v=` |
| 12 | Renders on all three gradient stops | text vanishing at the cream end |

**SVG exemption:** a `font-size` in *user units* inside a `viewBox` (e.g. `0.62px` in a 0–10 space) is legal and exempt from check 4 — it is not a CSS pixel size. Judge it by its rendered size.

## 26. The token bridge

Applets must **consume variables, never hardcode**. The room injects this block into every applet frame; the applet's own `:root` declares nothing but fallbacks.

```css
/* injected by the room — the applet's contract with the canvas */
--ink:            #212529;
--ink-body:       #495057;
--ink-muted:      #868e96;
--accent:         #7950f2;   /* concept */
--accent-action:  #228be6;
--accent-emph:    #fd7e14;
--accent-ok:      #40c057;
--accent-no:      #fa5252;
--tint:           #f3f0ff;
--surface:        #ffffff;
--surface-sunken: #f8f9fa;
--border:         #e9ecef;
--grid-minor:     #e9ecef;
--grid-major:     #dee2e6;
--axis:           #adb5bd;
--helper:         #adb5bd;
--ghost:          #ced4da;
--track:          #e9ecef;
--fs-title:       36px;
--fs-body:        24px;
--fs-label:       16px;
--radius-sm:      8px;
--radius-md:      12px;
--radius-lg:      16px;
--shadow-rest:    0 2px 6px -3px rgba(70,46,146,.16);
```

An applet reading only these inherits every future token change for free and needs no consent request when the palette moves. **Bridge-compliance is the goal state for every applet.**

## 27. The override layer

When source cannot be changed, inject a stylesheet scoped to the applet root, loaded **after** its own:

```css
.applet-root .vendor-title { font-size: 30px; font-weight: 800; color: var(--ink); }
```

Scope every selector to the applet root · no `!important` beyond Tier A · one override file per applet · every rule carries a comment naming the audit item it satisfies · the file is deleted when the vendor adopts the bridge.

## 28. Cache discipline

**Every applet bundle loads with a version query, bumped on every edit:**

```html
<script src="applet-inline.js?v=7"></script>
```

Without it the browser serves the cached bundle and **every fix appears to fail** — you change a colour, reload, and see the old one. This has already cost real debugging time here: three separate colour corrections to the parallelogram applet looked like no-ops because its bundle had no version string.

Applies to inlined bundles too (`window.__APPLET_SRCDOC`) — the *host* script needs the query, or the srcdoc string is stale.

## 29. The applet manifest

Each applet carries a short record beside it:

```
applet:    parallelogram-to-trapezoid
owner:     <team or vendor>
version:   1.4.0
bridge:    none          # none | partial | full
audit:     2026-08-10    # last run of §25
tier-a:    clear
tier-b:    3 open (weights, fluid sizing, radius)
overrides: none
consent:   requested 2026-08-10
```

Without this, the next person cannot tell an intentional vendor value from drift.

---

---
