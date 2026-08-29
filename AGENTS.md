# AGENTS.md — the Alatyr site

Three hand-written HTML pages, one stylesheet, one SVG mark. GitHub Pages serves the
repository root as `alatyr-programming-language.github.io`. No compiler and no
specification text live here.

```
index.html       English (the default)
ru/index.html    Russian
zh/index.html    Simplified Chinese
styles.css       shared by all three
logo.svg         the mark, also the favicon
og.png           the social preview, 1200x630
```

## The one rule that matters

**Every claim on the page must be traceable to a line in `spec/` or `compiler/`.**

The specification is a complete first draft *under review*, and the compiler is
pre-release. A landing page is exactly where a project starts overselling itself, and
a claim the repositories do not support is a defect here — not a matter of taste.
That is why the page carries no benchmark numbers: `benchmarks/` holds a harness, not
results, and its own `AGENTS.md` says a number without its machine is not a
measurement.

The traceability table lives in `README.md`. If you add a claim, add its source there
in the same commit.

## No build step

The files are served exactly as committed. There is no generator, no framework, and
no JavaScript on the page — the language switcher is ordinary links, so it works with
scripts disabled and gives each language its own URL and its own `<html lang>`.

Do not introduce a build step to remove the duplication between the three pages. The
duplication is the cost of being a static site with three real URLs, and it is
cheaper than a toolchain nobody will have installed in a year.

To look at it:

```sh
python3 -m http.server 8000
```

## Editing the pages

- **A content change has to be made in all three pages.** They share a structure and
  differ only in their text; if one drifts, the site starts contradicting itself.
- **Prose is translated, including comments inside the code sample. Code is not.**
  Identifiers, keywords and the shape of the `declarations.al` example stay exactly as
  the specification writes them.
- **Language links point at `ru/index.html`, not `ru/`.** A bare directory link needs a
  server that serves a directory index; opened from disk over `file://` it shows a file
  listing. The `hreflang` tags carry the canonical directory URLs — those are for search
  engines, not for navigation.
- **Chinese headings have their own line-height and tracking** (`html[lang^="zh"]` in
  `styles.css`). The display settings tuned for Latin text collide full-width glyphs
  into each other; this is not a detail you can drop when adding a heading.

## Checks before a commit

There is no CI. Run these by hand:

- No horizontal scrolling at 375, 640, 900 and 1440 px, on all three pages.
- Every `.landing-*` / `.site-*` rule in `styles.css` is used by at least one page, and
  every class in the markup has a rule. Dead CSS accumulates fast in a file this small.
- Local links resolve to files that exist — including from `ru/` and `zh/`.
- The pages still say only what the sibling repositories support.
