---
title: GW Approximation
linkTitle: GW Approximation
weight: 2
math: true
katex: true
---
The fully self-consistent $GW$ approximation implements Hedin's [^Hedin] GW framework with full frequency dependence and self-consistency on the imaginary frequency axis. This ensures that the solution is thermodynamically consistent and conserving [^BaymKadanoff]. There are several variants of the $GW$ approximation, including:

- **One Shot GW ($G_0W_0$)**: Utilizes non-interacting Green's functions $ G_0 $ and does not iteratively update the self-energy. Typically starts from a mean-field solution like Density Functional Theory (DFT) and performs a single-shot GW calculation to obtain quasiparticle energies.

- **Quasiparticle GW ($qpGW$)**: Focuses on determining quasiparticle energies by fitting the self-energy to a linear form around the initial mean-field solution. 

- **Fully Self-Consistent GW (scGW)**: Implements a complete self-consistency loop by iteratively updating both the Green's function $ G $ and the screened interaction $ W $ until all quantities converge. This approach ensures that the Green's functions and self-energies are consistent with each other throughout the calculation, providing a robust and unbiased description of the electronic structure.

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




[^Hedin]: L. Hedin, [Phys. Rev. 139, A796 (1965)](https://doi.org/10.1103/PhysRev.139.A796)

[^BaymKadanoff]: Gordon Baym and Leo P. Kadanoff, [Phys. Rev. 124, 287 (1961)](https://journals.aps.org/pr/abstract/10.1103/PhysRev.124.287)

[^Bloch]: C. Yeh, S. Iskakov, D. Zgid, and E. Gull, [Phys. Rev. B 106, 235104](https://journals.aps.org/prb/abstract/10.1103/PhysRevB.106.235104)

[^rel]: C. Yeh, A. Shee, Q. Sun, E. Gull, and D. Zgid, [Phys. Rev. B 106, 085121](https://journals.aps.org/prb/abstract/10.1103/PhysRevB.106.085121)


