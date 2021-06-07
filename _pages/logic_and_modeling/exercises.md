---
layout: archive
title: Logic and Modeling 2020 -- Exercise session schedule
permalink: /logic_and_modeling/exercises
---

This list of exercises will be updated as the course progresses.

Exercises are from [Logic and Proof](http://avigad.github.io/logic_and_proof/), except where otherwise noted. 
You should attempt some of the problems before the exercise class, and come with questions. Not all problems will be covered in each class.

This text will also be updated as the course progresses. Exercises may be added or changed. Don't download it once at the beginning -- refresh it regularly!

 
Coronavirus update: exercise sessions will be held by the TAs over Zoom. We are working to figure out how to make these sessions as interactive as possible. The TAs will also post solutions to some exercises on Canvas, but we recommend attending the live sessions!



## Exercise Class 1: Wednesday, April 1

* Chapter 2: #1, 3
* Write parse trees for the following formulas:
  * (¬ (A ∧ B)) ↔ (¬ B ∨ A)
  * ¬ ((A ∧ B) ↔ (¬ (B ∨ A)))
* Chapter 3: #1-5, 12-14

## Exercise Class 2: Friday, April 3

* Chapter 3: #6, 8-10, 15-16
* Derive the formulas (𝐴∨⊥)↔𝐴 and ¬𝐴→(𝐴→𝐵)
* Prove A → B from hypothesis ¬B → ¬A (this requires the proof by contradiction rule)

## Exercise Class 3: Wednesday, April 8

* Lean problems posted on CoCalc

## Exercise Class 4: Wednesday, April 15

* Chapter 5: #1, 4-6, 9
* Chapter 6: 1-3, 5

## Exercise Class 5: Friday, April 17

* Chapter 7: #1, 2
* Chapter 8: #1, 2, 4, 5, 7, 11
* Extra translation problemsPreview the document 2.1.2-2.1.4

## Exercise Class 6: Wednesday, April 22

* Chapter 10: #1, 3, 4 (try #2 on your own)
* Lean problems posted on CoCalc

## Exercise Class 7: Friday, April 24

* Chapter 10: #2 (you can pick some subset of the sentences), 5-8
* Consider the set of sentences in 10.2, and find one more sentence that makes the set unsatisfiable.
* Find a sentence in the "dots" language of 10.2 that is valid.
* Show that the formulas ∀x(LL(x) → C(x)) and ∀x LL(x) → ∀x C(x) are not equivalent, by providing a model which makes one formula true and the other false. Can you provide a second model, that makes the first one false and the second true? (See: lecture 8 slides)
* Write a first-order sentence that is true in every model whose domain contains exactly three elements.
* Finish the Lean exercises from the previous session.

## Exercise Class 8: Wednesday, April 29

* Chapter 13: 1-3, 5-6
* Chapter 14: 2, 3
* Let φ be the sentence ∀x∀y∃z(R(x, y) → R(y, z)), where R is a binary relation symbol. Do the following models satisfy φ?
  * A = {a, b, c, d}, R^M = { (b, c), (b, b), (b, a) }
  * A = {a, b, c}, R^M = { (b, c), (a, b), (c, b) }
* Construct another model that satisfies φ, and another that doesn't.

## Exercise Class 9: Friday, May 1

* Extra translation problems
* Exam Dec 2004-6, Exercise Class 7 Extra 1
* For the translated sentences in Exercise Class 7 Extra 1 part 2 i, iii, v: construct a model where the sentence is true and a model where the sentence is false
* Discuss Lean questions
* Open-ended question, if there's time:

  I'm writing a piece of software to control a subway system that runs automatically, without human drivers. To be safe, I want to logically specify some behavior of the system.
  What are some useful specifications you could write down? State the symbols in the language, the domain of quantification, and which sentences should hold.
  For example: in a language with a relation symbol same_postition(x, y), quantifying over trains, you might want forall x, forall y, not (x = y) -> not same_position(x, y).
  Can you find natural ways to formalize "a train always moves forward"? "A train can't go above a certain speed"? "When a train reaches the end of the line, its speed is 0"?
  It will be useful to think about arithmetic and order structures here. For instance, times can be added, and position (along a track) is a total order. We might write forall x, forall t, position_at_time(x, t+1) > position_at_time(x, t). What is the intended domain of quantification here?
  Note: this is actually done in real life. The software that controls line 14 of the Paris metro, which runs automatically, has had safety-critical properties checked with formal proofs. http://deploy-eprints.ecs.soton.ac.uk/8/1/fm_sc_rs_v2.pdf (Links to an external site.)

## Exercise Class 10: Wednesday, May 6

* Exercises and exam questions at the end of lecture slides
* Huth and Ryan 5.2 #1, 3, 4, 5a-g, 6a-b

## Exercise Class 11: Friday, May 8

From Huth and Ryan:

* 5.2: 5d-e
* 5.3: 7 (only the properties symmetry and functionality )
* 5.3: 13 (only the 4th and the 6th formula of the table)
* 5.3: 14, 16, 17
* Open ended question if there's time:
  One reason we're interested in modal logic is because it can be used to model program execution.
  You can think of a computer program as transitioning between states. A computer starts with a memory bank, with values assigned to different locations. It processes these (and perhaps changes values), and then transitions to a new state.
  Sometimes there can be more than one option for where to transition: i.e. the computer could behave differently if a certain variable is true or false.

  This "state transition" picture sounds a lot like a Kripke model. Propositional letters represent values stored in memory. (Maybe p means "bit number 20 is true.") A world is a single state. An arrow from one world to another represents that it's possible the program transitions from one to another.

  Think about the modal logic vocabulary we're using in this context. Under this interpretation, what does it mean that a sentence is true at a world? True in a model? What is a frame, and what does it mean for a sentence to be valid in a frame? 

  You even know enough to express some specific properties of programs. Can you write down a sentence in modal logic that says "this program never terminates"? Any other interesting sentences you can think of?

 

## Exercise Class 12: Wednesday, May 13

* 2.5.1 a, f. (Try d, e, g on your own)
* Extra 1: In the lecture we proved the consistency theorem [which says that the notions `consistent' and `syntactically consistent' coincide] from the soundness and completeness theorem [which says: ⊢ = ⊨). Now prove conversely the soundness and completeness theorem(s) from the consistency theorem.
* Extra 2: Show that from a set of formulas that is not semantically consistent (inconsistent) everything can be derived. Thus:
  {φ 1, ..., φ n} inconsistent <=> for all ψ it holds: φ 1, ..., φ n  |- ψ
* Extra 3: We work with a binary predicat symbol R, and constants c and c' (as in Theorem 2.26 in the book).
  * Give a formula that expresses that c' can be reached from c via an R-path consisting of 4 steps.
  * Give a formula that expresses that c' can be reached from c via an R-path consisting of less than 4 steps.
  * Give a set Γ of formulas that expresses that c' cannot be reached from c via a (finite) R-path.
  * Show that Γ cannot consist of only finitely many formulas.
  * Does there exist a formula that expresses that c' can be reached from c via an R-path of more than 4 steps?
* More practice (on your own): 2.4 #12 a-c, g-k
 

## Exercise Class 13: Friday, May 15

* Extra 1: Carefully state the definition of a decision problem. Is provability in propositional logic decidable? Why or why not?
* Extra 2: For each of the following formulas, find a Kripke model M in which the formula is valid, and one in which it is not.
  * ⋄p ∧ ¬◾p
  * p ∧ ⋄p
  * (⋄p ∨ ⋄q) → p
* 2.5 #2
* Exam review questions
* Extra 3 (hard!): We talked about decidability for predicate logic in the slides, and propositional logic in Extra 1.
  What about modal logic?
  Consider the decision problem with input a Kripke frame F and formula of modal logic ϕ, that asks whether ϕ is valid in F. Is this problem decidable?
  There's an even more general notion of validity in modal logic: a formula ϕ is valid if it's valid in every frame. Do you think this is decidable?
 

## Exercise Class 14: Wednesday, May 20

Come with questions to review for the exam!