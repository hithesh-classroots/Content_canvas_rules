# Content canvas — reference implementations

The **rendered** authorities the markdown law defers to. When a rule says *"trust the
reference implementation over any number written here — it measures its own contrast at
render time,"* the file it names lives here.

## The canonical reference — `Design Component Systems.dc.html`

**One dual-mode file is the source of truth for every component**, in both rooms. The rules
cite it per system, by anchor:

| Rule that cites it | Anchor |
|---|---|
| `rules/05-interactive.md` §18 (slider) | `Design Component Systems.dc.html#slider` |
| `rules/05-interactive.md` §18a (counter) | `…#counter` |
| `rules/05-interactive.md` §20 · `rules/01-foundations.md` §3.7 · `rules/03-…` (surfaces & buttons) | `…#shape` |
| `rules/03-data-maths-diagrams.md` §16 (graph) | `…#graph` |
| `rules/03-data-maths-diagrams.md` §17a (number line) | `…#numberline` |
| `rules/03-data-maths-diagrams.md` §17b (venn & set) | `…#venn` |
| `rules/design-system.md` §5 (the dark room) | the same file — **toggle the room** |

It is **hand-authored plain HTML/CSS/JS** (no `x-dc`, no bundler runtime, no network),
**role-parametrised** so it crosses light↔dark as a palette resolution, and it **measures its
own contrast at render time** in whichever room is shown (a live auditor, per §5.7/§9). Because
it is dual-mode, it **supersedes the separate `Component Systems - Dark.dc.html`** the dark-mode
doc used to name.

> **Reading it as a seat:** trust the renders over any number in the prose, but do **not**
> copy the file's `:root` or its `@font-face`. An applet **consumes the §26 token bridge**
> (`--accent`, `--accent-action`, `--accent-ok`…), **inherits the pinned font** from the room
> (§25.3), and keeps the **board transparent** (§25.1). The file self-hosts the font and paints
> a shell only because it is a standalone document, not an applet — it says so in its own header.

## Also here

| File | What it is |
|---|---|
| `three-canvas-frames.html` | The pipe-type reference: a **still**, an **applet**, the same applet **MCP-ised**, and a real interstitial — the clearest still↔applet demonstration. |
| `Design Component Systems.html` | The **original** Claude-design canvas bundle Hithesh authored (the `<x-dc>` version, light only). Retained as the authored source; **no longer the cited reference** — the dual-mode `.dc.html` above supersedes it. |

`Exponents Module - New design adoption.html` was **intentionally not vendored** — a worked
example, cited by no rule, and compiled React (its design values aren't legible in source).

## ⚠ Authoring a reference: plain HTML only — never a Claude-design export

A reference here MUST be **hand-authored / flattened HTML + CSS + JS with no Claude-design
canvas machinery**: no `<x-dc>` custom elements, no `__bundler` script blocks, no external
`dc-runtime` loader script, no uuid-keyed embedded resources, and **no network** (inline
fonts and assets as `data:` URIs).

**Why this is a hard rule.** A reference is read by seats to *design applets against it*. A
Claude-design export carries a runtime a seat cannot and must not adopt, and it invites a seat
to copy `<x-dc>` / bundler scaffolding into an applet — which breaks the §26 token bridge and
the transparent-board contract (§25.1). The reference has to render and **self-measure its own
contrast** with nothing but a browser.

**If you author in Claude Design, flatten before vendoring:** export, strip the bundler
wrapper and the `<x-dc>` runtime, keep only the rendered markup + CSS, and embed assets as
`data:` URIs. The current `Design Component Systems.dc.html` is the template — open it and it's
plain role-based CSS and inline SVG, **zero** canvas runtime. (The old
`Design Component Systems.html` bundle is retained only as an authored source, and is *not* a
reference precisely because it still carries the `<x-dc>` runtime.)
