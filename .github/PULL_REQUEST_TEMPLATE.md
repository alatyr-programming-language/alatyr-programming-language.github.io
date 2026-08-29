## What this changes

<!-- A correction, a translation fix, a new language, or a layout/accessibility fix. -->

## Kind

- [ ] A claim corrected (the page said something `spec/` or `compiler/` does not support)
- [ ] Translation fix
- [ ] New language
- [ ] Layout / accessibility fix

## Sources

<!--
If you added or changed a claim, name the file and line in `spec/` or `compiler/` it comes
from, and add the row to the table in README.md. No benchmark numbers: the harness has no
versioned results, and a timing without its machine is not a measurement.
-->

## Checklist

- [ ] The change is applied to **all three** pages (`index.html`, `ru/`, `zh/`), or is
      genuinely specific to one language
- [ ] No horizontal scrolling at 375, 640, 900 and 1440 px
- [ ] Local links resolve — including from `ru/` and `zh/`, and when opened over `file://`
- [ ] No CSS rule left with nothing using it, and no class left without a rule
- [ ] Code samples still match the specification character for character; only prose and
      code comments are translated
