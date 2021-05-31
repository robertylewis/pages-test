---
layout: archive
title: "Research"
permalink: /research/
author_profile: true
---

My research interests fall broadly into the category of formal methods, more specifically in interactive theorem proving and automated reasoning.
Disciplinary questions are difficult; I consider myself a logician,
a theoretical computer scientist, or an applied mathematician, depending on the day.
I publish primarily in computer science.

See [my CV]({{site.url}}/files/cv.pdf) for a list of my
publications, presentations, and drafts.

### Summary

*Proof assistants* are tools that provide languages for defining objects, stating properties of these objects, and proving that these properties hold; they also offer engines for verifying the correctness of these proofs.
*Automated reasoning* tools, including SAT solvers, SMT solvers, and first- and higher-order provers, are by contrast push-button tools that check the correctness of a statement. While they are sometimes used in the context of a proof assistant to close proof obligations automatically, they are seen more often in unverified settings.

My goal as a researcher is to adapt the logics, tools, and paradigms of formal methods in computer science to attack mathematical problems. I envision a future where trustworthy computer assistance in mathematical research is commonplace. The routine use of proof assistants will increase the reliability of proofs; large libraries of formal proofs will be used for reference and training by students and AI programs; advances in automated reasoning will do away with tedious parts of proving.

### Projects

Early in the course of my PhD studies, I became one of the first users of [Lean](http://leanprover.github.io), a proof assistant based on dependent type theory.
I am an active contributor to and maintainer of the Lean [standard library](https://leanprover-community.github.io/), an open-source community effort that serves as a base for much of my work.

I have recently worked on a [number](https://robertylewis.com/padics/) of [mathematical](https://lean-forward.github.io/e-g/) [formalizations](https://leanprover-community.github.io/papers/mathlib-paper.pdf) in Lean, as part of the [Lean Forward](https://lean-forward.github.io) project.

As part of my [dissertation]({{site.url}}/files/dissertation.pdf), I developed a method for automatically proving nonlinear inequalities. Extensions of this tool remain in active development. The system Draws on theory combination methods like SMT, to combine separate solvers for linear arithmetic, multiplicative arithmetic, and other theories in a heuristic proof search.

Another [project of mine]({{site.url}}/leanmm) integrates Lean with the computer algebra system (CAS) Mathematica. The link I have developed is generic, extensible, and can be used for communication in both directions.

To spread formal methods more widely, mathematicians and computer scientists must collaborate. Pushing this collaboration is an essential part of my research project.
I have organized [interdisciplinary](https://lean-forward.github.io/lean-together/2019/index.html)
[workshops](http://www.andrew.cmu.edu/user/avigad/meetings/fomm2020/index.html) working toward this goal.

I am very interested in the use of proof assistants in mathematics and computer science education. Jeremy Avigad, Floris
van Doorn, and I have developed a [mathematical reasoning
textbook](http://avigad.github.io/logic_and_proof/) that incorporates Lean.

My general interests
also include the philosophical and psychological aspects of mathematical reasoning. While my
published work is largely technical, I am curious about how developments in formal languages and
automated proof can shed light on traditional mathematical practice.



### Slides

Here is an assortment of slides from some talks I've given:

* [Formalizing the ring of Witt vectors](https://robertylewis.com/files/witt-short.pdf) ([video](https://www.youtube.com/watch?v=k-YncL7Cd4Q))
* [Simplifying casts and coercions](https://robertylewis.com/files/norm-cast.pdf)
* [The Lean mathematical library (video)](https://www.youtube.com/watch?v=fnRrwsaFUM8&ab_channel=ACMSIGPLAN)
* [Formalizing the solution to the cap set problem]({{site.url}}/files/capset_long_slides.pdf)
* [Formalized mathematics in Lean]({{site.url}}/files/lean_intro_slides.pdf)
* [A formal proof of Hensel's lemma over the p-adic integers]({{site.url}}/files/padics.pdf)
* [A heuristic method for formally verifying real inequalities]({{site.url}}/files/hales60.pdf)
* [Toward AI for Lean, via metaprogramming]({{site.url}}/files/lewis_aitp.pdf)
* [The Lean theorem prover, for mathematicians]({{site.url}}/files/western2.pdf)
* [An extensible ad-hoc interface between Lean and Mathematica]({{site.url}}/files/pxtp.pdf)
* [Automation and computation in the Lean theorem prover]({{site.url}}/files/aitp_slides.pdf)
* [Dependent types and the algebraic hierarchy]({{site.url}}/files/carma_slides.pdf)
* [Dissertation defense]({{site.url}}/files/defense.pdf)
* [MS thesis defense]({{site.url}}/files/ms_thesis.pdf)