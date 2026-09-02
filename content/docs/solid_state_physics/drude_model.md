---
title: The Drude Model
linkTitle: Drude Model
description: A derivation-led introduction to DC transport, optical conductivity, mobility, and the Hall response in the classical electron gas.
weight: 1
math: true
katex: true
---

The Drude model treats conduction electrons as a classical gas that accelerates between instantaneous, momentum-randomizing collisions. Its assumptions are crude, yet one relaxation time $\tau$ produces a remarkably useful first description of metallic transport.

{{< raw >}}
<div class="note-summary">
  <div><span>Central idea</span><strong>Acceleration + relaxation</strong></div>
  <div><span>Key scale</span><strong>Scattering time τ</strong></div>
  <div><span>Main result</span><strong>σ₀ = ne²τ/m</strong></div>
</div>
{{< /raw >}}

## Equation of motion

For carriers of charge $-e$, effective mass $m$, and average velocity $\mathbf v$, the relaxation-time approximation gives

$$
m\frac{d\mathbf v}{dt}=-e\left(\mathbf E+\mathbf v\times\mathbf B\right)-\frac{m\mathbf v}{\tau}.
$$

The last term is not a microscopic collision force. It is a statistical statement: in the absence of driving, the average momentum decays exponentially on the timescale $\tau$.

> **Interpretation.** The model separates coherent acceleration by external fields from incoherent momentum relaxation by the environment.

## DC conductivity

Set $\mathbf B=0$ and wait for the steady state, so $d\mathbf v/dt=0$. The drift velocity is

$$
\mathbf v_d=-\frac{e\tau}{m}\mathbf E.
$$

For an electron density $n$, the current density is $\mathbf j=-ne\mathbf v_d$. Therefore

$$
\mathbf j=\sigma_0\mathbf E,
\qquad
\sigma_0=\frac{ne^2\tau}{m},
\qquad
\rho_0=\frac{m}{ne^2\tau}.
$$

This result makes the roles of carrier density and scattering explicit. More carriers increase conductivity; more frequent momentum-relaxing collisions decrease it. The mobility $\mu_e$ and mean free path $\ell$ are

$$
\mu_e=\frac{e\tau}{m},
\qquad
\ell=v\tau,
$$

where the classical model estimates $v$ thermally. In real metals, transport is controlled by electrons near the Fermi surface, so the appropriate scale is usually $v_F$ rather than a Maxwell–Boltzmann thermal velocity.

## AC and optical response

For a harmonic electric field $\mathbf E(t)=\operatorname{Re}[\mathbf E_0e^{-i\omega t}]$, take $\mathbf v(t)=\operatorname{Re}[\mathbf v_0e^{-i\omega t}]$. The equation of motion becomes

$$
\left(\frac{1}{\tau}-i\omega\right)\mathbf v_0=-\frac{e}{m}\mathbf E_0,
$$

and the complex conductivity is

$$
\sigma(\omega)=\frac{ne^2\tau/m}{1-i\omega\tau}
=\frac{\sigma_0}{1-i\omega\tau}.
$$

Its real and imaginary parts are

$$
\operatorname{Re}\sigma(\omega)=\frac{\sigma_0}{1+(\omega\tau)^2},
\qquad
\operatorname{Im}\sigma(\omega)=\frac{\sigma_0\omega\tau}{1+(\omega\tau)^2}.
$$

The crossover at $\omega\tau\sim1$ distinguishes two regimes:

| Regime | Response |
|---|---|
| $\omega\tau\ll1$ | Collisions maintain an almost in-phase, resistive current. |
| $\omega\tau\gg1$ | Carriers cannot relax within one cycle; the response becomes mainly reactive. |

Using $\epsilon(\omega)=1+i\sigma(\omega)/(\epsilon_0\omega)$ gives the Drude dielectric function

$$
\epsilon(\omega)=1-\frac{\omega_p^2}{\omega(\omega+i/\tau)},
\qquad
\omega_p^2=\frac{ne^2}{\epsilon_0m}.
$$

The plasma frequency $\omega_p$ sets the natural collective scale of the electron gas and helps explain why many metals reflect visible or infrared light.

## Hall response

With $\mathbf B=B\hat{\mathbf z}$ and a steady current along $x$, the transverse Lorentz force is canceled by a Hall field. For a single electron-like carrier type,

$$
R_H=\frac{E_y}{j_xB}=-\frac{1}{ne}.
$$

The sign identifies the carrier type in this simple picture. Real multiband materials can have a Hall coefficient whose magnitude and sign cannot be interpreted through a single density $n$.

## What the model gets right—and misses

The Drude model captures Ohm's law, the scale of metallic conductivity, a relaxation-time optical response, and the existence of a Hall effect. It does not contain Fermi–Dirac statistics, band structure, Pauli blocking, or a microscopic theory of scattering. Consequently, its predictions for electronic heat capacity, thermal transport, and some Hall coefficients fail.

The Sommerfeld model keeps the same transport structure while replacing the classical gas with a degenerate Fermi gas. Band theory then replaces the bare mass by a dispersion-dependent velocity and effective mass. The Drude result survives—not as a complete theory, but as the low-frequency template beneath more realistic approaches.

## Reference

- Cornell ECE Open Courseware, [Drude model for metals: DC and high-frequency conductivity](https://ocw.ece.cornell.edu/courses/ece-4070-course-details/ece-4070-lectures-notes-handouts-2/).
