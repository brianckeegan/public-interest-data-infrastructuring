# Public interest data infrastructuring

[![Build PDF](https://github.com/brianckeegan/public-interest-data-infrastructuring/actions/workflows/build.yml/badge.svg)](https://github.com/brianckeegan/public-interest-data-infrastructuring/actions/workflows/build.yml)

> ### 📄 [**Read the latest compiled PDF →**](https://github.com/brianckeegan/public-interest-data-infrastructuring/releases/latest/download/manuscript.pdf)
>
> Built automatically from [`!manuscript.tex`](!manuscript.tex) by GitHub Actions on every push to `main`.
> *(The link activates after the first successful build on `main`.)*

Source repository for the article **"Public interest data infrastructuring"** by
**Brian C. Keegan** (University of Colorado Boulder).

- **Author:** Brian C. Keegan · [ORCID 0000-0002-7793-398X](https://orcid.org/0000-0002-7793-398X) · brian.keegan@colorado.edu
- **Type:** Conceptual framework article (not an empirical study)
- **Status:** Working paper, prepared for submission to the ACM *Journal on Responsible Computing* (JRC)
- **Format:** LaTeX, ACM `acmart` document class (`acmsmall`)

---

## What the paper argues

Democratic societies have long relied on data to make public life visible and accountable.
For about a decade (2008–2018), platform APIs and data dumps extended that capacity to the
study of online life — and then it began to close. The paper diagnoses this closure as the
product of three mutually reinforcing structural forces, and proposes a constructive agenda
against them:

| Pressure | What it does | Countervailing value |
|---|---|---|
| **Enclosure** — *who can observe?* | Privatizes or withdraws once-public data (API shutdowns, paywalls, retired government datasets) | **Openness** — durable legibility of evidentiary traces |
| **Exemption** — *who must answer?* | Lets platforms and AI developers operate beyond meaningful regulatory scrutiny | **Oversight** — routinized, testable scrutiny |
| **Erosion** — *what can be remembered?* | Decays the archives, standards, and continuity that long-term, reproducible research needs | **Ownership** — stewardship obligations and collective governance |

The central theoretical move is to treat ***infrastructuring*** — the ongoing work of
maintaining an "installed base" of records, standards, interfaces, and governance routines —
as the mechanism that turns these values into durable accountability capacities. The paper
situates this project within five **public interest professional lineages** (journalism,
law, accounting, planning, engineering) and distinguishes it from adjacent **conversations**
(public interest technology, data for good, digital government, civic technology, critical
data studies, data justice).

Three speculative **case studies** stress-test the framework:

1. **Mining municipal archives** — local-government transparency as a lived civic service.
2. **Supporting worker observatories** — counter-records under adversarial platform control.
3. **Sustaining archives in the Anthropocene** — climate memory as intergenerational stewardship.

### Abstract

> Data-driven systems increasingly govern critical aspects of public life, yet access to the
> data and infrastructures necessary to study and oversee these systems is rapidly shrinking.
> This article defines "public interest data infrastructuring" as an emerging field that adapts
> the public missions of journalism, law, accounting, planning, and engineering to contemporary
> data-intensive environments. The article argues that public interest data infrastructuring
> arises in response to three structural dynamics: enclosure, whereby once-public data is
> privatized or restricted; exemption, whereby platforms and AI developers operate beyond
> meaningful regulatory scrutiny; and erosion, whereby fragmentation and infrastructural decay
> undermine long-term observation and reproducible research. Against these forces, the article
> advances a constructive agenda organized around openness, oversight, and ownership as
> countervailing pillars of accountability and stewardship. Public interest data infrastructuring
> is distinguished from adjacent efforts — including data for good, civic technology, critical
> data studies, and data justice — by its emphasis on building durable infrastructures and
> regulatory architectures for democratic oversight. Three case studies examining municipal
> archives, worker observatories, and Anthropocene data trusts illustrate how public interest
> data infrastructuring reimagines the relationships among data, power, and the public good. The
> article concludes by outlining how public interest data infrastructuring can establish
> foundations for future institutions grounded in contemporary regulatory precedents.

---

## Repository structure

```
.
├── !manuscript.tex          # The manuscript (single source file; all figures are inline TikZ)
├── bibliography.bib         # 511-entry bibliography, organized into thematic clusters
├── README.md                # This file
├── .github/workflows/
│   └── build.yml            # CI: compile the PDF on push; publish to the "latest" release
├── acmart.cls               # ACM article class (LaTeX Project Public License) — do not edit
├── acmart-tagged.cls        # Tagged/accessible ACM class variant
├── ACM-Reference-Format.bst # ACM BibTeX reference style (used by this build)
├── acmauthoryear.{bbx,cbx}  # ACM biblatex backends (author–year) — not used by the current build
├── acmnumeric.{bbx,cbx}     # ACM biblatex backends (numeric) — not used by the current build
├── acmdatamodel.dbx         # ACM biblatex data model
└── old/                     # Archived material (earlier drafts; not part of the build)
    ├── !manuscript_v1.tex
    ├── !manuscript_v2.tex
    └── bike_rack.txt         # Cut "RAG-augmented thematic grid search" section + working notes
```

The three figures (the pressures/values diagram, the six installed-base elements, and the
summary of cases) are drawn inline with **TikZ** — there are no external image files to manage.

---

## Building the PDF

The project compiles with a standard TeX Live (or MacTeX) installation. The bibliography uses
**classic BibTeX** via `\bibliographystyle{ACM-Reference-Format}`.

> **Note on the filename:** the main file is `!manuscript.tex`. The leading `!` is a shell
> history/metacharacter, so quote or escape it (`'!manuscript.tex'`).

**With `latexmk` (recommended):**

```sh
latexmk -pdf '!manuscript.tex'
```

**Manual sequence (equivalent):**

```sh
pdflatex '!manuscript.tex'
bibtex   '!manuscript'      # note: no extension
pdflatex '!manuscript.tex'
pdflatex '!manuscript.tex'
```

**Overleaf:** this repository is synced with Overleaf; pushing to/from the Git remote builds
automatically there. Set the main document to `!manuscript.tex`.

**Continuous integration:** the [`Build PDF`](.github/workflows/build.yml) GitHub Actions workflow
compiles the manuscript on every push to `main` (and on pull requests). Each run uploads the PDF as a
downloadable artifact; pushes to `main` additionally publish it to the rolling
[**`latest` release**](https://github.com/brianckeegan/public-interest-data-infrastructuring/releases/latest/download/manuscript.pdf),
which is the same link surfaced at the top of this README.

To remove build artifacts (`.aux`, `.bbl`, `.blg`, `.log`, `.out`, `.fls`, `.fdb_latexmk`, `.pdf`):

```sh
latexmk -C '!manuscript.tex'
```

---

## The bibliography

`bibliography.bib` is a master library of **511 references**, of which **183 are cited by this
paper**. It is organized into thematic clusters with `% ===` comment headers and a cluster index
at the top of the file; within each cluster, entries are sorted alphabetically by citation key.
A `% [cited in this paper]` marker precedes each entry the manuscript actually cites, so the
working set is easy to find. The clusters are:

- Labor, gig work, and algorithmic management
- Disinformation, hate speech, extremism, and online harms
- Health, well-being, and online communities
- Archives, digital preservation, climate memory, and deep time
- Content moderation and online community governance
- Platform data access and the post-API age
- Public interest technology, civic tech, and digital government
- Public interest professions and traditions (journalism, law, accounting, planning, engineering)
- Critical data studies, data justice, and data power
- Algorithmic accountability, auditing, fairness, and regulation
- Infrastructure studies, platform studies, standards, and data systems
- Computational social science, digital methods, and measurement
- Datasets, repositories, commons, and platform alternatives
- Miscellaneous and uncategorized

Cluster assignment is thematic and meant for human navigation; entry *order* does not affect the
compiled output (BibTeX selects entries by key), so references can be moved between sections
freely.

---

## How to cite

This is a working paper; the BibTeX entry below is a placeholder. Update the venue, year, and
DOI once the article is published.

```bibtex
@unpublished{keegan2026publicinterest,
  author = {Keegan, Brian C.},
  title  = {Public Interest Data Infrastructuring},
  year   = {2026},
  note   = {Working paper. Prepared for submission to the
            ACM Journal on Responsible Computing (JRC).}
}
```

---

## License

No license file is currently included. Unless and until one is added:

- The **manuscript text and figures** are © 2026 Brian C. Keegan, all rights reserved.
- The bundled ACM class and style files (`acmart.cls`, `acmart-tagged.cls`,
  `ACM-Reference-Format.bst`, the `acm*.bbx/.cbx/.dbx` files) are distributed by ACM under the
  **LaTeX Project Public License (LPPL)** and retain their own terms.

If you intend to share the source for reuse, consider adding an explicit `LICENSE` (for example,
CC BY 4.0 for the text and a permissive license for any code).
