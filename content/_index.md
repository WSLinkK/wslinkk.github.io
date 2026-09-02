---
title: Munkhorgil Wang
linkTitle: Munkhorgil Wang
layout: hextra-home
toc: false
---

{{< raw >}}
<section class="home-hero" aria-labelledby="intro-heading">
  <div class="home-hero__copy">
    <p class="eyebrow">Theoretical chemistry · Scientific computing</p>
    <h1 id="intro-heading">Making many-body physics <span>computable.</span></h1>
    <p class="home-hero__lede">I’m Munkhorgil Wang, a Ph.D. candidate at the University of Michigan. I develop Green’s-function methods and scientific software to understand the electronic structure of molecules and solids.</p>
    <div class="home-actions" aria-label="Primary links">
      <a class="button button--primary" href="/about/#research">Explore my research <span aria-hidden="true">→</span></a>
      <a class="button button--secondary" href="/docs/">Read my notes</a>
    </div>
    <div class="home-meta" aria-label="Affiliations">
      <span>Ann Arbor, Michigan</span>
      <span>Zgid Research Group</span>
      <span>Ph.D. candidate</span>
    </div>
  </div>

  <div class="research-orbit" aria-hidden="true">
    <div class="research-orbit__glow"></div>
    <svg class="research-orbit__field" viewBox="0 0 420 420">
      <defs>
        <radialGradient id="nucleus-shell" cx="35%" cy="28%" r="75%">
          <stop offset="0%" stop-color="#ffffff" />
          <stop offset="42%" stop-color="#dce8ff" />
          <stop offset="100%" stop-color="#91aff0" />
        </radialGradient>
        <linearGradient id="wave-positive" x1="0" x2="1">
          <stop offset="0%" stop-color="#70a0ff" stop-opacity="0.08" />
          <stop offset="100%" stop-color="#2463eb" stop-opacity="0.34" />
        </linearGradient>
        <linearGradient id="wave-negative" x1="1" x2="0">
          <stop offset="0%" stop-color="#8067ef" stop-opacity="0.08" />
          <stop offset="100%" stop-color="#8067ef" stop-opacity="0.29" />
        </linearGradient>
        <filter id="electron-glow" x="-200%" y="-200%" width="400%" height="400%">
          <feGaussianBlur stdDeviation="4" result="blur" />
          <feMerge><feMergeNode in="blur" /><feMergeNode in="SourceGraphic" /></feMerge>
        </filter>
      </defs>

      <g class="research-orbit__wavefunction research-orbit__wavefunction--primary">
        <path class="research-orbit__lobe research-orbit__lobe--negative" d="M207 210C174 151 101 145 63 210c38 65 111 59 144 0Z" />
        <path class="research-orbit__lobe research-orbit__lobe--positive" d="M213 210c33-59 106-65 144 0-38 65-111 59-144 0Z" />
        <path class="research-orbit__contour" d="M195 210c-27-37-77-35-105 0 28 35 78 37 105 0Zm30 0c27-37 77-35 105 0-28 35-78 37-105 0Z" />
      </g>
      <path class="research-orbit__wave-line" d="M54 211c26-40 52 40 78 0s52-40 78 0 52 40 78 0 52-40 78 0" />
      <path class="research-orbit__electron-path" d="M73 245C105 100 318 91 352 204c35 117-110 170-221 111C64 280 51 208 92 158" />
      <path class="research-orbit__path-arrow" d="M318 303l13 2-6 11" />

      <g class="research-orbit__electron-motion" filter="url(#electron-glow)">
        <path class="research-orbit__electron-trail" d="M-26 0H-8" />
        <circle class="research-orbit__electron" r="6" />
        <animateMotion dur="6.5s" repeatCount="indefinite" rotate="auto" path="M73 245C105 100 318 91 352 204c35 117-110 170-221 111C64 280 51 208 92 158" />
      </g>
      <g class="research-orbit__electron-static" transform="translate(318 303)">
        <circle class="research-orbit__electron" r="6" />
      </g>

      <g class="research-orbit__nucleus">
        <circle class="research-orbit__nucleus-halo" cx="210" cy="210" r="49" />
        <circle class="research-orbit__nucleus-shell" cx="210" cy="210" r="34" />
        <circle class="research-orbit__nucleon research-orbit__nucleon--proton" cx="198" cy="198" r="10" />
        <circle class="research-orbit__nucleon research-orbit__nucleon--neutron" cx="219" cy="197" r="10" />
        <circle class="research-orbit__nucleon research-orbit__nucleon--neutron" cx="197" cy="220" r="10" />
        <circle class="research-orbit__nucleon research-orbit__nucleon--proton" cx="219" cy="220" r="10" />
        <circle class="research-orbit__nucleus-highlight" cx="194" cy="190" r="4" />
      </g>
    </svg>
    <span class="research-orbit__label research-orbit__label--gg">GG</span>
    <span class="research-orbit__label research-orbit__label--gw">GW</span>
    <span class="research-orbit__label research-orbit__label--thc">THC</span>
    <span class="research-orbit__label research-orbit__label--sigma">Σ</span>
  </div>
