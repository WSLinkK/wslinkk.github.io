---
title: Tensor Methods
linkTitle: Tensor Methods
description: Low-rank representations that make high-dimensional electronic-structure calculations tractable.
weight: 3
prev: "/docs/solid_state_physics"
next: "/docs/notes"
math: true
---

A tensor is a multidimensional array, but in computational many-body theory the important question is not its order—it is whether the apparent high-dimensional complexity contains compressible structure. Low-rank decompositions replace a dense object with smaller factors that can be stored, contracted, and evaluated efficiently.

## Why compression matters

An order-$d$ tensor with mode size $n$ contains $n^d$ entries. This exponential growth is the curse of dimensionality. A tensor-train representation instead writes

$$
A(i_1,\ldots,i_d)\approx G_1(i_1)G_2(i_2)\cdots G_d(i_d),
$$

where each $G_k(i_k)$ is a small matrix and the connecting dimensions are the TT ranks. When those ranks remain moderate, storage changes from exponential in $d$ to approximately $O(dnr^2)$.

{{< raw >}}
<div class="note-concept-grid">
  <article><span>CP</span><h3>Canonical polyadic</h3><p>A sum of rank-one outer products with compact storage but delicate rank behavior.</p></article>
  <article><span>TT</span><h3>Tensor train</h3><p>A chain of three-index cores with stable algorithms and controllable bond dimensions.</p></article>
  <article><span>THC</span><h3>Hypercontraction</h3><p>Structured factorization tailored to electron-repulsion tensors and many-body contractions.</p></article>
</div>
{{< /raw >}}

## Entry-sampling methods

{{< raw >}}
<div class="collection-card-grid collection-card-grid--single">
  <a class="collection-card" href="/docs/tensor/tensor_train_cross_interpolation/"><span class="collection-card__tag">Adaptive compression</span><h3>Tensor-train cross interpolation</h3><p>Construct a low-rank approximation using selected tensor entries instead of materializing the full array.</p><span class="text-link">Read the note →</span></a>
</div>
{{< /raw >}}
