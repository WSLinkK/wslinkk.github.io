---
title: Self-Consistent Vertex Corrections Beyond GW
linkTitle: Vertex Corrections
description: What the vertex changes, where it is inserted, and what self-consistent SOX, SOSEX, 2SOSEX, and G3W2 reveal.
weight: 3
math: true
katex: true
---

The vertex $\Gamma$ describes response processes that are absent when the $GW$ approximation replaces it by its lowest-order value. Adding a vertex is not a single, automatically improving correction: the result depends on the diagram, where the vertex is inserted, how its interaction lines are screened, and which quantities are updated self-consistently.

{{< raw >}}
<div class="note-summary">
  <div><span>Baseline</span><strong>Fully self-consistent GW</strong></div>
  <div><span>Vertex placement</span><strong>Self-energy only, ΓΣ</strong></div>
  <div><span>Studied family</span><strong>SOX → G3W2</strong></div>
</div>
{{< /raw >}}

## The vertex in Hedin's equations

Suppressing space, spin, and time labels, the exact self-energy and irreducible polarizability contain the same vertex,

$$
\Sigma=iGW\Gamma,
\qquad
P=-iGG\Gamma.
$$

Standard $GW$ takes $\Gamma\rightarrow1$, giving $\Sigma^{GW}=iGW$ and the bubble polarizability $P^{GW}=-iGG$. This neglects exchange and correlation processes carried by higher-order vertex diagrams.

Our paper studies a self-energy-only construction, denoted $GW\Gamma_\Sigma$:

$$
\widetilde\Sigma^{GW\Gamma_\Sigma}[G]
=\widetilde\Sigma^{GW}[G]
+\widetilde\Sigma^{\mathrm{vertex}}[G],
$$

while the polarization keeps the $GW$ bubble topology. This must be distinguished from a fully consistent solution of Hedin's equations in which a matching vertex also enters $P$. Self-energy and polarization vertices can partially cancel in one-particle excitation energies.

> **Important nuance.** There is no explicit vertex diagram in $P$, but screening is not frozen. The vertex-corrected $\Sigma$ changes $G$; the new $G$ rebuilds the bubble $P[G]$ and therefore $W[G]$ at every iteration.

## What “fully self-consistent” means here

The calculation is not $G_0W_0\Gamma$, eigenvalue-only $GW$, or quasiparticle self-consistent $GW$. Starting from an initial propagator, every iteration:

1. constructs $P=-iGG$ from the current interacting $G$;
2. solves the screening equation for $W$;
3. evaluates the $GW$ and selected vertex self-energies;
4. recomputes the static self-energy $\Sigma_\infty[G]$;
5. solves Dyson's equation and updates the chemical potential;
6. repeats until the coupled quantities converge.

The vertex is added to the dynamical self-energy $\widetilde\Sigma(i\omega_n)$. Nevertheless, both $\Sigma_\infty[G]$ and $\widetilde\Sigma[G]$ are recomputed from the updated propagator. “Dynamic-only vertex insertion” therefore describes the diagrammatic location of the correction, not a frozen static background.

## One exchange topology, several screenings

The common backbone is a second-order exchange contribution containing three Green's functions and two interaction kernels,

$$
\widetilde\Sigma^{\mathrm{SOX}(U_1,U_2)}
\sim -U_1U_2GGG.
$$

Write the screened interaction as

$$
W(i\Omega_m)=v+\widetilde W(i\Omega_m),
$$

where $v$ is the bare Coulomb interaction and $\widetilde W$ contains at least one polarization insertion. The approximations differ by choosing $U_1$ and $U_2$:

| Approximation | Interaction content | Physical reading |
|---|---|---|
| SOX | $(v,v)$ | Restores the bare second-order Pauli-exchange diagram missing from GW |
| SOSEX | $(v,W)$ | Screens one interaction line |
| 2SOSEX | $(v,W)$ plus the complementary ordering | Treats both placements of the singly screened line |
| G3W2 | $(W,W)$ | Uses two screened interactions and contains the full second order in $W$ |

