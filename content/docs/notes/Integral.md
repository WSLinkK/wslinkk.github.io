---
title: Two Electron Coulomb Integral
linkTitle: eri
weight: 4
math: true
katex: true
---

Electron-electron repulsion integrals are fundamental quantities in quantum chemistry that describe the Coulombic interactions between pairs of electrons occupying different molecular orbitals. These integrals are essential for accurately determining the electron correlation and overall energy of a molecular system.

$$
\begin{align*}
   U_{pqrs} &= \int \psi^*_p(\mathbf{r}_1, \sigma_1) \psi_q(\mathbf{r}_1, \sigma_1) \frac{1}{\vert\mathbf{r}_1-\mathbf{r}_2\vert}\psi^*_r(\mathbf{r}_2, \sigma_2) \psi_s(\mathbf{r}_2, \sigma_2) d\mathbf{r}_1 d\mathbf{r}_2 d\sigma_1 d\sigma_2\\
   &= \left( pq \vert rs \right) \text{ in chemists' notation}\\
   &= \int \phi^*_p(\mathbf{r}_1, \sigma_1) \phi^*_r(\mathbf{r}_2, \sigma_2) \frac{1}{\vert\mathbf{r}_1-\mathbf{r}_2\vert} \phi_q(\mathbf{r}_1, \sigma_1) \phi_s(\mathbf{r}_2, \sigma_2) d\mathbf{r}_1 d\mathbf{r}_2 d\sigma_1 d\sigma_2\\
   &= \langle pr \vert qs \rangle \text{ in physicists' notation} \\
\end{align*}
$$

In chemists' notation, the integral $(pq\vert rs)$ represents the interaction between electrons in orbitals $p$ and $q$ with those in orbitals $r$ and $s$. Alternatively, physicists' notation expresses the same integral as $\langle pr \vert qs \rangle$, highlighting the symmetry and exchange interactions inherent in the system.

### Resolution of Identity/Density Fitting

Calculating these four-center integrals directly can be computationally demanding, especially for large systems. To mitigate this, techniques such as Resolution of Identity (RI) or Density Fitting are employed. These methods approximate the electron-electron repulsion integrals by decomposing them into a sum over auxiliary basis functions, as shown in equation (3). This approximation significantly reduces the computational cost while maintaining accuracy, facilitating the study of larger and more complex molecular systems.

$$
   U_{pqrs} = \sum_{Q} V_{pq}(Q) V_{rs}(Q)
$$
