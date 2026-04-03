# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

Educational bioinformatics resources for two courses at Gebze Technical University:
- **BSB511** — Bioinformatics Fundamentals (graduate)
- **BENG451** — Introduction to Bioinformatics (undergraduate)

Content lives in three areas: `docs/` (interactive web widgets), `exercises/` (Jupyter notebooks), and `homeworks/` (PDF assignments).

## Development: Interactive Widgets (`docs/`)

**No build step required.** Each widget is a self-contained HTML file. Open any `.html` directly in a browser.

To preview locally, use any static file server:
```bash
python3 -m http.server 8080 --directory docs/
# Then open http://localhost:8080
```

Or just double-click the HTML file — they work offline after the first load caches CDN scripts.

## Widget Architecture

All widgets in `docs/` share the same pattern:

- **Runtime**: React 18 + Babel Standalone loaded from `unpkg.com` CDN. JSX is compiled in the browser at load time via `<script type="text/babel">`.
- **No npm, no bundler, no dependencies to install.** All logic is inside the single HTML file.
- **Structure of each widget file:**
  1. `<head>`: Google Fonts (Nunito / Nunito Sans) + minimal inline CSS for the back-link button
  2. `<body>`: `<div id="root">` + three CDN `<script>` tags + one `<script type="text/babel">` containing all React component code
- **Back navigation**: Every widget has a fixed `← All Widgets` link pointing to `index.html`.

**Visual theme** (consistent across all widgets, matching costbio.github.io):
- Primary color: `#2a7f8a` (teal)
- Hover/accent background: `#e8f4f6`, border: `#b8dce2`
- Fonts: `Nunito` (headings), `Nunito Sans` (body)
- Background: `#f8f9fa`

**Landing page** (`index.html`): Card grid linking to all widgets. To add a new widget, add a `<a class="card" href="new-widget.html">` entry inside `<div class="grid">`.

## Current Widgets

| File | Topic |
|------|-------|
| `dna-explorer.html` | Central dogma (transcription, translation, 6-frame reading, codon table) |
| `sanger-sequencing.html` | Chain termination: fragment generation, gel electrophoresis, chromatogram |
| `short-read-sequencing.html` | Illumina sequencing-by-synthesis, FASTQ quality, read pileups, coverage |
| `long-read-sequencing.html` | PacBio SMRT / Oxford Nanopore, ZMW, ionic current, CCS/HiFi |
| `fasta-blast.html` | FASTA k-tuple diagonal scoring + BLAST word seeding / HSP extension, E-value |
| `alignment-sandbox.html` | Interactive Needleman-Wunsch & Smith-Waterman DP matrix (hand-fill + check) |
| `motif-finder.html` | PROSITE pattern scanning on protein & DNA sequences |
| `phylo-interpreter.html` | UPGMA & Neighbor-Joining step-by-step tree building, Newick export |
| `scoring-matrices.html` | Dayhoff PAM construction, PAM1→PAM250 by matrix exponentiation, interactive globin sequence database builder, PAM1/30/250 explorer |
| `big-o-complexity.html` | Big-O growth curves, bioinformatics algorithm browser by complexity class, 8-question quiz |
| `hmm-hmmer.html` | Profile HMM architecture (match/insert/delete states), MSA→profile builder, Viterbi log-odds scoring, 8-question quiz |

## Exercises (`exercises/`)

Jupyter notebooks — run with a standard Python environment that has Biopython installed:
```bash
pip install biopython
jupyter notebook exercises/
```

Notebooks cover: Needleman-Wunsch (simple + PAM250), Smith-Waterman, Biopython GenBank / pairwise alignment, BLAST + MSA + phylogeny.

## Deployment

The `docs/` folder deploys to GitHub Pages (push to `main`, Pages source set to `/docs`). No CI configuration needed.