The names encode diagram content, not an accuracy ladder. More screening reduces the magnitude of the exchange-like subtraction, while additional orderings can change both magnitude and sign.

## Static versus dynamic screening

For a screened line, the dynamic formulation retains its bosonic-frequency dependence,

$$
\widetilde W\rightarrow\widetilde W(i\Omega_m),
$$

whereas the static approximation uses the zero-frequency limit,

$$
\widetilde W(i\Omega_m)\rightarrow\widetilde W(0).
$$

This “static versus dynamic” label refers to the interaction inside the **vertex diagram**. It is separate from the decomposition of the total self-energy into $\Sigma_\infty$ and $\widetilde\Sigma(i\omega_n)$.

Dynamic SOSEX and 2SOSEX retain the time dependence of one screened line. Fully dynamic G3W2 requires two frequency convolutions; a direct quadrature evaluation scales as $O(N^5n_\Omega^2)$, so the molecular study restricts G3W2 to the static limit.

{{< raw >}}
<div class="note-concept-grid">
  <article><span>v,v</span><h3>SOX</h3><p>Largest unscreened exchange correction in the tested hierarchy.</p></article>
  <article><span>v,W</span><h3>SOSEX / 2SOSEX</h3><p>Partial screening and complementary interaction ordering.</p></article>
  <article><span>W,W</span><h3>G3W2</h3><p>Fully screened second-order exchange topology.</p></article>
</div>
{{< /raw >}}

## What the molecular benchmarks show

Across the tested molecules, the paper finds an ordered progression from the least to the most negative self-energy/energy behavior,

$$
\mathrm{SOX}>\mathrm{SOSEX}>G3W2>2\mathrm{SOSEX}>\mathrm{sc}GW.
$$

The trend supports an effective-screening interpretation: bare SOX produces the strongest exchange subtraction, while screening reduces it. Static and dynamic variants remain systematically distinct because $W(i\Omega_m)$ carries genuine frequency structure.

The vertex corrections act mainly as an approximately frequency-uniform renormalization of the self-energy rather than a wholesale reshaping of its spectrum. That explains why sizable energy shifts do not necessarily translate into qualitatively new spectral features.

For first ionization potentials:

- SOX and SOSEX generally worsen the average error relative to sc$GW$;
- G3W2 and 2SOSEX remain closer to sc$GW$;
- dynamic 2SOSEX gives a modest improvement for the $G_0W_0\Gamma29$ benchmark, but the improvement is not uniform across data sets or chemical families.

The tested variants reduce aggregate electron-addition errors, but many nominal anions in the benchmark are metastable. Those quantities are best interpreted as finite-basis model addition energies rather than general evidence of improved physical electron affinities.

## The main lesson

“Including a vertex” is not by itself a guarantee of greater accuracy. A self-energy-only vertex changes one channel of Hedin's coupled equations, and the result depends on how screened exchange is balanced against the unchanged polarization topology. The molecular benchmarks show systematic shifts and useful physical trends, but not a universal improvement over sc$GW$.

The productive role of the calculation is therefore diagnostic as well as predictive: full self-consistency removes the fixed-reference ambiguity, THC makes the diagram hierarchy tractable, and the comparison isolates what each vertex topology actually changes.

Continue with [Tensor hypercontraction](/docs/tensor/tensor_hypercontraction/) for the factorization that enables these contractions, or return to the [GW approximation](/docs/greens_function/gw/) for the vertex-free baseline.

## References

- M. Wang *et al.*, [Self-consistent vertex corrected GW with static and dynamic screening using tensor hypercontraction: Assessment of molecular charged excitations](https://doi.org/10.1063/5.0341797), *J. Chem. Phys.* **165**, 084107 (2026). [Open preprint](https://arxiv.org/abs/2604.25581).
- P. Pokhilko *et al.*, [Tensor hypercontraction for self-consistent vertex corrected GW with static and dynamic screening: Applications to molecules and solids with superexchange](https://doi.org/10.1063/5.0269572), *J. Chem. Phys.* **162**, 244110 (2025).
