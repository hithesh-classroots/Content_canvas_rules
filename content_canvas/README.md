# Content canvas — the design source of truth

**This directory is the studio's single home for the Content Canvas design law.** It is
written by Hithesh (author of the design system), who **holds write access here.** His
standalone repo `hithesh-classroots/Content_canvas_rules` was **deprecated 2026-08-17 in
favour of this directory** — maintain the law *here*, not there. Two copies of one rulebook
drift, and as of this writing the standalone repo is already **behind** this one (see
"Currency" below).

Everything under this directory **publishes to Cloudflare on every merge to `main`**
(`sources/content_canvas/**` is a publish root in `.github/workflows/publish-skills.yml`),
lands in R2 as an immutable versioned artifact plus a `latest` pointer, and every seat
fetches it fresh through the `get_skill` MCP verb — no clone, no local copy, no drift.
Add a file here and it is served to every seat automatically.

---

## Layout — where each kind of file goes

```
sources/content_canvas/
├── rules/          the design LAW, as markdown. See rules/README.md for the placement
│                   contract (part boundaries are frozen; append, never renumber; literal
│                   values live only in 01-foundations.md + design-system.md, everything
│                   else cites by § — that is what stops the thirteen files drifting).
├── reference/      the RENDERED reference implementations the rules defer to (below).
├── README.md       this file.
└── VERSION         one line; bump it when you change anything here (currency stamp).
```

### `rules/` — the markdown law
Follow **`rules/README.md`**. In short: a new rule is *appended* to the part that owns it;
part numbers are frozen because a part number is its name in every citation. Design-only
files may be pushed directly; a file a pedagogy domain cites into needs a PR — the
per-file boundary is in `docs/OWNERSHIP-canvas.md`.

### `reference/` — the rendered authorities
Several rules name a rendered `.dc.html` as their **numeric** authority and say, verbatim,
*"trust it over any number written here … it measures its own contrast at render time."*
All of them now resolve to **one dual-mode file** — `reference/Design Component Systems.dc.html`
— cited per system by anchor (`#slider`, `#counter`, `#shape`, `#graph`, `#numberline`,
`#venn`). It is hand-authored (no canvas runtime, no network), role-parametrised so it crosses
light↔dark, and self-measures its own contrast in each room; being dual-mode it supersedes the
old separate `Component Systems - Dark.dc.html`. The per-system placement and the seat-adoption
caveats are in `reference/README.md`.

A reference file must be **self-contained** (it renders with no network), must **render and
self-measure standalone**, and must be **plain HTML — never a Claude-design canvas export**
(no `<x-dc>`, no bundler runtime): a reference is read by seats to design applets, and canvas
runtime artifacts break §26/§25 adoption. Flatten any Claude-design export before vendoring —
see `reference/README.md`.

---

## Currency — this directory is ahead of the standalone repo

As of 2026-09-03 the deprecated `hithesh-classroots/Content_canvas_rules` is **behind**
this directory on at least three rulings, so importing from it would *regress* the studio's
law. Sync the standalone repo *from here*, never the other way:

- the **`<var>`/`.var` marker** for algebraic variables (bold italic serif only when marked) — `rules/00`, `02`, `11`, `12`, `01`;
- the **colour updates** green `#2f9e44` and error `#c92a2a` (were `#2b8a3e` / `#e03131`) — `rules/07`, `09`;
- the **gradient-button retirement** (§20 bans gradient fills) — `rules/design-system.md`.

The standalone repo's dark-mode colour-adoption doc also carries a dark palette that is
**out of scope here** by rule (`rules/design-system.md` §5 keeps player-chrome out of the
studio's canvas). Do not import it wholesale; confirm which values, if any, are
content-canvas darks before adding them.

**When you change anything in this directory, bump `VERSION`.**
