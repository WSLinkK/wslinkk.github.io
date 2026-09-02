---
title: Two-Electron Coulomb Integrals
linkTitle: Coulomb Integrals
description: Notation, symmetry, basis transformations, and low-rank factorization of the electron-electron interaction.
weight: 1
math: true
katex: true
---

Two-electron repulsion integrals (ERIs) are the four-index representation of the Coulomb interaction in an orbital basis. They enter Hartree–Fock theory, correlated wavefunction methods, Green's-function self-energies, and screened interactions.

{{< raw >}}
<div class="note-summary">
  <div><span>Object</span><strong>Rank-4 tensor</strong></div>
  <div><span>Dense storage</span><strong>O(N⁴)</strong></div>
  <div><span>Common reduction</span><strong>Density fitting</strong></div>
</div>
{{< /raw >}}

## Definition and conventions

For spatial orbitals $\phi_p(\mathbf r)$, chemists' notation is

$$
(pq|rs)=
\iint
\phi_p^*(\mathbf r_1)\phi_q(\mathbf r_1)
\frac{1}{|\mathbf r_1-\mathbf r_2|}
\phi_r^*(\mathbf r_2)\phi_s(\mathbf r_2)
\,d\mathbf r_1d\mathbf r_2.
$$

Physicists often group bra and ket indices instead:

$$
\langle pr|qs\rangle=(pq|rs).
$$

The two expressions describe the same integral; only the index ordering changes. Stating the convention is essential because contractions that look identical can otherwise represent different direct and exchange terms.

For spin orbitals $\psi_p(x)=\psi_p(\mathbf r,\sigma)$, the spin integrations are included in $x$:

$$
\langle pr|qs\rangle=
\iint \psi_p^*(x_1)\psi_r^*(x_2)
\frac{1}{r_{12}}
\psi_q(x_1)\psi_s(x_2)\,dx_1dx_2.
$$

## Permutational symmetry

For real orbitals, the Coulomb kernel implies the eightfold symmetry

$$
(pq|rs)=(qp|rs)=(pq|sr)=(qp|sr)
=(rs|pq)=(sr|pq)=(rs|qp)=(sr|qp).
$$

With complex orbitals, exchanges within a pair introduce complex conjugation; for example,

$$
(pq|rs)^*=(qp|sr),
\qquad
(pq|rs)=(rs|pq).
$$

Implementations should exploit the symmetry appropriate to the chosen basis rather than assuming the real-orbital form universally.

## Why the tensor is expensive

With $N$ basis functions, a dense ERI tensor contains $O(N^4)$ elements. Transforming all four indices from an atomic-orbital basis to a molecular-orbital basis naively has even higher arithmetic cost. Many electronic-structure methods are therefore limited not by the formal equation alone, but by how this interaction is stored and contracted.

The Coulomb and exchange matrices illustrate two important contractions:

$$
J_{pq}=\sum_{rs}(pq|rs)D_{rs},
\qquad
K_{pq}=\sum_{rs}(pr|qs)D_{rs},
$$

where $D$ is a one-particle density matrix. The different index pairings are why notation discipline matters.

## Density fitting / resolution of the identity

Introduce an auxiliary basis $\{\chi_P\}$. Three-center integrals and the Coulomb metric are

$$
(pq|P),
\qquad
V_{PQ}=(P|Q).
$$

The four-center tensor is approximated as

$$
(pq|rs)\approx
\sum_{PQ}(pq|P)(V^{-1})_{PQ}(Q|rs).
$$

After a symmetric factorization of the metric, define

$$
B_{pq}^{Q}=\sum_P(pq|P)(V^{-1/2})_{PQ},
$$

so that

$$
(pq|rs)\approx\sum_Q B_{pq}^{Q}B_{rs}^{Q}.
$$

This replaces one four-index object with two three-index factors. Storage commonly drops from $O(N^4)$ to $O(N^2N_{\mathrm{aux}})$, and many contractions can be reorganized around matrix multiplication.

> **Implementation note.** As with cross interpolation, one normally solves or factorizes the Coulomb metric rather than forming $V^{-1}$ explicitly.

## Beyond density fitting

Cholesky decomposition generates similar three-index factors adaptively from the ERI matrix. Tensor hypercontraction factorizes the orbital-pair dependence further, often into products evaluated on interpolation points. Local and sparse representations exploit the spatial decay of orbital products. Each approach trades memory, arithmetic, accuracy control, and implementation complexity differently.

For Green's-function methods, these factorizations are especially valuable because the interaction appears repeatedly in self-energy, polarization, and screened-interaction contractions across time, frequency, momentum, and spin indices.
