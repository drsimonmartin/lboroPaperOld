# Loughborough Committee Paper: Quarto extension

This custom-format extension is based on the supplied 2025 committee-paper coversheet. It provides both Word and PDF output from one `.qmd` source.

## Requirements

- Quarto
- For DOCX: no extra rendering software is normally required beyond Quarto/Pandoc.
- For PDF: a TeX installation is required. `quarto install tinytex` is the simplest Quarto-managed option if you do not already have TeX.

## Install once for repeated use

The most portable method is to keep this repository in GitHub (or another shared location), then initialise each new paper with:

```bash
quarto use template YOUR-ORG/loughborough-committee-paper
```

This creates a new working directory containing `template.qmd` and the extension beneath `_extensions/`.

For a local copy of this package, run `quarto use template /path/to/loughborough-committee-paper` from the parent folder where you want the new paper.

If adding only the extension to an existing Quarto project, use:

```bash
quarto add YOUR-ORG/loughborough-committee-paper
```

Then use the formats `committee-paper-docx` and `committee-paper-pdf` in the document YAML.

## Render

Render both formats declared in `template.qmd`:

```bash
quarto render template.qmd
```

Or render one format explicitly:

```bash
quarto render template.qmd --to committee-paper-docx
quarto render template.qmd --to committee-paper-pdf
```

## Reusing the template across folders

Quarto extensions are normally installed into a project or copied in with a starter template. For repeat use across unrelated folders, a small Git repository is recommended rather than maintaining duplicate manual copies. Put this package at the root of a repository, commit it, and use `quarto use template ...` whenever starting a new committee paper. Colleagues can use the same command, so the template has one maintainable source.

For institutional use, replace `YOUR-ORG/loughborough-committee-paper` with the actual repository path and tag releases (for example `@v1.0.0`) when you want stable, reproducible versions.

## Metadata fields

Edit these fields in the YAML at the top of `template.qmd`:

- `title`
- `committee`
- `paper-reference`
- `origin`
- `action`
- `action-detail`

The body then contains the standard sections from the supplied template: Executive Summary, Other Committees Consulted, EDI Considerations, Paper Details, and Supplementary Reading.

## Design notes

- DOCX uses the supplied Word document as `reference-doc`, retaining its page setup and Word styles.
- PDF uses an A4 LaTeX format with Helvetica/Arial-like sans-serif typography, compact margins, 1.5 line spacing, paper reference in the header, institutional copyright footer, and an outlined Action Required box.
- Because Word reference documents and LaTeX are different layout engines, the two outputs are designed to be visually consistent rather than pixel-identical.
