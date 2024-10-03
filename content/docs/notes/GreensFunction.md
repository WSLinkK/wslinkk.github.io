---
title: Green's Function
linkTitle: Green's Function
weight: 2
math: true
katex: true
---
# Second-Order Approximation (GF2)

Self-consistent second-order perturbation theory is a conserving diagrammatic approximation that provides a nonzero contribution to the correlated self-energy. Also known as Second Order Born, the method was introduced to molecules in modern times by Holleboom and Snijders [^holleboom]. Generally, GF2 is considered accurate when gaps are large and interactions are weak but is known to fail for metals. Unlike the GW approximation, GF2 includes a second-order exchange term but does not incorporate higher-order screening contributions.

The second-order contribution to the self-energy in imaginary time and momentum space is[^rusakov][^BandGapPaper]:

$$
\begin{align*}
\Sigma^{(2)}_{ij}(\tau,\mathbf{k}) = - \frac{1}{N_{\mathbf{k}}^3}\sum\limits_{\substack{klmnpq\\ \mathbf{k_1}\mathbf{k_2}\mathbf{k_3} }} & 
(2U^{\mathbf{k_1}\mathbf{k}\mathbf{k_2}\mathbf{k_3}}_{qjln} - U^{\mathbf{k_2}\mathbf{k}\mathbf{k_1}\mathbf{k_3}}_{ljqn})
\times U^{\mathbf{k}\mathbf{k_1}\mathbf{k_3}\mathbf{k_2}}_{ipmk}
\\ \times
 &G^{\mathbf{k_1}}_{pq}(\tau)G^{\mathbf{k_2}}_{kl}(\tau)G^{\mathbf{k_3}}_{nm}(-\tau)\delta_{\mathbf{k}+\mathbf{k_3},\mathbf{k_1}+\mathbf{k_2}},
\end{align*}
$$


Here, $G^{\mathbf{k}}_{ij}(\tau)$ is the imaginary-time Green's function, $U^{\mathbf{k}\mathbf{k_1}\mathbf{k_2}\mathbf{k_3}}_{ijkl}$ is the Coulomb interaction tensor, and $\delta_{\mathbf{k}+\mathbf{k_3},\mathbf{k_1}+\mathbf{k_2}}$ ensures momentum conservation.

# GW Method

The fully self-consistent $GW$ approximation implements Hedin's [^Hedin] GW approximation with its full frequency dependence and self-consistency on the imaginary axis, ensuring the solution is thermodynamically consistent and conserving [^BaymKadanoff]. Note that there are several variants of the $GW$ approximation, including non-selfconsistent, partially self-consistent, quasiparticle approximated, and quasiparticle self-consistent versions, each corresponding to different equations and additional approximations.

In the $GW$ approximation [^Hedin], the correlated self-energy is approximated as the sum of an infinite series of RPA-like "bubble" diagrams. Implementation details of the code in Green are provided in our implementation paper [^Bloch].

On the imaginary-time axis, the GW self-energy ${(\Sigma^{GW})}^{\mathbf{k}}(\tau)$ is given by:


$$
{(\Sigma^{GW})}^{\mathbf{k}}_{i\sigma,j\sigma}(\tau) = -\frac{1}{N_{k}}\sum_{\mathbf{q}}\sum_{ab} G^{\mathbf{k-q}}_{a\sigma,b\sigma}(\tau)\tilde{W}^{\mathbf{k},\mathbf{k-q},\mathbf{k-q},\mathbf{k}}_{i a b j}(\tau)
$$


where $\tilde{W}$ is the effective screened interaction tensor, defined as the difference between the full dynamically screened interaction $W$ and the bare interaction $\boldsymbol{U}$, i.e., $\tilde{W} = W - U$.

Here and throughout, the indices $\{i,j,k,l,a,b\}$ represent orbital indices, $\{k,q\}$ denote crystal momenta, and $N_{k}$ is the number of momenta considered for a finite cluster.

In the $GW$ approximation, the screened interaction $W$ in frequency space is expressed as [^Hedin]:


$$
\begin{aligned}
&W^{\mathbf{k}_{1}\mathbf{k}_{2}\mathbf{k}_{3}\mathbf{k}_{4}}_{i j k l}(i\Omega_{n}) = U^{\mathbf{k}_{1}\mathbf{k}_{2}\mathbf{k}_{3}\mathbf{k}_{4}}}_{i j k l} \\
&\quad + \frac{1}{N_{k}}\sum_{\mathbf{k}_{5}\mathbf{k}_{6}\mathbf{k}_{7}\mathbf{k}_{8}}\sum_{abcd} U^{\mathbf{k}_{1}\mathbf{k}_{2}\mathbf{k}_{5}\mathbf{k}_{6}}}_{i j a b} \mathit{\Pi}^{\mathbf{k}_{5}\mathbf{k}_{6}\mathbf{k}_{7}\mathbf{k}_{8}}}_{a b c d}(i\Omega_{n}) W^{\mathbf{k}_{7}\mathbf{k}_{8}\mathbf{k}_{3}\mathbf{k}_{4}}}_{c d k l}(i\Omega_{n})
\end{aligned}
$$


where $\boldsymbol{\mathit{\Pi}}$ is the non-interacting polarization function:


$$
\mathit{\Pi}^{\mathbf{k}_{1}\mathbf{k}_{2}\mathbf{k}_{3}\mathbf{k}_{4}}_{a b c d}(\tau) = \sum_{\sigma} G^{\mathbf{k}_{1}}_{d\sigma,a\sigma}(\tau) G^{\mathbf{k}_{2}}_{b\sigma,c\sigma}(-\tau) \delta_{\mathbf{k}_{1}\mathbf{k}_{4}} \delta_{\mathbf{k}_{2}\mathbf{k}_{3}}.
$$


Green also provides an implementation of the GW approximation using the exact two-component formalism with the one-electron approximation (X2C-1e) for solving relativistic problems, such as those involving spin-orbit coupling [^rel].

[^Hedin]: L. Hedin, [Phys. Rev. 139, A796 (1965)](https://doi.org/10.1103/PhysRev.139.A796)

[^BaymKadanoff]: Gordon Baym and Leo P. Kadanoff, [Phys. Rev. 124, 287 (1961)](https://journals.aps.org/pr/abstract/10.1103/PhysRev.124.287)

[^Bloch]: C. Yeh, S. Iskakov, D. Zgid, and E. Gull, [Phys. Rev. B 106, 235104](https://journals.aps.org/prb/abstract/10.1103/PhysRevB.106.235104)

[^rel]: C. Yeh, A. Shee, Q. Sun, E. Gull, and D. Zgid, [Phys. Rev. B 106, 085121](https://journals.aps.org/prb/abstract/10.1103/PhysRevB.106.085121)

[^holleboom]: L. J. Holleboom and J. G. Snijders, [A comparison between the Møller–Plesset and Green’s function perturbative approaches to the calculation of the correlation energy in the many-electron problem](https://doi.org/10.1063/1.459578)

[^rusakov]: A. A. Rusakov and D. Zgid, [Self-consistent second-order Green’s function perturbation theory for periodic systems](https://doi.org/10.1063/1.4940900)

[^BandGapPaper]: Sergei Iskakov, Alexander A. Rusakov, Dominika Zgid, and Emanuel Gull, [Effect of propagator renormalization on the band gap of insulating solids](https://journals.aps.org/prb/abstract/10.1103/PhysRevB.100.085112)
