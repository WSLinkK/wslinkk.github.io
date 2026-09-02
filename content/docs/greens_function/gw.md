---
title: GW Approximation
linkTitle: GW Approximation
description: From Hedin's screened interaction to self-consistent GW equations, variants, observables, and limitations.
weight: 2
math: true
katex: true
---
The fully self-consistent $GW$ approximation implements Hedin's [^Hedin] framework with full frequency dependence and self-consistency on the imaginary-frequency axis. A fully self-consistent solution is thermodynamically consistent and conserving [^BaymKadanoff], while less expensive variants update only selected quantities.

{{< raw >}}
<div class="note-summary">
  <div><span>Self-energy</span><strong>Σ ≈ −GW</strong></div>
  <div><span>Screening</span><strong>W = U + UΠW</strong></div>
  <div><span>Polarization</span><strong>Π ≈ GG</strong></div>
</div>
{{< /raw >}}

## Common GW variants

- **One-shot GW ($G_0W_0$)** evaluates the self-energy once from a fixed mean-field propagator $G_0$ and fixed screening $W_0$. Its result therefore retains a starting-point dependence.

- **Eigenvalue-only GW with fixed screening ($evGW_0$)** updates quasiparticle energies in $G$ while keeping $W_0$ fixed. It is iterative, but it is not fully self-consistent because the screening and orbitals are not updated.

- **Eigenvalue-only GW ($evGW$)** updates energies entering both $G$ and $W$, usually while keeping the orbitals fixed. This can reduce starting-point dependence without solving the full Dyson problem.

- **Quasiparticle self-consistent GW ($qsGW$)** iteratively maps the dynamical self-energy to an effective static Hermitian potential. It updates energies and orbitals, but it remains conceptually distinct from fully dynamical Dyson self-consistency.

- **Fully self-consistent GW ($scGW$)** iterates the frequency-dependent $G$, rebuilds $W$, and solves Dyson's equation until all coupled quantities converge. No fixed $G_0$ or $W_0$ remains in the final solution.

In the $GW$ approximation [^Hedin], the correlated self-energy is approximated as the sum of an infinite series of Random Phase Approximation (RPA)-like "bubble" diagrams. Detailed implementation specifics for the Green code can be found in our implementation paper [^Bloch].

On the imaginary-time axis, the GW self-energy ${(\Sigma^{GW})}^{\mathbf{k}}(\tau)$ is expressed as:

{{< raw >}}
$$
{(\Sigma^{GW})}^{\mathbf{k}}_{i\sigma,j\sigma}(\tau) = -\frac{1}{N_{k}}\sum_{\mathbf{q}}\sum_{ab} G^{\mathbf{k-q}}_{a\sigma,b\sigma}(\tau)\tilde{W}^{\mathbf{k},\mathbf{k-q},\mathbf{k-q},\mathbf{k}}_{i a b j}(\tau)
$$
{{< /raw >}}

**Explanation of the Equation:**

- **${(\Sigma^{GW})}^{\mathbf{k}}_{i\sigma,j\sigma}(\tau)$**: The GW self-energy component for orbitals $i$ and $j$ with spin $\sigma$ at momentum $\mathbf{k}$ and imaginary time $\tau$.

- **$N_{k}$**: The total number of momentum points considered.

- **Summations**: The summations run over all momentum transfers $\mathbf{q}$ and orbital indices $a, b$.

- **$G^{\mathbf{k-q}}_{a\sigma,b\sigma}(\tau)$**: The Green's function for electrons with momentum $\mathbf{k-q}$ and spin $\sigma$, propagating from orbital $b$ to $a$ over time $\tau$.

- **$\tilde{W}^{\mathbf{k},\mathbf{k-q},\mathbf{k-q},\mathbf{k}}_{i a b j}(\tau)$**: The effective screened interaction tensor, which accounts for the screening effects beyond the bare Coulomb interaction.

This equation represents how the GW self-energy is constructed by coupling the Green's function with the screened interaction, effectively capturing the many-body interactions in the system.

**Screened Interaction in GW:**

In the GW approximation, the screened interaction $W$ in frequency space is given by [^Hedin]:

{{< raw >}}
$$
\begin{align*}
&W^{\mathbf{k}_{1}\mathbf{k}_{2}\mathbf{k}_{3}\mathbf{k}_{4}}_{i j k l}(i\Omega_{n}) = U^{\mathbf{k}_{1}\mathbf{k}_{2}\mathbf{k}_{3}\mathbf{k}_{4}}_{i j k l} \\
&\quad + \frac{1}{N_{k}}\sum_{\mathbf{k}_{5}\mathbf{k}_{6}\mathbf{k}_{7}\mathbf{k}_{8}}\sum_{abcd} U^{\mathbf{k}_{1}\mathbf{k}_{2}\mathbf{k}_{5}\mathbf{k}_{6}}_{i j a b} \mathit{\Pi}^{\mathbf{k}_{5}\mathbf{k}_{6}\mathbf{k}_{7}\mathbf{k}_{8}}_{a b c d}(i\Omega_{n}) W^{\mathbf{k}_{7}\mathbf{k}_{8}\mathbf{k}_{3}\mathbf{k}_{4}}_{c d k l}(i\Omega_{n})
\end{align*}
$$
{{< /raw >}}

**Explanation of the Equation:**

- **{{< raw >}}$W^{\mathbf{k}_{1}\mathbf{k}_{2}\mathbf{k}_{3}\mathbf{k}_{4}}_{i j k l}(i\Omega_{n})${{< /raw >}}**: The screened interaction tensor for orbitals $i, j, k, l$ and momenta {{< raw >}}$\mathbf{k}_{1}, \mathbf{k}_{2}, \mathbf{k}_{3}, \mathbf{k}_{4}${{< /raw >}} at Matsubara frequency $i\Omega_{n}$.

