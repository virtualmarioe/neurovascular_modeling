# Neurovascular Modeling — Project Website

A static project website for the NeuroImage (2020) article:

> **Modeling the impact of neurovascular coupling impairments on BOLD-based functional connectivity at rest**
> Mario E. Archila-Meléndez, Christian Sorg, Christine Preibisch.
> *NeuroImage* **218** (2020), 116871.
> DOI: [10.1016/j.neuroimage.2020.116871](https://doi.org/10.1016/j.neuroimage.2020.116871)

The site explains the paper's motivation and results for a broad audience, and
ships with three self-contained **in-browser simulations** that reproduce the
qualitative behaviour of the paper's adjusted balloon model:

1. **Balloon Model Explorer** — tweak CBF, CMRO<sub>2</sub> and CBV dynamics
   and watch the resulting BOLD signal.
2. **BOLD-FC Simulator** — compare two simulated regions (seed vs. target),
   see both BOLD time courses and a live Pearson correlation / scatter plot.
3. **Scenario Heatmap** — 2-D landscapes of BOLD-FC over pairs of physiological
   parameters for each of the three scenarios (amplitudes / delays / CBV).

All demos use a linearised Davis-style BOLD model
(ΔBOLD/B<sub>0</sub> ≈ M · [(β − α)·ΔCBF/CBF<sub>0</sub>
− β·ΔCMRO<sub>2</sub>/CMRO<sub>2,0</sub>]) and run entirely in the browser
with no external libraries.

## Site sections

- **Overview** — TL;DR and pipeline teaser.
- **Background: why the plumbing matters** — primer on BOLD, CBF, CMRO<sub>2</sub>,
  CBV and neurovascular coupling.
- **Abstract** — the published abstract verbatim.
- **Methods at a glance** — four-step simulation pipeline.
- **Inside the balloon model** — explainer plus Balloon Model Explorer demo.
- **Three simulation scenarios** — illustrated summary cards.
- **BOLD-FC simulator** — interactive two-region simulator with scatter plot.
- **Scenario heatmap** — 2-D BOLD-FC landscape for each scenario.
- **Key findings** — six take-aways from the paper.
- **Clinical implications** — what the results mean for rs-fMRI practice.
- **Glossary** — quick reference for all acronyms and concepts.
- **Authors** — corresponding author, co-authors and funding.
- **Cite this work** — one-click BibTeX citation.

## Structure

```
.
├── index.html                # Single-page project website (HTML + inline CSS/JS)
├── files/
│   └── images/
│       ├── logo.png          # Project logo / favicon
│       ├── teaser.png        # Hero / overview teaser figure
│       ├── scenario1.png     # Illustration for scenario 1 (amplitudes)
│       ├── scenario2.png     # Illustration for scenario 2 (delays)
│       └── scenario3.png     # Illustration for scenario 3 (CBF–CBV coupling)
├── .github/
│   └── workflows/
│       └── deploy.yml        # GitHub Pages deployment workflow
├── LICENSE                   # MIT (website code)
└── README.md
```

The site is intentionally dependency-free: plain HTML with inline CSS and
vanilla JavaScript (all SVG plots are drawn by hand, no external charting
library). No build step is required.

## Local preview

From the project root:

```bash
# Python 3
python3 -m http.server 8000
```

Then open <http://localhost:8000> in your browser.

Alternatively, with Node.js:

```bash
npx --yes serve .
```

## Deployment (GitHub Pages)

This repository ships with a workflow at `.github/workflows/deploy.yml` that
publishes the site to GitHub Pages on every push to `main`.

To enable it once:

1. Go to **Settings → Pages** in the GitHub UI.
2. Under **Build and deployment**, set **Source** to **GitHub Actions**.
3. Push to `main`; the workflow will deploy the site automatically.

The site will then be served at
`https://<your-username>.github.io/neurovascular_modeling/`.

## Content

All figures in `files/images/` are schematic illustrations generated for this
summary website; they are not the original journal figures. The paper itself
should be consulted for the complete results, equations and figures. The
interactive demos reproduce the qualitative behaviour of the paper's three
scenarios but use a simplified linearised model intended for pedagogical
exploration, not quantitative reanalysis.

## Citation

```bibtex
@article{ArchilaMelendez2020neurovascular,
  title   = {Modeling the impact of neurovascular coupling impairments on {BOLD}-based functional connectivity at rest},
  author  = {Archila-Mel{\'e}ndez, Mario E. and Sorg, Christian and Preibisch, Christine},
  journal = {NeuroImage},
  volume  = {218},
  pages   = {116871},
  year    = {2020},
  month   = sep,
  doi     = {10.1016/j.neuroimage.2020.116871},
  issn    = {1053-8119},
  publisher = {Elsevier}
}
```

## License

- The **website code** (HTML/CSS/JS in this repository) is released under the
  [MIT License](./LICENSE).
- The **published article** is distributed under
  [CC BY-NC-ND 4.0](https://creativecommons.org/licenses/by-nc-nd/4.0/) by the
  authors and Elsevier. Please consult the publisher's page for the canonical
  version of record.
