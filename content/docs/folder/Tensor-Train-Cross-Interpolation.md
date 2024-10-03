---
title: Tensor Train Cross Interpolation
date: 2024-03-18 21:56:55
tags:
categories: Tensor Train 
mathjax: true
---
## Matrix Cross Interpolation

Given an $M \times N$ matrix $A$, the *cross interpolation* technique (CI) yields an approximate rank $\chi$ factorization of $A$. It is distinct from the truncated singular value decomposition (SVD), in whcih one approximated $A$ by its SVD with all but the largest $\chi$ singluar values set to zero. Although the truncated SVD yields an optimal rank $\chi$ approximation of $A$ in the spectral norm, CI has the advantage that it may be constructed by querying only a small subset of the entries of $A$. CI is quasioptimal in the sense that its error is at most $O(\chi^2)$ times the optimal one.

We Begin by establishing our notation, Let $\mathcal{I}=\{i_1, i_2,\ldots ,i_{\chi}\}$ (respectively, $\mathcal{J}=\{j_1, j_2,\ldots ,j_{\chi}\}$) denote a list of rows (columns) of A, $\mathcal{I}_a\equiv i_a$ its $a\text{th}$ elements, and $\mathbb{I}={1, 2,\ldots, M}$ ($\mathbb{J}={1, 2,\ldots, N}$) the list of the indices of all rows (columns).

The matrix cross interpolation formula reas
$$
\begin{equation}
A=A(\mathbb{I},\mathbb{J})\approx A(\mathbb{I},\mathcal{J})A(\mathcal{I},\mathcal{J})^{-1}A(\mathcal{I},\mathbb{J})
\end{equation}
$$
