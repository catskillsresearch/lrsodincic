[![Lean 4](https://img.shields.io/github/actions/workflow/status/catskillsresearch/lrsodincic/build.yml?label=Lean%204)](https://github.com/catskillsresearch/lrsodincic/actions/workflows/build.yml)

# LRSODInCIC

L/R/S/O/D axiom layers embedded in Lean 4's CIC — no Mathlib.

Scott's reflexive domain \(D_∞\) can be axiomatized in five layers:
**L** (logic), **R** (inference), **S** (capped set theory), **O** (point-set
topology), and **D** (domain-theoretic residue). This repository states those
20 axioms and 2 rules, states Lean 4's kernel calculus, and gives a deep
embedding of the layers in CIC without Mathlib and without
`Classical.choice`. The specialization order \(\sqsubseteq\) is recovered
from open sets. A Sierpiński-space witness discharges D1–D4.

This repository is the continuation of work that began as
[`scott_models/LRSODInCIC`](https://github.com/catskillsresearch/scott_models/tree/main/LRSODInCIC)
and was split out because it is not part of that project's intent. See
`PROVENANCE.md`. The old path is historical.

## Files

| File | Role |
|---|---|
| `LRSODInCIC.md` | Paper (axioms, CIC, translation) — the source of truth |
| `LRSODInCIC.lean` | Deep embedding, plus a Sierpiński-space witness for D1–D4 |
| `PROVENANCE.md` | Split from `scott_models/LRSODInCIC`; this repo is the continuation |
| `LRSODInCIC.pdf` | Paper PDF (committed deliverable; synced from `view.pdf`) |
| `view.pdf` | Official arXiv AutoTeX build (pdfLaTeX) |
| `build_pdf.py` | `LRSODInCIC.md` → `LRSODInCIC.tex` → `LRSODInCIC.pdf`, Lean source inlined as an appendix |
| `scripts/package_arxiv_submit.sh` | `dist/arxiv_submit.zip` for arXiv (pdfLaTeX + Lean listing) |
| `scripts/tex_preamble_arxiv.tex` | Listings / unicode preamble used by the PDF build |
| `LICENSE` | Apache License 2.0 |
| `NOTICE` | Copyright and third-party attribution |

`LRSODInCIC.tex` is generated and git-ignored. The title page lists the author,
ORCID, Catskills Research Company, and the GitHub URL.

## Build the Lean

Requires [elan](https://github.com/leanprover/elan) (or an equivalent Lean 4
install). The pin is `leanprover/lean4:v4.30.0`. There is no Mathlib
dependency.

```bash
lake build
```

Open `LRSODInCIC.lean` in this repository so the Lean server uses this
package's `lakefile.toml`.

## Build the paper

Needs `pandoc` and `latexmk`.

```bash
python3 build_pdf.py
bash scripts/package_arxiv_submit.sh   # dist/arxiv_submit.zip (rebuilds the PDF first)
```

`dist/arxiv_submit.zip` is the arXiv upload: `LRSODInCIC.tex`, `LRSODInCIC.lean`
(the `\lstinputlisting` appendix), and `00README.json` so AutoTeX keeps the Lean
file and compiles with pdfLaTeX. On arXiv Add Files, Delete All before
uploading; on Review Files, uncheck deletion if `LRSODInCIC.lean` is marked.
After a successful arXiv compile, save the preview PDF as `view.pdf` and copy it
to `LRSODInCIC.pdf` so the committed deliverable matches AutoTeX.

## License

Copyright 2026 Lars Warren Ericson. Licensed under the Apache License,
Version 2.0. See `LICENSE` and `NOTICE`.
