---
title: Research Notes
linkTitle: Notes
description: Working notes on Green's functions, solid-state physics, tensor methods, and the mathematical foundations of electronic-structure theory.
icon: book-open
layout: home
---

{{< raw >}}
<div class="notes-landing">
  <section class="notes-hero" aria-labelledby="notes-intro">
    <div>
      <p class="eyebrow">Open notebook · Theory into practice</p>
      <h1 id="notes-intro">A working library for many-body calculations.</h1>
      <p class="notes-hero__lede">These notes connect physical intuition, mathematical derivations, and implementation details. They are written to be revisited—not merely read once.</p>
      <div class="home-actions">
        <a class="button button--primary" href="/docs/greens_function/">Start with Green’s functions <span aria-hidden="true">→</span></a>
        <a class="button button--secondary" href="#learning-path">Follow the learning path</a>
      </div>
    </div>
    <dl class="notes-stats" aria-label="Notebook summary">
      <div><dt>4</dt><dd>connected subjects</dd></div>
      <div><dt>6</dt><dd>focused notes</dd></div>
      <div><dt>∞</dt><dd>room to refine</dd></div>
    </dl>
  </section>

  <section class="notes-section" aria-labelledby="topics-heading">
    <div class="section-heading">
      <p class="eyebrow">Browse by subject</p>
      <h2 id="topics-heading">Choose an entry point</h2>
      <p>Each collection begins with the essential picture, then moves toward equations and computational choices.</p>
    </div>
    <div class="notes-topic-grid">
      <a class="notes-topic-card notes-topic-card--blue" href="/docs/greens_function/">
        <span class="notes-topic-card__symbol">G</span>
        <div><span class="notes-topic-card__count">2 focused notes</span><h3>Green’s functions</h3><p>Dyson’s equation, self-energies, GF2, GW, and screened interactions.</p><span class="text-link">Explore the collection →</span></div>
      </a>
      <a class="notes-topic-card notes-topic-card--gold" href="/docs/solid_state_physics/">
        <span class="notes-topic-card__symbol">k</span>
        <div><span class="notes-topic-card__count">1 focused note</span><h3>Solid-state physics</h3><p>Build intuition for charge transport, crystals, and electronic behavior in solids.</p><span class="text-link">Explore the collection →</span></div>
      </a>
      <a class="notes-topic-card notes-topic-card--violet" href="/docs/tensor/">
        <span class="notes-topic-card__symbol">T</span>
        <div><span class="notes-topic-card__count">1 focused note</span><h3>Tensor methods</h3><p>Low-rank representations and cross interpolation for high-dimensional problems.</p><span class="text-link">Explore the collection →</span></div>
      </a>
      <a class="notes-topic-card notes-topic-card--green" href="/docs/notes/">
        <span class="notes-topic-card__symbol">∫</span>
        <div><span class="notes-topic-card__count">2 focused notes</span><h3>Foundations</h3><p>Coulomb integrals, quasiparticles, notation, and reusable physical concepts.</p><span class="text-link">Explore the collection →</span></div>
      </a>
    </div>
  </section>

  <section id="learning-path" class="notes-section" aria-labelledby="path-heading">
    <div class="section-heading">
      <p class="eyebrow">Suggested sequence</p>
      <h2 id="path-heading">One path through the notebook</h2>
      <p>Start with a classical model, add the language of excitations, then move into interacting and compressed representations.</p>
    </div>
    <ol class="learning-path">
      <li><span>01</span><div><p class="learning-path__type">Physical intuition</p><h3><a href="/docs/solid_state_physics/drude_model/">The Drude model</a></h3><p>From collisions to DC and optical conductivity.</p></div></li>
      <li><span>02</span><div><p class="learning-path__type">Many-body language</p><h3><a href="/docs/notes/quasiparticle/">Quasiparticles</a></h3><p>Poles, lifetimes, spectral weight, and the self-energy.</p></div></li>
      <li><span>03</span><div><p class="learning-path__type">Interaction</p><h3><a href="/docs/notes/integral/">Two-electron integrals</a></h3><p>The four-index object behind electronic correlation.</p></div></li>
      <li><span>04</span><div><p class="learning-path__type">Approximation</p><h3><a href="/docs/greens_function/gw/">GW and GF2</a></h3><p>Two conserving views of the electronic self-energy.</p></div></li>
      <li><span>05</span><div><p class="learning-path__type">Compression</p><h3><a href="/docs/tensor/tensor_train_cross_interpolation/">TT cross interpolation</a></h3><p>Query only the tensor entries that carry the structure.</p></div></li>
    </ol>
  </section>

  <section class="notes-section notes-principles" aria-labelledby="principles-heading">
    <div><p class="eyebrow">How to read these notes</p><h2 id="principles-heading">Intuition first. Derivation second. Implementation always in view.</h2></div>
    <div class="notes-principles__items">
      <div><span>01</span><p>Definitions establish a shared notation before calculations begin.</p></div>
      <div><span>02</span><p>Equations are followed by interpretation, limits, and computational meaning.</p></div>
      <div><span>03</span><p>Primary references make every page a launch point for deeper study.</p></div>
    </div>
  </section>
</div>
{{< /raw >}}
