---
title: Green's Functions
linkTitle: Green's Functions
description: A practical route from propagators and Dyson's equation to self-consistent GF2 and GW calculations.
weight: 1
next: "/docs/solid_state_physics"
math: true
---

Green's functions provide a compact language for asking how an added electron or hole propagates through an interacting system. Rather than describing a single wavefunction, the one-particle Green's function organizes excitation energies, spectral weights, lifetimes, densities, and thermodynamic information in one frequency-dependent object.

## The central objects

For a non-interacting reference with one-particle Hamiltonian $h_0$, the frequency-domain propagator is

$$
G_0(z)=\left[(z+\mu)S-h_0\right]^{-1},
$$

where $S$ is the overlap matrix and $\mu$ is the chemical potential. Interactions dress this propagator through Dyson's equation,

$$
G^{-1}(z)=G_0^{-1}(z)-\Sigma(z).
$$

The self-energy $\Sigma$ is the effective, energy-dependent potential that contains exchange and correlation. Choosing an approximation to $\Sigma$, then solving Dyson's equation consistently, defines a Green's-function method.

{{< raw >}}
<div class="note-concept-grid">
  <article><span>G</span><h3>Propagation</h3><p>Where and when a particle or hole excitation can travel.</p></article>
  <article><span>Σ</span><h3>Correlation</h3><p>How interactions shift, broaden, and redistribute spectral weight.</p></article>
  <article><span>A</span><h3>Observation</h3><p>The spectral function that connects theory to charged-excitation spectra.</p></article>
</div>
{{< /raw >}}

## Two approximations in this notebook

{{< raw >}}
<div class="collection-card-grid">
  <a class="collection-card" href="/docs/greens_function/gf2/"><span class="collection-card__tag">Second order</span><h3>GF2 approximation</h3><p>Direct and exchange diagrams through second order in the bare interaction.</p><span class="text-link">Read the note →</span></a>
  <a class="collection-card" href="/docs/greens_function/gw/"><span class="collection-card__tag">Screening</span><h3>GW approximation</h3><p>A dynamically screened interaction summed through the polarization.</p><span class="text-link">Read the note →</span></a>
</div>
{{< /raw >}}

## A self-consistent calculation

1. Build a reference Green's function $G_0$ and choose $\mu$.
2. Evaluate the self-energy $\Sigma[G]$ for the selected approximation.
3. Solve Dyson's equation to obtain an updated $G$.
4. Update the density and chemical potential, then repeat until all target quantities converge.
5. Continue $G$ or $\Sigma$ from the imaginary axis when real-frequency spectra are required.

The same loop can behave very differently under GF2 and GW because their diagrammatic content, screening, and failure modes differ. The notes below focus on those distinctions.
