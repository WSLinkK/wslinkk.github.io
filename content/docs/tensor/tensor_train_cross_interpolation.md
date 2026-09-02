---
title: Tensor-Train Cross Interpolation
linkTitle: TT Cross Interpolation
description: Building tensor-train approximations from adaptively selected entries rather than the full dense tensor.
weight: 2
math: true
katex: true
---

Tensor-train cross interpolation (TT-cross) builds a compressed representation of a high-dimensional tensor by evaluating only carefully selected entries. The method is useful when an individual element is inexpensive to compute but constructing the full tensor is impossible.

{{< raw >}}
<div class="note-summary">
  <div><span>Input access</span><strong>Selected entries</strong></div>
  <div><span>Representation</span><strong>Tensor train</strong></div>
  <div><span>Goal</span><strong>Avoid nᵈ storage</strong></div>
</div>
{{< /raw >}}

## Matrix cross interpolation

Begin with a matrix $A\in\mathbb C^{M\times N}$. Choose row indices $\mathcal I$ and column indices $\mathcal J$, each of size $r$. Define

$$
C=A(:,\mathcal J),\qquad
U=A(\mathcal I,\mathcal J),\qquad
R=A(\mathcal I,:).
$$

The cross or skeleton approximation is

$$
A\approx C\,U^{\dagger}R,
$$

where $U^{\dagger}$ is the inverse when the intersection matrix is square and nonsingular, or a pseudoinverse in the more general case. If $A$ has exact rank $r$ and the selected rows and columns span its row and column spaces, the reconstruction is exact.

This differs from a truncated singular-value decomposition in an important way. The SVD normally requires access to the full matrix; cross interpolation queries only selected rows and columns. The price is that accuracy depends strongly on the pivot set.

## Choosing informative pivots

A good intersection matrix $U$ should be well conditioned and geometrically representative. The maximum-volume principle seeks a submatrix with large $|\det U|$. Exact maximum-volume selection is combinatorial, so practical algorithms use greedy or alternating updates that find a sufficiently good submatrix.

> **Numerical warning.** Writing $U^{-1}$ is compact notation, but explicitly forming an inverse is rarely the stable implementation. Solve linear systems or use a rank-revealing factorization.

## Tensor-train representation

For a tensor $A(i_1,\ldots,i_d)$ with mode sizes $n_1,\ldots,n_d$, the TT form is

$$
A(i_1,\ldots,i_d)\approx
G_1(i_1)G_2(i_2)\cdots G_d(i_d),
$$

where

$$
G_k(i_k)\in\mathbb C^{r_{k-1}\times r_k},
\qquad r_0=r_d=1.
$$

The integers $r_k$ are TT ranks. Dense storage scales as $\prod_k n_k$; for a uniform mode size $n$ and rank $r$, TT storage is approximately $O(dnr^2)$.

Each bond $k$ corresponds to a matrix unfolding

$$
A^{\langle k\rangle}
\in\mathbb C^{(n_1\cdots n_k)\times(n_{k+1}\cdots n_d)}.
$$

The rank of this unfolding determines the exact TT rank across that bond. TT-cross applies the matrix-cross idea to these unfoldings without assembling them explicitly.

## How a TT-cross sweep works

1. **Initialize index sets.** Choose right multi-indices, often randomly or from a heuristic guess.
2. **Sweep left to right.** Evaluate fibers selected by the current left and right environments, reshape them into a local matrix, and update the core.
3. **Select new pivots.** Apply a max-volume or rank-revealing procedure to update the left index set.
4. **Sweep right to left.** Repeat symmetrically to refine right index sets.
5. **Adapt ranks.** Enrich or truncate the local representation until a residual or validation estimate reaches the target tolerance.
6. **Validate.** Compare the TT prediction with independently sampled tensor entries, not only the pivots used during construction.

Alternating sweeps couple local approximations into a global tensor train. For moderate ranks, the number of sampled entries and algebraic work grow roughly linearly with dimension $d$, although exact costs depend on mode sizes, ranks, and the pivot strategy.

## When it works well

TT-cross is attractive when:

- tensor entries can be evaluated independently on demand;
- relevant unfoldings have rapidly decaying singular values;
- the function is globally structured rather than dominated by isolated spikes;
- a dense tensor or global SVD would exceed memory limits.

It can struggle when ranks grow rapidly with dimension, pivot submatrices become ill-conditioned, the tensor is noisy, or important structure occupies a region the adaptive sampling never reaches.

## Practical diagnostics

| Diagnostic | What to watch |
|---|---|
| Held-out entry error | Direct evidence that interpolation generalizes beyond its pivots |
| TT-rank profile | Reveals which variable partitions carry the most correlation |
| Pivot conditioning | Warns about unstable local solves |
| Sweep-to-sweep change | Indicates convergence or stagnation |
| Physical constraints | Symmetry, conservation laws, and known limits should remain satisfied |

In many-body calculations, entry sampling can turn an otherwise impossible intermediate into an evaluable function. The essential question is then not only whether the tensor is low rank, but whether the chosen ordering and variables expose that structure.

## Reference

- I. Oseledets and E. Tyrtyshnikov, [TT-cross approximation for multidimensional arrays](https://doi.org/10.1016/j.laa.2009.07.024), *Linear Algebra and its Applications* **432**, 70–88 (2010).
