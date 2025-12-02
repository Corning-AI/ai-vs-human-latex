# LaTeX Techniques Guide | LaTeX技巧指南

This document provides a comprehensive guide to the advanced LaTeX techniques used in this IEEE TPEL journal paper.

本文档全面介绍了这篇IEEE TPEL期刊论文中使用的高级LaTeX技巧。

---

## Table of Contents | 目录

1. [Package Organization](#1-package-organization--宏包组织)
2. [Mathematical Typesetting](#2-mathematical-typesetting--数学公式排版)
3. [Professional Tables](#3-professional-tables--专业表格)
4. [Figure Management](#4-figure-management--图片管理)
5. [IEEE Formatting](#5-ieee-formatting--ieee格式)
6. [Custom Commands](#6-custom-commands--自定义命令)
7. [Spacing Control](#7-spacing-control--间距控制)

---

## 1. Package Organization | 宏包组织

### Core Package Stack

```latex
% Document class
\documentclass[journal]{IEEEtran}

% Mathematics
\usepackage{amsmath}      % Core math environments
\usepackage{amssymb}      % Mathematical symbols
\usepackage{empheq}       % Emphasized equations
\usepackage{steinmetz}    % Phasor notation (\phase{})

% Tables
\usepackage{booktabs}     % Professional rules (\toprule, \midrule, \bottomrule)
\usepackage{multirow}     % Row spanning
\usepackage{makecell}     % Multi-line cells
\usepackage{threeparttable} % Table footnotes
\usepackage{array}        % Extended column specifications

% Figures
\usepackage{graphicx}     % \includegraphics
\usepackage{subfigure}    % Subfigures (deprecated but functional)
\usepackage{epstopdf}     % Automatic EPS to PDF conversion
\usepackage{float}        % H placement option

% Formatting
\usepackage{siunitx}      % SI units
\usepackage{hyperref}     % Hyperlinks
\usepackage{soul}         % Highlighting
\usepackage{color}        % Colors
\usepackage{colortbl}     % Table cell colors

% Layout
\usepackage{stfloats}     % Better float positioning
\usepackage{balance}      % Column balancing
\usepackage{cuted}        % Strip environments
```

### Package Conflict Resolution

```latex
% Soul package needs registration for citations
\soulregister\cite7
\soulregister\eqref7
\soulregister\ref7
```

---

## 2. Mathematical Typesetting | 数学公式排版

### Multi-line Equations with Custom Tags

```latex
\begin{align}
  \tag{1}
  B_x|_{i,j} &= \sum\limits_{i=1}^m \sum\limits_{j=1}^n B_{x,i,j}
\end{align}
```

### Vector and Matrix Notation

```latex
% Overline for average
\overline{B_{i,j}}

% Hat for unit vectors
\hat{r}_{i,j}

% Complex subscripts
I_{i,j}^m

% Evaluation at point
B_x|_{i,j}
```

### Biot-Savart Law Example

```latex
\begin{align}
  \vec{B}_{i,j}(\vec{r}) &= \frac{\mu_0 I_{i,j}}{4\pi}
    \oint \frac{d\vec{l} \times \hat{r}_{i,j}}{r_{i,j}^2}
\end{align}
```

### Phasor Notation

```latex
\usepackage{steinmetz}

% Usage
V = 10\phase{30^\circ}  % Renders as 10∠30°
```

### Delimiter Scaling

```latex
% Manual scaling
\left( \frac{a}{b} \right)
\left[ \sum_{i=1}^n x_i \right]
\left\{ \begin{array}{l} ... \end{array} \right.
```

---

## 3. Professional Tables | 专业表格

### Basic Booktabs Table

```latex
\begin{table}[h]
\centering
\caption{Parameters of Tx Coils}
\renewcommand\arraystretch{1.1}  % Increase row height
\begin{tabular}{l c c c}
  \toprule[1pt]
  \\[-3mm]  % Reduce space after rule
  \textbf{Parameter} & \textbf{Symbol} & \textbf{Value} & \textbf{Unit} \\
  \midrule[0.5pt]
  Coil length & $l$ & 9 & cm \\
  Wire width & $w$ & 0.2 & cm \\
  \bottomrule[1pt]
\end{tabular}
\end{table}
```

### Table with Embedded Images

```latex
\begin{table}[h]
\centering
\begin{tabular}{c c c}
  \toprule[1pt]
  \textbf{Scene} & \textbf{Image} & \textbf{Result} \\
  \midrule[0.5pt]
  Case 1 &
  \begin{minipage}[b]{0.35\columnwidth}
    \centering
    \raisebox{-.5\height}{%
      \includegraphics[width=1.0\linewidth]{fig/figTableIVa.eps}
    }
  \end{minipage} &
  $\eta = 82.1\%$ \\
  \bottomrule[1pt]
\end{tabular}
\end{table}
```

### Multi-row Spanning with Offset

```latex
\multirow{2}{*}[-10pt]{Centered text}  % 2 rows, auto-width, -10pt offset
\multirow{4}{*}[-20pt]{Spanning text}  % 4 rows, larger offset
```

### Multi-line Cells

```latex
\usepackage{makecell}

% Centered multi-line cell
\makecell[c]{Line 1 \\ Line 2 \\ Line 3}

% Left-aligned
\makecell[l]{First line \\ Second line}
```

### Table Footnotes

```latex
\usepackage{threeparttable}

\begin{threeparttable}
  \begin{tabular}{l c}
    \toprule
    Item & Value\tnote{*} \\
    \midrule
    Data & 100 \\
    \bottomrule
  \end{tabular}
  \begin{tablenotes}
    \footnotesize
    \item[*] This is a footnote
  \end{tablenotes}
\end{threeparttable}
```

### Partial Horizontal Rules

```latex
\cmidrule[0.4pt](lr){1-1}   % Rule under column 1, with left-right padding
\cmidrule[0.4pt](lr){2-6}   % Rule under columns 2-6
```

---

## 4. Figure Management | 图片管理

### Basic Figure

```latex
\begin{figure}[b!]
  \centering
  \includegraphics[width=8cm]{fig/fig1.eps}
  \caption{An extendable planar Tx-coil array.}
  \label{fig:array}
\end{figure}
```

### Subfigures (2x2 Layout)

```latex
\begin{figure}[h]
  \centering
  \subfigure[]{
    \label{fig:sub1}
    \includegraphics[height=3.5cm]{fig/fig3a.eps}
  }
  \subfigure[]{
    \label{fig:sub2}
    \includegraphics[height=3.5cm]{fig/fig3b.eps}
  }\\
  \subfigure[]{
    \label{fig:sub3}
    \includegraphics[height=3.5cm]{fig/fig3c.eps}
  }
  \subfigure[]{
    \label{fig:sub4}
    \includegraphics[height=3.5cm]{fig/fig3d.eps}
  }
  \caption{B-field at different times. (a) $\omega t=0$. (b) $\omega t=\pi/4$.
           (c) $\omega t=\pi/2$. (d) $\omega t=3\pi/4$.}
  \label{fig:bfield}
\end{figure}
```

### Two-column Figure

```latex
\begin{figure*}[ht!]
  \centering
  \subfigure[]{...}
  \subfigure[]{...}
  \subfigure[]{...}
  \caption{Wide figure spanning both columns.}
  \label{fig:wide}
\end{figure*}
```

### Asymmetric Layout

```latex
\begin{figure}[h]
  \centering
  \subfigure[]{
    \includegraphics[width=6.5cm]{fig/fig7a.eps}
  }\\
  \subfigure[]{\includegraphics[width=4.22cm]{fig/fig7b.eps}}
  \hspace{0.3cm}
  \subfigure[]{\includegraphics[width=4.22cm]{fig/fig7c.eps}}\\
  \subfigure[]{\includegraphics[width=4.22cm]{fig/fig7d.eps}}
  \hspace{0.3cm}
  \subfigure[]{\includegraphics[width=4.22cm]{fig/fig7e.eps}}
  \caption{...}
\end{figure}
```

### EPS to PDF Conversion

```latex
\usepackage{epstopdf}

% Automatic conversion when using pdflatex
\includegraphics{fig/figure.eps}
% Creates: figure-eps-converted-to.pdf
```

### Placement Options

| Option | Meaning |
|--------|---------|
| `h` | Here (approximately) |
| `t` | Top of page |
| `b` | Bottom of page |
| `p` | Special float page |
| `!` | Override internal parameters |
| `H` | Exactly here (requires `float` package) |

---

## 5. IEEE Formatting | IEEE格式

### Document Class

```latex
\documentclass[journal]{IEEEtran}

% Options:
% journal     - Two-column journal format
% conference  - Conference paper format
% onecolumn   - Single column
% draftclsnofoot - Draft mode without footer
```

### Author Block

```latex
\author{
  First~Author,~\IEEEmembership{Student Member,~IEEE,}
  Second~Author,~\IEEEmembership{Member,~IEEE,}\\
  Third~Author,~\IEEEmembership{Senior Member,~IEEE}

  \thanks{Manuscript received...}
  \thanks{This work was supported by...}
  \thanks{Affiliation information...}
}
```

### Column Balancing

```latex
% At the right position in the first column of first page
\IEEEpubidadjcol
```

### Author Biography

```latex
\begin{IEEEbiography}[{%
  \includegraphics[width=1in,height=1.25in,clip,keepaspectratio]{author.eps}
}]{Author Name}
Biography text here...
\end{IEEEbiography}
```

### Abstract and Keywords

```latex
\begin{abstract}
  This paper presents...
\end{abstract}

\begin{IEEEkeywords}
  Keyword1, keyword2, keyword3.
\end{IEEEkeywords}
```

---

## 6. Custom Commands | 自定义命令

### Custom Horizontal Rules

```latex
\def\hrulefill{\leavevmode\leaders\hrule height 0.8pt\hfill\kern0pt}

\makeatletter
\def\rulefill{\leavevmode\leaders\hrule depth -3pt height 4pt\hfill\kern0pt}
\makeatother
```

### Custom Colors

```latex
\definecolor{limegreen}{rgb}{0.2, 0.8, 0.2}
\definecolor{forestgreen}{rgb}{0.13, 0.55, 0.13}
\definecolor{greenhtml}{rgb}{0.0, 0.5, 0.0}
```

### Resizable Tables

```latex
\resizebox{\columnwidth}{!}{%
  \begin{tabular}{...}
    ...
  \end{tabular}
}
```

---

## 7. Spacing Control | 间距控制

### Vertical Spacing

```latex
% Negative space after rules in tables
\\[-3mm]
\\[-2mm]
\\[-1mm]

% Space between figures
\vspace{-0.3cm}
\vspace{-0.5cm}
\vspace{-0.8cm}
```

### Horizontal Spacing

```latex
% Between subfigures
\hspace{0.3cm}
\hspace{1.3cm}
\hspace{-0.1cm}  % Negative for tighter spacing
```

### Row Height in Tables

```latex
\renewcommand\arraystretch{1.0}  % Default
\renewcommand\arraystretch{1.1}  % 10% taller
\renewcommand\arraystretch{1.2}  % 20% taller
\renewcommand\arraystretch{1.3}  % 30% taller
```

### Strip Environment (Full-width in Two-column)

```latex
\usepackage{cuted}
\stripsep -3pt plus 3pt minus 2pt

\begin{strip}
  % Full-width content in two-column document
\end{strip}
```

---

## Quick Reference | 快速参考

### Common Mistakes to Avoid | 常见错误

| Mistake | Correct |
|---------|---------|
| `\includegraphics{fig.eps}` without path | `\includegraphics{fig/fig.eps}` |
| Missing `\\` between subfigure rows | Add `\\` for line breaks |
| Wrong placement option order | Use `[ht!]` not `[!ht]` |
| Forgetting `\label` after `\caption` | Always add `\label` |
| Using `\\ ` inside paragraph | Use blank line instead |

### Compilation Order | 编译顺序

```bash
pdflatex document.tex   # First pass
bibtex document         # Process bibliography
pdflatex document.tex   # Resolve references
pdflatex document.tex   # Final pass for cross-refs
```

---

## Resources | 资源

- [IEEEtran Documentation](https://ctan.org/pkg/ieeetran)
- [Booktabs Package Guide](https://ctan.org/pkg/booktabs)
- [AMS-LaTeX Documentation](https://ctan.org/pkg/amsmath)
- [LaTeX Wikibook](https://en.wikibooks.org/wiki/LaTeX)

---

<p align="center">
  <em>Master these techniques, and you'll produce publication-quality documents.</em><br>
  <em>掌握这些技巧，您就能制作出出版级质量的文档。</em>
</p>
