---
layout: post
title: Team Organization and Modular Decomposition
description: Brief explanation of how modular decomposition relates to team organization by referring to the Conway's law.
---

> Organizations which design systems (in the broad sense used here) are constrained to produce designs which are copies of the communication structures of these organizations.<br>
> -- Melvin E. Conway

Let's see how modularity and team organization relate to each other by taking inspiration from Conway's quotation, which is known as _[Conway's law][1]{:target="_blank"}_.

## Motivation for a modular architecture

Shorter development time is one among the many benefits which a well designed (i.e. modular) software architecture can bring to the development process.

Indeed, a modular architecture enables developers to safely work in parallel on distinct components with little need for communication.

But this can only hold true provided that the team organization is appropriate, let's see how.

## Need for proper team organization

In order to make the best use of a modular architecture the team organization should comply with the following:

* There is a **balanced workload distribution** across development teams; and
* Teams are responsible for **disjoint subsets of components** so they can work simultaneously with little need for communication.

## System decomposition and team organization

Briefly recap that _[designing a modular architecture][2]{:target="_blank"}_ requires decomposing a system into highly cohesive components that are loosely coupled with one another.

During _[system decomposition][3]{:target="_blank"}_ designers must seriously take the team organization into account in order to maximize the benefits of the architecture under design.

At the same time, they should evaluate all the possible adjustments on the team structure based on the potential design choices.

## Conclusion and further readings

Summing up, Conway's law tells us how modular system decomposition and team organization strongly relate to each other.

And that they should progress hand in hand over the development process so as to take full advantage of modularity!

See also _["Conway's Law"][4]{:target="_blank"}_ by Martin Fowler.

**Related posts**:

* [Modularization Against Technical Debt][5]
* [Modular Code in OOP][6]

[1]: https://en.wikipedia.org/wiki/Conway%27s_law
[2]: {% link _posts/2019-09-05-software-architecture-design.md %}
[3]: https://en.wikipedia.org/wiki/Decomposition_(computer_science)
[4]: https://martinfowler.com/bliki/ConwaysLaw.html
[5]: {% link _posts/2023-08-11-modularization.md %}
[6]: {% link _posts/2023-09-21-modular-oop.md %}
