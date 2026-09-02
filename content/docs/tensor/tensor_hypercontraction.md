---
title: Tensor Hypercontraction for Self-Consistent Green's Functions
linkTitle: Tensor Hypercontraction
description: How THC compresses Coulomb tensors and makes fully self-consistent GW and vertex-corrected calculations practical.
weight: 1
math: true
katex: true
---

Tensor hypercontraction (THC) is a structured factorization of the electron-repulsion integral tensor. Its purpose is not merely to store fewer numbers: it changes expensive four-index contractions into sequences of lower-rank operations over orbital and interpolation-point indices. In our work, that reduction is the enabling step for fully self-consistent $GW$ and self-energy vertex corrections.

{{< raw >}}
<div class="note-summary">
  <div><span>Dense object</span><strong>Four orbital indices</strong></div>
  <div><span>THC structure</span><strong>Collocation + kernel</strong></div>
  <div><span>Used for</span><strong>Dynamic self-energy</strong></div>
</div>
{{< /raw >}}

## From density fitting to hypercontraction

For atomic orbitals ${\phi_p\}$, the Coulomb integrals are

$$
(pq|rs)=\iint
\phi_p^{\ast}(\mathbf r_1)\phi_q(\mathbf r_1)
\frac{1}{|\mathbf r_1-\mathbf r_2|}
\phi_r^{\ast}(\mathbf r_2)\phi_s(\mathbf r_2)
\,d\mathbf r_1d\mathbf r_2.
$$

Density fitting (DF) first replaces the four-index tensor by products of three-index factors,

$$
(pq|rs)\approx\sum_{Q}V_{pq}(Q)V_{rs}(Q).
$$

THC factorizes the orbital-pair dependence one step further:

$$
(pq|rs)\approx
\sum_{\mu\nu}
X_p^{\mu}X_q^{\mu}
Z^{\mu\nu}
X_r^{\nu}X_s^{\nu}.
$$

Here $X_p^{\mu}=\phi_p(\mathbf r_\mu)$ is an orbital collocation matrix evaluated at selected real-space interpolation points, and $Z^{\mu\nu}$ is an effective interaction kernel on that grid. The essential approximation is that the orbital-product space can be represented accurately by values at a compact set of points.

> **Interpretation.** DF compresses the interaction into three-index objects. THC exposes a separable orbital structure inside those objects, allowing contractions to alternate between orbital space and interpolation-point space.

## What is—and is not—approximated

Separate the self-energy into frequency-independent and frequency-dependent parts,

$$
\Sigma(i\omega_n)=\Sigma_\infty+\widetilde\Sigma(i\omega_n).
$$

In our molecular charged-excitation study, DF is used for the static part $\Sigma_\infty$, while THC is applied to the dynamical post-Hartree–Fock contribution $\widetilde\Sigma(i\omega_n)$. This distinction matters: saying only that “the calculation uses THC” hides which physics is actually compressed.

The separation does **not** mean the static observables are isolated from THC error. At full self-consistency, the compressed dynamical self-energy changes $G$; the updated $G$ changes the density matrix; and both $\Sigma_\infty[G]$ and $\widetilde\Sigma[G]$ are rebuilt. A dynamical approximation can therefore feed back into a static energy contribution even though that static contraction is evaluated with DF.

{{< raw >}}
<div class="note-concept-grid">
  <article><span>Σ∞</span><h3>Static channel</h3><p>Evaluated with density-fitted integrals and recomputed from the interacting density.</p></article>
  <article><span>Σ̃</span><h3>Dynamic channel</h3><p>THC compresses the frequency-dependent GW and SOX-type contractions.</p></article>
  <article><span>G</span><h3>Feedback</h3><p>Dyson iteration couples both channels through the updated propagator.</p></article>
</div>
{{< /raw >}}

## Storage and contraction structure

Let $N=n_{\mathrm{AO}}$, $n_Q$ be the number of DF auxiliary functions, and $n_\mu$ the number of THC interpolation points.

| Representation | Main stored interaction structure |
|---|---|
| Dense ERIs | $O(N^4)$ |
| Density fitting | $O(n_QN^2)$ |
| THC / ISDF | $O(Nn_\mu+n_\mu^2)$ |

For the SOX-type vertex terms in our implementation, the leading THC contractions fall into two regimes,

$$
O(n_tn_\mu^2N^2n_k^2)
\qquad\text{and}\qquad
O(n_tn_\mu^2N^3n_k),
$$

where $n_t$ is the imaginary-time grid size and $n_k$ is the number of momentum points. Which regime dominates depends on system dimensions and contraction order. The practical gain comes from replacing the dense exchange bottleneck by matrix-like products over interpolation points.

## Choosing the THC rank

We parameterize the rank through the interpolation-point ratio

$$
\alpha_{\mathrm{Ipts}}=\frac{n_\mu}{N}.
$$

This makes the accuracy–cost tradeoff explicit: increasing $\alpha_{\mathrm{Ipts}}$ increases both the memory footprint and the work of every self-consistency iteration.

In the molecular benchmarks reported in our paper:

- a very small value, $\alpha_{\mathrm{Ipts}}=5$, can under-resolve the frequency dependence of the self-energy for a sensitive case such as SiO;
- at moderate rank, the frequency-dependent shape stabilizes and the residual error is closer to a nearly uniform amplitude offset;
- by $\alpha_{\mathrm{Ipts}}=10$, the plotted self-energy curves are visually indistinguishable from tighter results, and representative total energies differ from the $\alpha_{\mathrm{Ipts}}=15$ reference by well below $10^{-6}$ a.u.

These are protocol-specific convergence observations, not a universal rank prescription. Basis, system, observable, and whether THC is applied to static or dynamical terms all matter.

## Why THC enables vertex corrections

A second-order exchange topology contains three Green's functions and two interaction lines. Replacing either interaction by a screened, frequency-dependent $W$ adds time or frequency structure on top of an already expensive exchange contraction. Without factorization, evaluating these diagrams at every Dyson iteration quickly becomes prohibitive.

THC makes the calculation feasible by preserving the separable pair structure through the contraction. The benchmark result is therefore twofold: the factorization lowers cost, and its error can be converged below the scale relevant to the self-consistent $GW$ and $GW\Gamma_\Sigma$ charged excitations studied.

## Practical validation checklist

1. Converge the same observable that will be reported—not only the ERI residual.
2. Inspect the shape of $\widetilde\Sigma(i\omega_n)$, since an energy can look converged before all frequency structure is stable.
3. Separate errors in $\Sigma_\infty$ and $\widetilde\Sigma$ by recording which factorization is used in each channel.
4. Compare against a same-method, tighter-THC reference before comparing different many-body approximations.
5. Recheck convergence after changing basis, system size, or vertex topology.

Continue with [Self-consistent vertex corrections](/docs/greens_function/vertex_corrections/) to see which diagrams the factorization makes accessible, or revisit [Two-electron Coulomb integrals](/docs/notes/integral/) for the uncompressed interaction.

## References

- M. Wang *et al.*, [Self-consistent vertex corrected GW with static and dynamic screening using tensor hypercontraction: Assessment of molecular charged excitations](https://doi.org/10.1063/5.0341797), *J. Chem. Phys.* **165**, 084107 (2026). [Open preprint](https://arxiv.org/abs/2604.25581).
- P. Pokhilko *et al.*, [Tensor hypercontraction for self-consistent vertex corrected GW with static and dynamic screening: Applications to molecules and solids with superexchange](https://doi.org/10.1063/5.0269572), *J. Chem. Phys.* **162**, 244110 (2025).
