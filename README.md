# Can Top AI Beat Top Human LaTeX Engineering?

<p align="center">
  <img src="https://img.shields.io/badge/LaTeX-008080?style=for-the-badge&logo=latex&logoColor=white" alt="LaTeX"/>
  <img src="https://img.shields.io/badge/IEEE-00629B?style=for-the-badge&logo=ieee&logoColor=white" alt="IEEE"/>
  <img src="https://img.shields.io/badge/License-CC%20BY--NC%204.0-lightgrey?style=for-the-badge" alt="License"/>
  <img src="https://img.shields.io/badge/Era-Pre--AI%20(2023)-orange?style=for-the-badge" alt="Pre-AI Era"/>
</p>

<p align="center">
  <strong>A Complete IEEE Top Journal LaTeX Project | Human Benchmark Edition</strong>
</p>

<p align="center">
  <a href="README_CN.md">中文文档</a> |
  <a href="TECHNIQUES.md">LaTeX Techniques Guide</a> |
  <a href="Latex/arrayTX-TPEL.pdf">View PDF</a>
</p>

---

## Overview

This repository contains the **complete LaTeX source code** for the IEEE Transactions on Power Electronics (TPEL) paper:

> **"Analysis and Implementation of 3D Magnetic Field Shaping via A 2D Planar Transmitting Coil Array"**

This project was crafted in **July 2023**, before the widespread adoption of Large Language Models (LLMs) in academic writing. It represents the pinnacle of **human-crafted LaTeX engineering** for IEEE journal submissions.

### Why Open Source This?

1. **Educational Resource**: Demonstrate advanced LaTeX typesetting techniques for IEEE journals
2. **Benchmark for AI**: Establish a human baseline for future AI-enhanced LaTeX comparison
3. **Knowledge Sharing**: Help researchers master professional academic document preparation

---

## Paper Information

| Item | Details |
|------|---------|
| **Title** | Analysis and Implementation of 3D Magnetic Field Shaping via A 2D Planar Transmitting Coil Array |
| **Authors** | Ning Kang, Yaoxia Shao, Ming Liu, Chengbin Ma |
| **Journal** | IEEE Transactions on Power Electronics (TPEL) |
| **Year** | 2021 |
| **Affiliation** | Shanghai Jiao Tong University |
| **Keywords** | Wireless Power Transfer, Magnetic Field Shaping, Planar Coil Array, MHz WPT |

---

## Project Highlights

### By the Numbers

| Metric | Count |
|--------|-------|
| LaTeX Packages Used | **30+** |
| Mathematical Equations | **130+** |
| Figures | **18** (with 48 subfigures) |
| Professional Tables | **6** |
| Lines of LaTeX Code | **900+** |
| Delimiter Pairs | **47** |

### Advanced LaTeX Techniques

#### 1. Complex Mathematical Typesetting
- Multi-line `align` environments with custom equation tagging
- Biot-Savart law derivations with nested integrals
- Vector notation: `\overline{}`, `\hat{}`, complex subscript/superscript
- Phasor notation using `steinmetz` package

```latex
\begin{align}
  \overline{B_{i,j}} = \frac{\mu_0 I_{i,j}}{4\pi} \oint \frac{d\vec{l} \times \hat{r}_{i,j}}{r_{i,j}^2}
\end{align}
```

#### 2. Professional Table Design
- Embedded images within table cells using `minipage` + `raisebox`
- Multi-row spanning with precise vertical offset control
- Fine-tuned spacing: `\\[-3mm]`, `\arraystretch{1.1}`
- Table footnotes with `threeparttable`

```latex
\begin{minipage}[b]{0.35\columnwidth}
  \centering
  \raisebox{-.5\height}{\includegraphics[width=1.0\linewidth]{fig/figTableIVa.eps}}
\end{minipage}
```

#### 3. Sophisticated Figure Management
- 2x2, 2x3, and asymmetric subfigure layouts
- Dual format strategy: EPS source with automatic PDF conversion
- Precise spacing control with `\vspace{}` and `\hspace{}`
- Two-column spanning figures with `figure*`

#### 4. IEEE Journal Compliance
- Full `IEEEtran` document class implementation
- Proper author formatting with IEEE membership
- Copyright notices and funding acknowledgments
- Biography sections with photos

