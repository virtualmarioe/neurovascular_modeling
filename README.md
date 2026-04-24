# Neurovascular Modeling: Project Website

A static project website for the NeuroImage (2020) article:

> **Modeling the impact of neurovascular coupling impairments on BOLD-based functional connectivity at rest**
> Mario E. Archila-Meléndez, Christian Sorg, Christine Preibisch.
> *NeuroImage* **218** (2020), 116871.
> DOI: [10.1016/j.neuroimage.2020.116871](https://doi.org/10.1016/j.neuroimage.2020.116871)

The site explains the paper's motivation and results for a broad audience, and
ships with three self-contained **in-browser simulations** that reproduce the
qualitative behaviour of the paper's adjusted balloon model:

1. **Balloon Model Explorer**: tweak CBF, CMRO<sub>2</sub> and CBV dynamics
   and watch the resulting BOLD signal.
2. **BOLD-FC Simulator**: compare two simulated regions (seed vs. target),
   see both BOLD time courses and a live Pearson correlation / scatter plot.
3. **Scenario Heatmap**: 2-D landscapes of BOLD-FC over pairs of physiological
   parameters for each of the three scenarios (amplitudes / delays / CBV).

All demos use a linearised Davis-style BOLD model
(ΔBOLD/B<sub>0</sub> ≈ M · [(β − α)·ΔCBF/CBF<sub>0</sub>
− β·ΔCMRO<sub>2</sub>/CMRO<sub>2,0</sub>]) and run entirely in the browser
with no external libraries.

The Scenario Heatmap follows the paper's methodology more closely than the
single-tone demos: the seed and target regions are driven by a shared
broadband signal filtered to the canonical resting-state band
(0.01–0.1 Hz, sampled at TR = 2 s over 6 min), the Pearson correlation of
each parameter combination is averaged over four independent Monte-Carlo
realisations of drive and measurement noise, and the grid is refined to
41 × 41 cells with a bilinear interpolation overlay for smooth rendering.

## Site sections

The page follows the reader-first arc of the paper, then opens into
pedagogical deep dives and interactive demos, and closes with reference
material and authorship.

**Paper arc**

- **Overview**: TL;DR and pipeline teaser.
- **Abstract**: the published abstract verbatim.
- **Methods at a glance**: four-step simulation pipeline.
- **Three simulation scenarios**: illustrated summary cards for the three
  manipulations (amplitudes, delays, CBF-CBV coupling).
- **Key findings**: six take-aways from the paper.
- **Clinical implications**: what the results mean for rs-fMRI practice.

**Deep dives and interactive demos**

- **Background: why the vasculature matters**: primer on BOLD, CBF,
  CMRO<sub>2</sub>, CBV and neurovascular coupling.
- **Inside the balloon model**: explainer plus Balloon Model Explorer demo.
- **BOLD-FC simulator**: interactive two-region simulator with scatter plot.
- **Scenario heatmap**: 2-D BOLD-FC landscape for each scenario.

**Reference and meta**

- **Glossary**: quick reference for all acronyms and concepts.
- **Educational disclaimer & resources**: explicit "toy example" notice plus
  links to the peer-reviewed article, the Zenodo data/code archive, and the
  GitLab Matlab simulation source.
- **Authors & contributions**: per-author CRediT-style contribution
  statements, plus a nested BibTeX card with one-click copy.

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

## Educational disclaimer and resources

All explainers, figures and in-browser simulators on this site are **toy
examples for educational purposes only**. They rely on a linearised
Davis-style BOLD model and a small set of synthetic inputs, deliberately
sacrificing numerical fidelity for interactivity. They are *not* a
reproduction of the paper's quantitative analyses and should not be used for
scientific reanalysis, clinical inference, or benchmarking.

The schematic figures in `files/images/` are illustrations generated for this
companion site; they are not the original journal figures.

For anything serious, use the primary sources, all open access:

- Peer-reviewed article (full methods, statistics and discussion):
  <https://doi.org/10.1016/j.neuroimage.2020.116871>
- Data and custom Matlab code (Zenodo, citable archive):
  <https://zenodo.org/record/3773316>
- Matlab BOLD simulation source (GitLab LRZ, maintained by the authors):
  <https://gitlab.lrz.de/nmrm_lab/public_projects/bold-simulation>

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
