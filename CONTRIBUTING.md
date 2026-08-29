# Contributing to the Alatyr site

This repository is the project's landing page in three languages. The bar for a change
is not "make Alatyr sound impressive" — it is **make the page true**, including where
the honest answer is that something is not ready yet.

## What a good contribution looks like

- **A correction.** A claim on the page that `spec/` or `compiler/` does not support is
  a bug, and fixing it is the most valuable thing you can do here.
- **A translation fix.** The Russian and Chinese pages were written by the maintainers,
  not by native technical writers. Wording that a systems programmer in that language
  would not use is worth an issue even without a patch.
- **A new language.** See `AGENTS.md` for the mechanics: a directory, an entry in every
  switcher, an `hreflang` line on every page, and a row in `sitemap.xml`.
- **An accessibility or layout fix**, especially one you can reproduce on a real device.

## The rules that keep it honest

- **Every claim traces to a line in a sibling repository.** `README.md` holds the table
  of claim → source. A new claim without a new row in that table will be asked for one.
- **No benchmark numbers.** The `benchmarks` repository is a harness, not a result set;
  timings depend on the machine, and a number without its machine is not a measurement.
  A speed claim on a landing page is the easiest way to publish something untrue.
- **Do not describe the compiler as further along than it is.** It is self-hosted and
  byte-reproducible, and it is also pre-release, x86_64 Linux only, with no tagged
  release. All of that is true at once and the page says so.
- **A content change touches all three pages.** One language drifting is how a site
  starts contradicting itself.
- **No build step and no page JavaScript.** See `AGENTS.md` for why the duplication is
  deliberate.

## Before you open a PR

```sh
python3 -m http.server 8000
```

Check the page you changed at 375, 640, 900 and 1440 px, in every language you touched.
Nothing should scroll sideways, no local link should 404, and no CSS rule should be left
behind with nothing using it.

## Commit messages

Use [Conventional Commits](https://www.conventionalcommits.org/):
`<type>(<scope>): <imperative summary>`, for example `fix(ru): correct the lowering wording`.
Keep the subject short and omit the trailing period. Suitable types here include `feat`,
`fix`, `docs`, `style`, `refactor`, `chore`.

## Licensing of contributions

By contributing you agree that your contribution is licensed under **Apache-2.0**, the
licence of this repository.