</section>
<section class="home-section" aria-labelledby="focus-heading">
  <div class="section-heading">
    <p class="eyebrow">Research focus</p>
    <h2 id="focus-heading">From equations to reliable predictions</h2>
    <p>I work at the intersection of quantum chemistry, condensed-matter physics, and high-performance scientific computing.</p>
  </div>

  <div class="focus-grid">
    <article class="focus-card">
      <span class="focus-card__number">01</span>
      <h3>Many-body methods</h3>
      <p>Building self-consistent Green’s-function approaches for correlated electrons at finite temperature.</p>
    </article>
    <article class="focus-card">
      <span class="focus-card__number">02</span>
      <h3>Efficient representations</h3>
      <p>Using tensor hypercontraction and explicit atomic cores to make accurate calculations more practical.</p>
    </article>
    <article class="focus-card">
      <span class="focus-card__number">03</span>
      <h3>Scientific software</h3>
      <p>Contributing reproducible implementations for molecular and periodic electronic-structure calculations.</p>
    </article>
  </div>
</section>

<section class="home-section home-section--featured" aria-labelledby="work-heading">
  <div class="section-heading section-heading--split">
    <div>
      <p class="eyebrow">Selected work</p>
      <h2 id="work-heading">Recent research</h2>
    </div>
    <a class="text-link" href="/about/#research">Research overview <span aria-hidden="true">→</span></a>
  </div>

  <div class="work-list">
    <article class="work-item">
      <div class="work-item__meta">
        <span class="status-pill">2026 · J. Chem. Phys.</span>
        <span>Lead author</span>
      </div>
      <h3><a href="https://doi.org/10.1063/5.0341797">Self-consistent vertex-corrected GW with tensor hypercontraction</a></h3>
      <p>Assessing molecular charged excitations with static and dynamic screening while reducing dependence on the starting point.</p>
      <a class="text-link" href="https://doi.org/10.1063/5.0341797">View publication <span aria-hidden="true">↗</span></a>
    </article>

    <article class="work-item">
      <div class="work-item__meta">
        <span class="status-pill">2025 · Comput. Phys. Commun.</span>
        <span>Contributor</span>
      </div>
      <h3><a href="https://doi.org/10.1016/j.cpc.2024.109380">Green/WeakCoupling: finite-temperature many-body perturbation theory</a></h3>
      <p>An open implementation of fully self-consistent methods for molecules and periodic solids.</p>
      <a class="text-link" href="https://doi.org/10.1016/j.cpc.2024.109380">View publication <span aria-hidden="true">↗</span></a>
    </article>
  </div>
</section>

<section class="home-section notes-invite" aria-labelledby="notes-heading">
  <div>
    <p class="eyebrow">Open notebook</p>
    <h2 id="notes-heading">Ideas become clearer when they’re shared.</h2>
    <p>I write working notes on Green’s functions, solid-state physics, tensor methods, and the mathematical tools behind them.</p>
  </div>
  <a class="button button--primary" href="/docs/">Browse the notes <span aria-hidden="true">→</span></a>
</section>
{{< /raw >}}
