# alatyr-programming-language.github.io

The Alatyr language site, served by GitHub Pages from the repository root.

```
index.html       English (the default)
ru/index.html    Russian
zh/index.html    Simplified Chinese
styles.css       shared styles for all three
logo.svg         the mark, also the favicon
og.png           the social preview, 1200x630
robots.txt       points crawlers at the sitemap
sitemap.xml      the three pages and their hreflang pairs
.nojekyll        serve the tree as-is, without Jekyll
```

No build step, no framework, no JavaScript. To preview it locally:

```sh
python3 -m http.server 8000
```

## Where the content comes from

Every factual claim on the page is taken from a sibling repository and must be
traceable to a line there:

| Claim on the page | Source |
| --- | --- |
| The one-sentence thesis, and "you always know what the machine does" | [`spec`](https://github.com/alatyr-programming-language/spec) — `README.md`, `spec/00-overview.md` §thesis |
| "One language. Every layer." — no tier ladder | `design/decisions/principles.md` (`PRIN-7`), `spec/00-overview.md` (`I5`) |
| "Transparent lowering." | `spec/00-overview.md` — invariant `I1` |
| "Nothing hidden." | `spec/00-overview.md` — invariant `I3` |
| "Correct, or a trap." | `spec/00-overview.md` — invariant `I11` |
| One declaration form, and the `declarations.al` sample verbatim | `spec/40-declarations.md` §1.1 and §1.3 |
| What the `Download` link serves | [`compiler`](https://github.com/alatyr-programming-language/compiler) — `seed/alatyr`, described in its `README.md` |

Two rules follow from that:

- **Do not publish a claim that no line in `spec/` or `compiler/` supports.**
  The specification is a draft under review and the compiler is pre-release;
  overstating either is worse than saying less.
- **Do not publish benchmark numbers.** The
  [`benchmarks`](https://github.com/alatyr-programming-language/benchmarks)
  repository holds a harness, not results: timings are machine-dependent, and
  its own `AGENTS.md` says a number without its machine is not a measurement.

## Translations

The three pages carry the same structure and differ only in their text. They are
plain files, not generated at serve time, so **a content change has to be made in
all three** — otherwise the versions drift apart.

The language switcher in the header is a set of ordinary links; the current
language is a `<span class="active">`, the others are `<a>`. They point at
`ru/index.html` rather than `ru/` on purpose: a bare directory link needs a
server that serves a directory index, and opening the page from disk over
`file://` shows a file listing instead. Each page also declares the full set
through `<link rel="alternate" hreflang="…">` — those carry the canonical
directory URLs, which is what search engines should see.

Adding a language means: create its directory, add its entry to every switcher,
and add its `hreflang` line to every page.

Prose is translated, and that includes the comments inside the code sample. The
code itself — identifiers, keywords, the shape of the `declarations.al` example —
stays exactly as it appears in the specification.

Chinese headings get their own line-height and tracking (`html[lang^="zh"]` in
`styles.css`): the display settings tuned for Latin text collide full-width
glyphs. The Chinese copy is a first pass and would benefit from a native review.

## Status of the page

The landing page is complete: hero, principles, syntax, footer. Documentation
pages are a separate, later step and intentionally do not exist yet.

## Licence

Apache-2.0 — see [`LICENSE`](LICENSE). `AGENTS.md` records how the site is built and
what may not be claimed on it; [`CONTRIBUTING.md`](CONTRIBUTING.md) is the short version
for anyone opening a pull request.
