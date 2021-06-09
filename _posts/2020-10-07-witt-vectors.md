---
title:  "Formalizing the Ring of Witt Vectors"
date:   2020-10-07 10:30:00 +100
categories: lean
comments: false
---

Johan Commelin and I have released a preprint of our new paper,
[Formalizing the Ring of Witt Vectors](http://robertylewis.com/files/witt-vectors.pdf)!
(Update, Nov 25: the paper has been accepted at [CPP '21](https://popl21.sigplan.org/home/CPP-2021#event-overview) and recognized as a Distinguished Paper.)
We describe the construction of the [p-typical Witt vectors](https://en.wikipedia.org/wiki/Witt_vector)
and their ring structure in Lean, and show that the ring of Witt vectors over the integers modulo p
is isomorphic to the ring of p-adic integers.

Witt vectors are a notoriously messy topic to cover informally.
The ring structure depends on a layer of definitions binding certain polynomials together.
Without caution, trying to prove things about this ring structure can lead to unfolding
horrible polynomial identities that are both intractable and unenlightening.

Johan and I developed a framework in Lean to vastly simplify these calculations.
The horror is minimized and neatly contained in one or two preliminary proofs;
after that, some simple Lean metaprograms are able to handle these calculations cleanly and uniformly.