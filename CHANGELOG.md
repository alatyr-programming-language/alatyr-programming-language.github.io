# Changelog

What is recorded here is what changes the site's *claims* or its structure — a new
language, a reworded principle, a link that now points somewhere else. Typography and
spacing adjustments are not listed individually.

## Unreleased

First public version of the site; nothing is tagged yet.

- The landing page in three languages — English, Russian and Simplified Chinese — as
  static files with their own URLs, no build step and no page JavaScript.
- Content is drawn from the specification and the compiler repository: the thesis and
  niche from `spec/00-overview.md`, the three principles from invariants `I1`, `I3` and
  `I11`, and the declaration example from `spec/40-declarations.md`. `README.md` carries
  the claim → source table.
- Deliberately absent: benchmark numbers, and any description of the compiler as more
  finished than pre-release. The `benchmarks` repository holds a harness, not results.
- `Download` links straight at `seed/alatyr` on `raw.githubusercontent.com`. The
  `blob` URL it replaced served GitHub's file viewer, which cannot display a 3.9 MB ELF.
  Once releases are tagged, this should point at a tag rather than at `main`.
- The declaration example follows `spec/40-declarations.md` §1.3 again: the
  type-returning function there is named `Run`, not `Vec` (renamed in the spec at
  `9f7bce3`), and the page shows the sample verbatim.
- The mark is the organisation's identicon redrawn as a transparent SVG; it is also the
  favicon, so the page makes no external requests at all.
