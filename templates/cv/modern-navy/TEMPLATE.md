# Template: modern-navy

- **Type:** CV
- **Source extension:** .tex
- **Engine/toolchain:** lualatex
- **Page limit:** 2 page(s)
- **Fonts:** TeX Gyre Heros (system font - must be installed; ships with any complete TeX Live/MiKTeX install, no separate bundling needed)
- **Class/packages:** standard `article` class, no custom `.cls`/`.sty`. Uses `fontspec`, `xcolor`, `hyperref`, `array`, `geometry` (all standard).

## Compile command

    cd cv && lualatex -interaction=nonstopmode <file>.tex

## Style rules

- Colors: navy `#1B3A5C` (headings, rules, name), gray `#555555` (dates, subtitles).
- Section order: Header -> Profil -> Berufserfahrung -> Projekte -> Ausbildung -> Ausserschulisches Engagement -> Technische Fähigkeiten -> Sprachen (add Relevante Fächer / Weiterbildung / Publications / Honors sections as needed to fill 2 pages).
- German-language design throughout, including section headings — this is the template's whole point, not something to translate per-application.
- Custom macros: `\cvsection{}` for section headers (bold navy label + full-width rule), `\entryhead{title}{dates}` and `\entrysub{subtitle}{location}` for each entry (title/dates on one line via `\hfill`, subtitle/location on the next).
- Compact spacing throughout: `\parskip=0pt`, custom `\@listI` override for zero-gap bullet lists (no `enumitem` dependency).
- Skills rendered as a two-column `tabular` (`>{\bfseries}p{4.4cm}` label column + wide value column), not a bullet list.

## Known pitfalls

- **Do not load `babel` or `polyglossia`** for German hyphenation — both trigger a MiKTeX on-the-fly package-install hang in sandboxed compile environments. Instead the template raises `\tolerance=2500`, `\emergencystretch=2.5em`, `\hbadness=10000` so long unhyphenated German compounds still fit the margin without hyphenation patterns.
- `TeX Gyre Heros` must be available to `fontspec`/lualatex; if a distro's TeX install is missing it, install the `tex-gyre` package rather than substituting a different sans font (changes the whole look).
- The two-column skills `tabular` uses fixed column widths (`4.4cm` + `12.9cm`) sized for A4 with the template's `1.15cm` margins — if margins change, the widths need re-tuning or the table overflows.
