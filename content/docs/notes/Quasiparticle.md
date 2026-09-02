---
title: Quasiparticles
linkTitle: Quasiparticles
description: How interacting excitations emerge as poles and broadened peaks of the one-particle Green's function.
weight: 2
math: true
katex: true
---

A quasiparticle is a long-lived excitation of an interacting system that behaves approximately like a particle with renormalized properties. It is not a bare electron: the surrounding medium responds, and that dressing changes the excitation energy, spectral weight, velocity, and lifetime.

{{< raw >}}
<div class="note-summary">
  <div><span>Energy shift</span><strong>Re Σ</strong></div>
  <div><span>Lifetime</span><strong>−2 Im Σ</strong></div>
  <div><span>Coherent weight</span><strong>Z ≤ 1</strong></div>
</div>
{{< /raw >}}

## From Dyson's equation to a pole

For a single band, the retarded Green's function can be written as

$$
G^R(\mathbf k,\omega)=
\frac{1}{\omega+\mu-\epsilon_{\mathbf k}-\Sigma^R(\mathbf k,\omega)}.
$$

The non-interacting pole lies at $\epsilon_{\mathbf k}-\mu$. Interactions replace it with the solution of the quasiparticle equation

$$
E_{\mathbf k}+\mu-\epsilon_{\mathbf k}
-\operatorname{Re}\Sigma^R(\mathbf k,E_{\mathbf k})=0.
$$

Because the self-energy depends on frequency, this equation is nonlinear and may have more than one solution. A recognizable quasiparticle requires one solution to carry appreciable spectral weight and have a width small compared with its characteristic energy scale.

## Renormalization factor

Expand the real part of the self-energy near the quasiparticle energy. The coherent pole has residue

$$
Z_{\mathbf k}=\left[
1-\left.\frac{\partial\operatorname{Re}\Sigma^R(\mathbf k,\omega)}{\partial\omega}
\right|_{\omega=E_{\mathbf k}}
\right]^{-1}.
$$

$Z_{\mathbf k}$ measures the overlap between the bare-particle state and the dressed excitation. Interactions transfer the missing weight $1-Z_{\mathbf k}$ into incoherent backgrounds and satellite features. In a matrix problem, the derivative is evaluated in the relevant quasiparticle state rather than treated as a scalar.

## Spectral function and lifetime

The quantity measured by charged-excitation spectroscopies is related to the spectral function

$$
A(\mathbf k,\omega)=-\frac{1}{\pi}\operatorname{Im}G^R(\mathbf k,\omega).
$$

Near a well-isolated pole, the coherent contribution is approximately Lorentzian:

$$
A_{\mathrm{qp}}(\mathbf k,\omega)\approx
\frac{Z_{\mathbf k}}{\pi}
\frac{\Gamma_{\mathbf k}/2}
{(\omega-E_{\mathbf k})^2+(\Gamma_{\mathbf k}/2)^2},
$$

with linewidth

$$
\Gamma_{\mathbf k}\approx
-2Z_{\mathbf k}\operatorname{Im}\Sigma^R(\mathbf k,E_{\mathbf k}),
\qquad
\tau_{\mathbf k}\approx\frac{\hbar}{\Gamma_{\mathbf k}}.
$$

Thus the two parts of the self-energy have complementary roles: $\operatorname{Re}\Sigma$ shifts the excitation, while $\operatorname{Im}\Sigma$ gives decay and broadening.

## What a spectrum is telling you

| Feature | Interpretation |
|---|---|
| Sharp peak with large $Z$ | Long-lived, particle-like excitation |
| Broad peak | Short lifetime or strong scattering |
| Satellite peak | Coupling to another excitation, such as a plasmon |
| Strong incoherent continuum | Spectral weight not captured by a single quasiparticle |

Photoemission probes electron removal; inverse photoemission probes electron addition. Neither experiment measures a Kohn–Sham eigenvalue directly. In Green's-function methods, quasiparticle energies emerge from the interacting propagator and its self-energy.

## When the picture breaks down

The quasiparticle approximation is controlled only when $\Gamma_{\mathbf k}$ is small and the self-energy varies smoothly near the pole. It becomes unreliable when peaks strongly overlap, $Z$ becomes very small, satellites compete with the main peak, or the Green's function has no isolated pole. Strongly correlated metals, systems near quantum criticality, and fractionalized phases can require a description centered on the full spectral function rather than individual quasiparticles.

## Connection to GW

The GW approximation constructs $\Sigma\approx iGW$ from a propagator and a dynamically screened interaction. Its most common use is to correct charged-excitation energies, but the same frequency-dependent self-energy also contains spectral weights, lifetimes, and satellites. A one-shot $G_0W_0$ calculation evaluates these corrections from a fixed reference; self-consistent GW updates the propagator and screening together.

## Further reading

- L. Hedin, [New Method for Calculating the One-Particle Green's Function with Application to the Electron-Gas Problem](https://doi.org/10.1103/PhysRev.139.A796).
- M. Wang *et al.*, [Self-consistent vertex-corrected GW with static and dynamic screening using tensor hypercontraction](https://doi.org/10.1063/5.0341797).