---

## Project Structure

```
finalPackage/
├── Latex/
│   ├── arrayTX-TPEL.tex      # Main LaTeX source (900+ lines)
│   ├── arrayTX-TPEL bk.tex   # Backup version
│   ├── arrayTX-TPEL.pdf      # Compiled output
│   ├── fig/                   # 57 EPS figures + PDF conversions
│   │   ├── fig1.eps          # System overview
│   │   ├── fig2.eps          # Circuit configuration
│   │   ├── fig3a-d.eps       # B-field calculations
│   │   └── ...
│   ├── Bibliography/
│   │   ├── myRef.bib         # Paper references
│   │   ├── IEEEabrv.bib      # IEEE abbreviations
│   │   └── IEEEfull.bib      # IEEE full names
│   ├── NingKang.eps          # Author photo
│   ├── YaoxiaShao.eps        # Author photo
│   ├── MingLiu.eps           # Author photo
│   └── ChengbinMa.eps        # Author photo
├── figures/                   # High-resolution source figures
├── author photos/             # Original author photos
├── .gitignore
├── README.md                  # This file
├── README_CN.md               # Chinese documentation
├── TECHNIQUES.md              # Detailed techniques guide
└── LICENSE                    # CC BY-NC 4.0
```

---

## How to Compile

### Prerequisites
- TeX Live 2020+ or MiKTeX
- `pdflatex` with `epstopdf` support

### Compilation Steps

```bash
cd Latex/
pdflatex arrayTX-TPEL.tex
bibtex arrayTX-TPEL
pdflatex arrayTX-TPEL.tex
pdflatex arrayTX-TPEL.tex
```

Or using `latexmk`:
```bash
latexmk -pdf arrayTX-TPEL.tex
```

---

## Key Packages Used

| Category | Packages |
|----------|----------|
| **Mathematics** | `amsmath`, `amssymb`, `empheq`, `steinmetz` |
| **Tables** | `booktabs`, `multirow`, `makecell`, `threeparttable`, `array` |
| **Figures** | `graphicx`, `subfigure`, `epstopdf`, `float` |
| **Formatting** | `siunitx`, `hyperref`, `soul`, `color`, `colortbl` |
| **Layout** | `stfloats`, `balance`, `cuted`, `multicol` |
| **IEEE** | `IEEEtran` (document class) |

---

## Citation

If you use this LaTeX template or find it helpful, please cite the original paper:

```bibtex
@article{kang2021analysis,
  author  = {Kang, Ning and Shao, Yaoxia and Liu, Ming and Ma, Chengbin},
  title   = {Analysis and Implementation of 3D Magnetic Field Shaping
             via A 2D Planar Transmitting Coil Array},
  journal = {IEEE Transactions on Power Electronics},
  year    = {2021},
  volume  = {37},
  number  = {2},
  pages   = {2029-2043},
  doi     = {10.1109/TPEL.2021.3104954}
}
```

---

## Roadmap

- [x] **v1.0.0-human**: Human-crafted baseline (current release)
- [ ] **v2.0.0-ai**: AI-enhanced version (Claude/GPT optimization)
- [ ] **Comparison Report**: Quantitative analysis of human vs AI LaTeX

### The Experiment

> Can top-tier AI improve upon top-tier human LaTeX engineering?

This repository will serve as the **human benchmark**. Future releases will explore:
- AI-suggested code optimizations
- Alternative package selections
- Enhanced mathematical formatting
- Improved figure layouts

---

## License

This project is licensed under the **Creative Commons Attribution-NonCommercial 4.0 International License** (CC BY-NC 4.0).

You are free to:
- **Share** - copy and redistribute the material
- **Adapt** - remix, transform, and build upon the material

Under the following terms:
- **Attribution** - Give appropriate credit
- **NonCommercial** - Not for commercial purposes

See [LICENSE](LICENSE) for details.

---

## Acknowledgments

- **Authors**: Ning Kang, Yaoxia Shao, Ming Liu, Chengbin Ma
- **Institution**: Shanghai Jiao Tong University
- **Funding**: National Natural Science Foundation of China (Grant 52077132)

---

<p align="center">
  <strong>Crafted with precision by humans, before the AI era.</strong><br>
  <em>July 2023</em>
</p>