- **{{< raw >}}$U^{\mathbf{k}_{1}\mathbf{k}_{2}\mathbf{k}_{3}\mathbf{k}_{4}}_{i j k l}${{< /raw >}}**: The bare Coulomb interaction tensor.

- **{{< raw >}}$\mathit{\Pi}^{\mathbf{k}_{5}\mathbf{k}_{6}\mathbf{k}_{7}\mathbf{k}_{8}}_{a b c d}(i\Omega_{n})${{< /raw >}}**: The non-interacting polarization function, which describes how electron density responds to external perturbations.

- **Summations**: These account for all possible interactions and screening processes involving intermediate states indexed by {{< raw >}}$\mathbf{k}_{5}, \mathbf{k}_{6}, \mathbf{k}_{7}, \mathbf{k}_{8}${{< /raw >}} and orbitals $a, b, c, d$.

This equation iteratively defines the screened interaction $W$ by accounting for the polarization effects mediated by the non-interacting polarization function $\mathit{\Pi}$.

**Non-interacting Polarization Function:**

The non-interacting polarization function $\mathit{\Pi}$ is defined as:

{{< raw >}}
$$
\mathit{\Pi}^{\mathbf{k}_{1}\mathbf{k}_{2}\mathbf{k}_{3}\mathbf{k}_{4}}_{a b c d}(\tau) = \sum_{\sigma} G^{\mathbf{k}_{1}}_{d\sigma,a\sigma}(\tau) G^{\mathbf{k}_{2}}_{b\sigma,c\sigma}(-\tau) \delta_{\mathbf{k}_{1}\mathbf{k}_{4}} \delta_{\mathbf{k}_{2}\mathbf{k}_{3}}.
$$
{{< /raw >}}

**Explanation of the Equation:**

- **{{< raw >}}$\mathit{\Pi}^{\mathbf{k}_{1}\mathbf{k}_{2}\mathbf{k}_{3}\mathbf{k}_{4}}_{a b c d}(\tau)${{< /raw >}}**: The polarization function describing the response of the electron density to perturbations.

- **$G^{\mathbf{k}}_{ij}(\tau)$**: The Green's function representing the propagation of an electron from orbital $j$ to $i$ over imaginary time $\tau$.

- **{{< raw >}}$\delta_{\mathbf{k}_{1}\mathbf{k}_{4}} \delta_{\mathbf{k}_{2}\mathbf{k}_{3}}${{< /raw >}}**: Ensures momentum conservation within the polarization bubble.

This polarization function is crucial for determining how the bare Coulomb interaction is screened by the presence of other electrons in the system.

Green also provides an implementation of the GW approximation using the exact two-component formalism with the one-electron approximation (X2C-1e) for solving relativistic problems, such as those involving spin-orbit coupling [^rel].

## Computational loop

For a fully self-consistent calculation, the coupled objects are updated together:

1. Construct the polarization $\Pi[G]$ from the current propagator.
2. Solve the screening equation for $W$.
3. Contract $G$ and the correlation part of $W$ to obtain $\Sigma^{GW}$.
4. Add static Hartree and exchange terms consistently with the chosen convention.
5. Solve Dyson's equation for a new $G$ and adjust the chemical potential.
6. Mix and iterate until $G$, $\Sigma$, density, and thermodynamic targets converge.

On the imaginary axis this loop is numerically smooth, but charged-excitation spectra require analytic continuation or a real-axis treatment. Agreement of total energies does not by itself guarantee converged spectral features.

## What GW captures

The screened interaction resums an infinite sequence of polarization bubbles. This makes GW particularly effective for long-range screening and charged excitations in weakly to moderately correlated molecules and solids. The self-energy shifts quasiparticle energies, redistributes spectral weight, and introduces finite lifetimes.

The approximation omits the vertex $\Gamma$ by setting it to its lowest-order value. As a result, screening and self-energy corrections can become unbalanced. One-shot results depend on the starting mean-field reference; full self-consistency removes that dependence but can broaden spectra or alter error cancellation. Vertex-corrected approaches aim to treat these missing response and self-energy contributions more consistently.

## GW compared with GF2

| | GW | GF2 |
|---|---|---|
| Effective interaction | Dynamically screened $W$ | Bare Coulomb $U$ |
| Infinite resummation | Polarization bubbles | Generated only through Dyson iteration |
| Second-order exchange | Absent in standard GW | Included |
| Typical strength | Long-range screening and quasiparticle energies | Weak short-range correlation and total energies |

Continue with [Quasiparticles](/docs/notes/quasiparticle/) for the pole interpretation of $G$, or compare the equations directly with [GF2](/docs/greens_function/gf2/).




[^Hedin]: L. Hedin, [Phys. Rev. 139, A796 (1965)](https://doi.org/10.1103/PhysRev.139.A796)

[^BaymKadanoff]: Gordon Baym and Leo P. Kadanoff, [Phys. Rev. 124, 287 (1961)](https://journals.aps.org/pr/abstract/10.1103/PhysRev.124.287)

[^Bloch]: C. Yeh, S. Iskakov, D. Zgid, and E. Gull, [Phys. Rev. B 106, 235104](https://journals.aps.org/prb/abstract/10.1103/PhysRevB.106.235104)

[^rel]: C. Yeh, A. Shee, Q. Sun, E. Gull, and D. Zgid, [Phys. Rev. B 106, 085121](https://journals.aps.org/prb/abstract/10.1103/PhysRevB.106.085121)
