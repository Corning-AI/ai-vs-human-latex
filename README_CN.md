# 顶尖AI能比顶尖人类工程更好么？

<p align="center">
  <img src="https://img.shields.io/badge/LaTeX-008080?style=for-the-badge&logo=latex&logoColor=white" alt="LaTeX"/>
  <img src="https://img.shields.io/badge/IEEE-00629B?style=for-the-badge&logo=ieee&logoColor=white" alt="IEEE"/>
  <img src="https://img.shields.io/badge/许可证-CC%20BY--NC%204.0-lightgrey?style=for-the-badge" alt="License"/>
  <img src="https://img.shields.io/badge/时代-前AI时代%20(2023)-orange?style=for-the-badge" alt="Pre-AI Era"/>
</p>

<p align="center">
  <strong>一个完整的IEEE顶刊LaTeX工程 | 人类基准版本</strong>
</p>

<p align="center">
  <a href="README.md">English</a> |
  <a href="TECHNIQUES.md">LaTeX技巧指南</a> |
  <a href="Latex/arrayTX-TPEL.pdf">查看PDF</a>
</p>

---

## 项目概述

本仓库包含IEEE电力电子汇刊（TPEL）论文的**完整LaTeX源代码**：

> **"基于二维平面发射线圈阵列的三维磁场整形分析与实现"**
>
> (Analysis and Implementation of 3D Magnetic Field Shaping via A 2D Planar Transmitting Coil Array)

这个项目创建于**2023年7月**，在大语言模型（LLM）广泛应用于学术写作之前。它代表了IEEE期刊投稿中**人类LaTeX工程的巅峰水平**。

### 为什么开源这个项目？

1. **教育资源**：展示IEEE期刊的高级LaTeX排版技巧
2. **AI基准测试**：为未来AI增强版LaTeX建立人类基准线
3. **知识共享**：帮助研究人员掌握专业学术文档制作

---

## 论文信息

| 项目 | 详情 |
|------|------|
| **标题** | Analysis and Implementation of 3D Magnetic Field Shaping via A 2D Planar Transmitting Coil Array |
| **中文标题** | 基于二维平面发射线圈阵列的三维磁场整形分析与实现 |
| **作者** | 康宁, 邵耀霞, 刘明, 马澄斌 |
| **期刊** | IEEE Transactions on Power Electronics (TPEL) |
| **年份** | 2021 |
| **单位** | 上海交通大学 |
| **关键词** | 无线电能传输, 磁场整形, 平面线圈阵列, MHz WPT |

---

## 项目亮点

### 数据一览

| 指标 | 数量 |
|------|------|
| 使用的LaTeX宏包 | **30+** |
| 数学公式 | **130+** |
| 图片 | **18** 张（含48个子图）|
| 专业表格 | **6** 个 |
| LaTeX代码行数 | **900+** |
| 定界符对数 | **47** |

### 高级LaTeX技巧

#### 1. 复杂数学公式排版
- 多行`align`环境与自定义公式编号
- Biot-Savart定律推导与嵌套积分
- 向量标记：`\overline{}`、`\hat{}`、复杂上下标
- 使用`steinmetz`宏包的相量表示

```latex
\begin{align}
  \overline{B_{i,j}} = \frac{\mu_0 I_{i,j}}{4\pi} \oint \frac{d\vec{l} \times \hat{r}_{i,j}}{r_{i,j}^2}
\end{align}
```

#### 2. 专业表格设计
- 使用`minipage` + `raisebox`在表格单元格中嵌入图片
- 多行合并与精确垂直偏移控制
- 精细间距调整：`\\[-3mm]`、`\arraystretch{1.1}`
- 使用`threeparttable`的表格脚注

```latex
\begin{minipage}[b]{0.35\columnwidth}
  \centering
  \raisebox{-.5\height}{\includegraphics[width=1.0\linewidth]{fig/figTableIVa.eps}}
\end{minipage}
```

#### 3. 精密图片管理
- 2x2、2x3和不对称子图布局
- 双格式策略：EPS源文件自动转换为PDF
- 使用`\vspace{}`和`\hspace{}`精确间距控制
- 跨栏图片`figure*`环境

