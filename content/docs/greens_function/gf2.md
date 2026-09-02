---
title: Second-Order Green's Function Approximation (GF2)
linkTitle: GF2 Approximation
description: Diagrammatic content, self-consistency, equations, and practical limits of finite-temperature GF2.
weight: 1
math: true
katex: true
---

Self-consistent second-order perturbation theory (GF2) is a conserving diagrammatic approximation that provides a nonzero contribution to the correlated self-energy. Also known as Second Order Born, GF2 was introduced to molecular systems in recent times by Holleboom and Snijders [^holleboom]. This method is generally accurate for systems with large energy gaps and weak interactions but is known to fail for metallic systems. Unlike the GW approximation, GF2 incorporates a second-order exchange term but does not account for higher-order screening effects.

{{< raw >}}
<div class="note-summary">
  <div><span>Expansion</span><strong>Second order in U</strong></div>
  <div><span>Interaction</span><strong>Bare Coulomb</strong></div>
  <div><span>Distinctive term</span><strong>Second-order exchange</strong></div>
</div>
{{< /raw >}}

## Diagrammatic content

GF2 evaluates the first-order Hartree–Fock contribution and the two second-order skeleton self-energy diagrams using the dressed Green's function. One is a direct or bubble-like contribution; the other is the second-order exchange diagram. Iterating these diagrams with Dyson's equation generates contributions beyond strict second order while retaining a conserving, $\Phi$-derivable structure.

The second-order contribution to the self-energy in imaginary time ($\tau$) and momentum space ($\mathbf{k}$) is given by [^rusakov] [^BandGapPaper]:

{{< raw >}}
$$
\begin{align*}
\Sigma^{(2)}_{ij}(\tau,\mathbf{k}) = - \frac{1}{N_{\mathbf{k}}^3}\sum\limits_{\substack{klmnpq\\ \mathbf{k_1}\mathbf{k_2}\mathbf{k_3} }} & 
\left(2U^{\mathbf{k_1}\mathbf{k}\mathbf{k_2}\mathbf{k_3}}_{qjln} - U^{\mathbf{k_2}\mathbf{k}\mathbf{k_1}\mathbf{k_3}}_{ljqn}\right)
\times U^{\mathbf{k}\mathbf{k_1}\mathbf{k_3}\mathbf{k_2}}_{ipmk}
\\ \times
& G^{\mathbf{k_1}}_{pq}(\tau) G^{\mathbf{k_2}}_{kl}(\tau) G^{\mathbf{k_3}}_{nm}(-\tau) \delta_{\mathbf{k}+\mathbf{k_3},\mathbf{k_1}+\mathbf{k_2}},
\end{align*}
$$
{{< /raw >}}

**Explanation of the Equation:**

- **$\Sigma^{(2)}_{ij}(\tau,\mathbf{k})$**: This represents the second-order self-energy component for orbitals $i$ and $j$ at imaginary time $\tau$ and momentum $\mathbf{k}$.

- **$N_{\mathbf{k}}$**: The number of discrete momentum points considered in the finite cluster.

- **Summations**: The summations run over all possible orbital indices ($k, l, m, n, p, q$) and momentum indices ($\mathbf{k_1}, \mathbf{k_2}, \mathbf{k_3}$).

- **{{< raw >}}$U^{\mathbf{k_1}\mathbf{k}\mathbf{k_2}\mathbf{k_3}}_{qjln}${{< /raw >}} and {{< raw >}}$U^{\mathbf{k_2}\mathbf{k}\mathbf{k_1}\mathbf{k_3}}_{ljqn}${{< /raw >}}**: These are components of the Coulomb interaction tensor, representing the electron-electron interactions between different orbitals and momenta.

- **$G^{\mathbf{k}}_{ij}(\tau)$**: The imaginary-time Green's function, describing the propagation of an electron from orbital $j$ to $i$ over time $\tau$.

- **$\delta_{\mathbf{k}+\mathbf{k_3},\mathbf{k_1}+\mathbf{k_2}}$**: The Kronecker delta ensures momentum conservation in the interaction process, meaning the total momentum before and after the interaction remains the same.

This equation effectively captures the second-order processes contributing to the self-energy, accounting for interactions between electrons mediated by the Coulomb tensor and the Green's functions.

## Self-consistency loop

1. Start from a reference $G$ and density matrix.
2. Build the Hartree–Fock and second-order correlation self-energies.
3. Transform between imaginary time and Matsubara frequency as required.
4. Solve Dyson's equation and update the chemical potential to preserve particle number.
5. Mix the new and old quantities, then repeat until energy, density, and self-energy converge.

Self-consistency removes dependence on a fixed reference propagator, but it does not make the diagrammatic approximation exact. Convergence behavior and the final spectrum should be checked separately.

## Strengths and limitations

| Strength | Limitation |
|---|---|
| Includes direct and exchange second-order diagrams | Does not resum long-range screening as GW does |
| Conserving when solved fully self-consistently | Can fail for metals and strongly correlated regimes |
| Gives energies, densities, and finite-temperature observables from one $G$ | Real-frequency spectra require analytic continuation |
| Polynomial formulation is compatible with integral factorizations | Four-index contractions remain costly without compression |

GF2 is most natural when the bare interaction is a useful expansion parameter and short-range correlation is important. Compare it with the [GW approximation](/docs/greens_function/gw/), where an infinite polarization series is absorbed into a screened interaction $W$.

[^holleboom]: L. J. Holleboom and J. G. Snijders, [A comparison between the Møller–Plesset and Green’s function perturbative approaches to the calculation of the correlation energy in the many-electron problem](https://doi.org/10.1063/1.459578)

[^rusakov]: A. A. Rusakov and D. Zgid, [Self-consistent second-order Green’s function perturbation theory for periodic systems](https://doi.org/10.1063/1.4940900)

[^BandGapPaper]: Sergei Iskakov, Alexander A. Rusakov, Dominika Zgid, and Emanuel Gull, [Effect of propagator renormalization on the band gap of insulating solids](https://journals.aps.org/prb/abstract/10.1103/PhysRevB.100.085112)
