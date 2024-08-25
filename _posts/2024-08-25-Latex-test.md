---
layout: post
title: "Latex Test"
date: 2024-08-25
categories: latex
tags: [test]
---
\documentclass{article}
\usepackage{amsmath} % 数学公式支持
\usepackage{amsfonts} % 数学符号
\usepackage{amssymb} % 数学符号
\usepackage{graphicx} % 插入图片
\usepackage{hyperref} % 链接
\usepackage{multirow} % 表格多行

\begin{document}

\title{复杂的 LaTeX 示例}
\author{ChatGPT}
\date{\today}
\maketitle

\section{引言}

在这篇文章中，我们将展示一些复杂的 LaTeX 示例，包括数学公式、方程组、矩阵、表格和插图。

\section{数学公式}

\subsection{分数和根号}

考虑以下分数和根号表达式：
\[
\frac{a^2 + b^2}{\sqrt{c^2 + d^2}}
\]

\subsection{极限与积分}

极限与积分的表达式：
\[
\lim_{x \to \infty} \frac{1}{x} = 0
\]
\[
\int_{0}^{1} x^2 \, dx = \frac{1}{3}
\]

\subsection{方程组}

线性方程组的解：
\[
\begin{cases}
2x + 3y = 7 \\
4x - y = 1
\end{cases}
\]

\subsection{矩阵}

矩阵示例：
\[
\mathbf{A} = \begin{pmatrix}
1 & 2 & 3 \\
4 & 5 & 6 \\
7 & 8 & 9
\end{pmatrix}
\]

\subsection{多项式}

一个多项式的展开：
\[
(x + y)^3 = x^3 + 3x^2y + 3xy^2 + y^3
\]

\section{表格}

\begin{table}[h!]
\centering
\begin{tabular}{|c|c|c|}
\hline
\textbf{列1} & \textbf{列2} & \textbf{列3} \\
\hline
\multirow{2}{*}{A} & B1 & C1 \\
                   & B2 & C2 \\
\hline
D1 & E1 & F1 \\
\hline
D2 & E2 & F2 \\
\hline
\end{tabular}
\caption{一个包含多行和多列的表格}
\label{tab:example}
\end{table}

\section{插图}

插入一个示例图片（假设图片文件为 `example.jpg`）：
\begin{figure}[h!]
\centering
\includegraphics[width=0.5\textwidth]{example.jpg}
\caption{这是一个示例图片}
\label{fig:example}
\end{figure}

\section{参考文献}

引用文献的示例：
\begin{thebibliography}{99}
\bibitem{example1} A. Author, \textit{Title of the Book}, Publisher, Year.
\end{thebibliography}

\end{document}
