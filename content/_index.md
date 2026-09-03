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
        <radialGradient id="wave-density" cx="50%" cy="50%" r="50%">
          <stop offset="0%" stop-color="#2463eb" stop-opacity="0.22" />
          <stop offset="30%" stop-color="#6f8ff0" stop-opacity="0.15" />
          <stop offset="58%" stop-color="#8067ef" stop-opacity="0.09" />
          <stop offset="82%" stop-color="#2463eb" stop-opacity="0.035" />
          <stop offset="100%" stop-color="#2463eb" stop-opacity="0" />
        </radialGradient>
        <linearGradient id="electron-tail" x1="0" x2="1">
          <stop offset="0%" stop-color="#f1a83b" stop-opacity="0" />
          <stop offset="100%" stop-color="#f1a83b" stop-opacity="0.78" />
        </linearGradient>
        <filter id="electron-glow" x="-200%" y="-200%" width="400%" height="400%">
          <feGaussianBlur stdDeviation="4" result="blur" />
          <feMerge><feMergeNode in="blur" /><feMergeNode in="SourceGraphic" /></feMerge>
        </filter>
      </defs>

      <circle class="research-orbit__density" cx="210" cy="210" r="164" />
      <g class="research-orbit__density-waves">
        <circle cx="210" cy="210" r="72" />
        <circle cx="210" cy="210" r="108" />
        <circle cx="210" cy="210" r="144" />
      </g>

      <g class="research-orbit__callout-lines">
        <path d="M82 70L137 132" />
        <path d="M338 70L302 132" />
        <path d="M82 350L145 302" />
        <path d="M338 350L306 311" />
        <circle cx="137" cy="132" r="2.5" />
        <circle cx="302" cy="132" r="2.5" />
        <circle cx="145" cy="302" r="2.5" />
        <circle cx="306" cy="311" r="2.5" />
      </g>

      <g class="research-orbit__concept-motion research-orbit__concept-motion--wavefunction">
        <g class="research-orbit__concept-tag">
          <rect x="-60" y="-11" width="120" height="22" rx="11" />
          <circle cx="-48" cy="0" r="2.5" />
          <text x="7" y="2.6" text-anchor="middle">ORBITAL WAVEFUNCTION</text>
        </g>
        <animateMotion dur="24s" begin="-3s" repeatCount="indefinite" rotate="0" path="M80 210a130 130 0 1 0 260 0a130 130 0 1 0-260 0" />
      </g>
      <g class="research-orbit__concept-motion research-orbit__concept-motion--correlation">
        <g class="research-orbit__concept-tag">
          <rect x="-60" y="-11" width="120" height="22" rx="11" />
          <circle cx="-48" cy="0" r="2.5" />
          <text x="7" y="2.6" text-anchor="middle">ELECTRON CORRELATION</text>
        </g>
        <animateMotion dur="29s" begin="-17s" repeatCount="indefinite" rotate="0" path="M80 210a130 130 0 1 0 260 0a130 130 0 1 0-260 0" />
      </g>
      <g class="research-orbit__concept-static research-orbit__concept-static--wavefunction" transform="translate(210 80)">
        <g class="research-orbit__concept-tag">
          <rect x="-60" y="-11" width="120" height="22" rx="11" />
          <circle cx="-48" cy="0" r="2.5" />
          <text x="7" y="2.6" text-anchor="middle">ORBITAL WAVEFUNCTION</text>
        </g>
      </g>
      <g class="research-orbit__concept-static research-orbit__concept-static--correlation" transform="translate(210 340)">
        <g class="research-orbit__concept-tag">
          <rect x="-60" y="-11" width="120" height="22" rx="11" />
          <circle cx="-48" cy="0" r="2.5" />
          <text x="7" y="2.6" text-anchor="middle">ELECTRON CORRELATION</text>
        </g>
      </g>

      <g class="research-orbit__correlation">
        <path class="research-orbit__correlation-link" d="M118 282Q210 342 307 278" />
        <circle class="research-orbit__correlation-node" cx="118" cy="282" r="4" />
        <circle class="research-orbit__correlation-node" cx="307" cy="278" r="4" />
      </g>

      <g class="research-orbit__plane" transform="rotate(18 210 210)">
        <ellipse class="research-orbit__ring" cx="210" cy="210" rx="151" ry="69" />
        <g class="research-orbit__electron-motion" filter="url(#electron-glow)">
          <circle class="research-orbit__screening-shell research-orbit__screening-shell--outer" r="19" />
          <circle class="research-orbit__screening-shell" r="12" />
          <path class="research-orbit__electron-trail" d="M-27 0H-9" />
          <circle class="research-orbit__electron" r="6" />
          <animateMotion dur="7.5s" begin="-1.2s" repeatCount="indefinite" rotate="auto" path="M59 210a151 69 0 1 0 302 0a151 69 0 1 0-302 0" />
        </g>
        <circle class="research-orbit__electron research-orbit__electron-static" cx="361" cy="210" r="6" />
      </g>
      <g class="research-orbit__plane" transform="rotate(138 210 210)">
        <ellipse class="research-orbit__ring" cx="210" cy="210" rx="151" ry="69" />
        <g class="research-orbit__electron-motion research-orbit__electron-motion--secondary" filter="url(#electron-glow)">
          <path class="research-orbit__electron-trail" d="M-24 0H-9" />
          <circle class="research-orbit__electron" r="5.5" />
          <animateMotion dur="9.5s" begin="-4.1s" repeatCount="indefinite" rotate="auto" path="M59 210a151 69 0 1 0 302 0a151 69 0 1 0-302 0" />
        </g>
        <circle class="research-orbit__electron research-orbit__electron-static" cx="210" cy="141" r="5.5" />
      </g>
      <g class="research-orbit__plane" transform="rotate(258 210 210)">
        <ellipse class="research-orbit__ring" cx="210" cy="210" rx="151" ry="69" />
        <g class="research-orbit__electron-motion research-orbit__electron-motion--secondary" filter="url(#electron-glow)">
          <path class="research-orbit__electron-trail" d="M-24 0H-9" />
          <circle class="research-orbit__electron" r="5.5" />
          <animateMotion dur="11.5s" begin="-7.2s" repeatCount="indefinite" rotate="auto" path="M59 210a151 69 0 1 0 302 0a151 69 0 1 0-302 0" />
        </g>
        <circle class="research-orbit__electron research-orbit__electron-static" cx="59" cy="210" r="5.5" />
      </g>

      <g class="research-orbit__tensor-network" transform="translate(270 284) scale(1.15)">
        <path class="research-orbit__tensor-leg" d="M0 0L18 11M0 22L18 11M46 11L64 0M46 11L64 22" />
        <path class="research-orbit__tensor-bond" d="M22 11H28M36 11H42" />
        <circle class="research-orbit__tensor-orbital" cx="0" cy="0" r="3.5" />
        <circle class="research-orbit__tensor-orbital" cx="0" cy="22" r="3.5" />
        <circle class="research-orbit__tensor-orbital" cx="64" cy="0" r="3.5" />
        <circle class="research-orbit__tensor-orbital" cx="64" cy="22" r="3.5" />
        <rect class="research-orbit__tensor-factor" x="16" y="5" width="12" height="12" rx="3" />
        <rect class="research-orbit__tensor-core" x="28" y="4" width="8" height="14" rx="2" />
        <rect class="research-orbit__tensor-factor" x="36" y="5" width="12" height="12" rx="3" />
      </g>

      <g class="research-orbit__nucleus">
        <circle class="research-orbit__nucleus-halo" cx="210" cy="210" r="54" />
        <circle class="research-orbit__nucleus-shell" cx="210" cy="210" r="41" />
        <circle class="research-orbit__nucleon research-orbit__nucleon--proton" cx="195" cy="193" r="10" />
        <circle class="research-orbit__nucleon research-orbit__nucleon--neutron" cx="217" cy="191" r="10" />
        <circle class="research-orbit__nucleon research-orbit__nucleon--proton" cx="229" cy="210" r="10" />
        <circle class="research-orbit__nucleon research-orbit__nucleon--neutron" cx="218" cy="229" r="10" />
        <circle class="research-orbit__nucleon research-orbit__nucleon--proton" cx="196" cy="228" r="10" />
        <circle class="research-orbit__nucleon research-orbit__nucleon--neutron" cx="186" cy="209" r="10" />
        <circle class="research-orbit__nucleon research-orbit__nucleon--proton" cx="207" cy="210" r="10" />
        <circle class="research-orbit__nucleus-highlight" cx="190" cy="183" r="4" />
      </g>
    </svg>
    <span class="research-orbit__label research-orbit__label--green"><strong>G(ω)</strong><small>Green’s function</small></span>
    <span class="research-orbit__label research-orbit__label--gw"><strong>GW</strong><small>screening</small></span>
    <span class="research-orbit__label research-orbit__label--thc"><strong>THC</strong><small>tensor hypercontraction</small></span>
    <span class="research-orbit__label research-orbit__label--sigma"><strong>Σ(ω)</strong><small>self-energy</small></span>
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