#### 4. IEEE期刊规范
- 完整的`IEEEtran`文档类实现
- 规范的作者格式与IEEE会员标注
- 版权声明和资助致谢
- 带照片的作者简介

---

## 项目结构

```
finalPackage/
├── Latex/
│   ├── arrayTX-TPEL.tex      # 主LaTeX源文件（900+行）
│   ├── arrayTX-TPEL bk.tex   # 备份版本
│   ├── arrayTX-TPEL.pdf      # 编译输出
│   ├── fig/                   # 57个EPS图片 + PDF转换版
│   │   ├── fig1.eps          # 系统概览
│   │   ├── fig2.eps          # 电路配置
│   │   ├── fig3a-d.eps       # B场计算
│   │   └── ...
│   ├── Bibliography/
│   │   ├── myRef.bib         # 论文参考文献
│   │   ├── IEEEabrv.bib      # IEEE缩写
│   │   └── IEEEfull.bib      # IEEE全称
│   ├── NingKang.eps          # 作者照片
│   ├── YaoxiaShao.eps        # 作者照片
│   ├── MingLiu.eps           # 作者照片
│   └── ChengbinMa.eps        # 作者照片
├── figures/                   # 高分辨率源图片
├── author photos/             # 原始作者照片
├── .gitignore
├── README.md                  # 英文文档
├── README_CN.md               # 本文件
├── TECHNIQUES.md              # 详细技巧指南
└── LICENSE                    # CC BY-NC 4.0
```

---

## 如何编译

### 前置要求
- TeX Live 2020+ 或 MiKTeX
- 支持`epstopdf`的`pdflatex`

### 编译步骤

```bash
cd Latex/
pdflatex arrayTX-TPEL.tex
bibtex arrayTX-TPEL
pdflatex arrayTX-TPEL.tex
pdflatex arrayTX-TPEL.tex
```

或使用`latexmk`：
```bash
latexmk -pdf arrayTX-TPEL.tex
```

---

## 使用的关键宏包

| 类别 | 宏包 |
|------|------|
| **数学** | `amsmath`, `amssymb`, `empheq`, `steinmetz` |
| **表格** | `booktabs`, `multirow`, `makecell`, `threeparttable`, `array` |
| **图片** | `graphicx`, `subfigure`, `epstopdf`, `float` |
| **格式** | `siunitx`, `hyperref`, `soul`, `color`, `colortbl` |
| **布局** | `stfloats`, `balance`, `cuted`, `multicol` |
| **IEEE** | `IEEEtran`（文档类）|

---

## 引用

如果您使用了这个LaTeX模板或觉得它有帮助，请引用原始论文：

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

## 发展路线图

- [x] **v1.0.0-human**：人类基准版本（当前版本）
- [ ] **v2.0.0-ai**：AI增强版本（Claude/GPT优化）
- [ ] **对比报告**：人类 vs AI LaTeX的量化分析

### 实验目标

> 顶级AI能否改进顶级人类的LaTeX工程？

本仓库将作为**人类基准**。未来版本将探索：
- AI建议的代码优化
- 替代宏包选择
- 增强的数学公式格式
- 改进的图片布局

---

## 许可证

本项目采用**知识共享署名-非商业性使用 4.0 国际许可协议**（CC BY-NC 4.0）。

您可以自由地：
- **共享** — 在任何媒介以任何形式复制、发行本作品
- **演绎** — 修改、转换或以本作品为基础进行创作

惟须遵守下列条件：
- **署名** — 您必须给出适当的署名
- **非商业性使用** — 您不得将本作品用于商业目的

详见 [LICENSE](LICENSE)。

---

## 致谢

- **作者**：康宁、邵耀霞、刘明、马澄斌
- **单位**：上海交通大学
- **资助**：国家自然科学基金（资助号：52077132）

---

<p align="center">
  <strong>在AI时代之前，由人类精心打造。</strong><br>
  <em>2023年7月</em>
</p>
