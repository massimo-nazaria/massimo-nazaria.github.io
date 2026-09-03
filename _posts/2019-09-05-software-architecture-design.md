---
layout: post
title: Software Architecture Design for Busy Developers
description: This article introduces some fundamental principles about software architecture design, including modularity, low coupling, and high cohesion.
redirect_from:
  - /blog/2019/09/05/software-architecture-design-for-busy-developers.html
---

Let's talk about some of the fundamental software design principles, which are typically applied behind the scenes by designers.

[Software architecture][1]{:target="_blank"} represents the result of a sequence of design decisions which take place over time as long as software system complexity increases.

For the sake of clarity, let's define an architecture as a collection of [components][2]{:target="_blank"} combined together via connectors, which represent constraints on how components interact.

## Tackling Software Erosion

Tackling [software erosion][3]{:target="_blank"} is key. To this end, architecture choices are also aimed at preventing the accumulation of technical debt. See "[_Mind the Architecture-Code Gap_][4]{:target="_blank"}".

### Architecture Constraints

Technical debt results from architecture constraint violations, which create gaps between the planned architecture and the corresponding code implementation.

In order to mitigate this phenomenon, software architecture must clearly describe constraints on how components can exchange information.

### Component Boundaries, and Interfaces

Constraints are described by clear component boundaries, which indicate that internal data and functionalities of components are hidden to the rest of the architecture.

In addition to this, component interactions are forced to take place at restricted data exchange areas across component boundaries, namely [interfaces][5]{:target="_blank"}.

These interfaces indicate clear constraints on what data information are allowed in and out of the corresponding components.

### Example of Constraint Violation

Let's consider a layered architecture, where each component is constrained to only use information provided by the component immediately below it.

Any source code component that does not observe this constraint represents an architecture constraint violation, which must be corrected ASAP.

If such violations are not corrected, they can transform the architecture into a monolithic block which is difficult to maintain and extend.

As opposed to the concept of monolithic architecture, let's introduce modularity.

## Modularity

Often undervalued by developers, [modularity][6]{:target="_blank"} is fundamentally what architecture design choices should be supposed to be aiming at.

In a nutshell, a modular architecture is made of _loosely coupled_ and _high cohesive_ components, which are easy to [maintain][7]{:target="_blank"}, [extend][8]{:target="_blank"}, and [reuse][9]{:target="_blank"}.

Let’s start by introducing these concepts of coupling and cohesion in order to see what modularity means in its essence.

### Coupling and Cohesion

In a software architecture,

* [Coupling][10]{:target="_blank"} refers to multiple components, particularly to how the different components are dependent on one another, whereas
* [Cohesion][11]{:target="_blank"} refers to a single component, particularly to how internal functionalities of components are closely related to one another.

### Loosely Coupled and Highly Cohesive Components

A [loosely coupled][12]{:target="_blank"} architecture is one in which each of its components has, or makes use of, little or no knowledge of internal information about other components.

In other words, if there is minimal co-dependency between different components, then we say the architecture is loosely coupled.

On the other hand, a [highly cohesive][13]{:target="_blank"} component is made of a set of functionalities which are strictly related to one another.

Typically, a highly cohesive component follows the one-thing-done-well principle. See "[_Unix Philosophy with an Example_][14]{:target="_blank"}".

### About Maintainability, Extendibility, and Reusability

Let’s see how loose coupling and high cohesion increase software quality and reduce costs by improving maintainability, extensibility, and reusability.

Since loosely coupled components are poorly co-dependant, while functionalities of highly cohesive components are strictly correlated:

* It's easy to understand a given source code component, because there's no need to analyse other code outside of the component at hand.
* Modifications on a given source code component will seldom affect other code outside of the given component, which also makes the architecture more robust.
* Components can be easily set apart and reused in other architectures, because their functionalities are typically put together so as to solve a very specific sub-problem.

The latter also means components can be easily tested in isolation without the need of reproducing their architectural context.

### Loose Coupling and High Cohesion are Correlated

High cohesion relates to loose coupling and vice versa, thus an architecture made of highly cohesive components also exhibits loosely coupled components.

That said, we may question the utility of keeping in mind both loose coupling and high cohesion when designing an architecture.

In fact, due to this correlation, it should be sufficient to design architecture components by keeping in mind only one of such two characteristics.

We could just design a set of highly cohesive components, without taking loose coupling into account, and then put them together. The resulting architecture should be loosely coupled per se.

However, it's generally a good idea to take into account both loose coupling and high cohesion when making design choices, let's see why.

## Software Architecture Decomposition

Let's start by defining architecture [decomposition][15]{:target="_blank"} as an iterative design process which is aimed at decomposing large and complex systems into smaller and specialised components.

All in all, decomposition consists of [separating][16]{:target="_blank"} closely related system functionalities by encapsulating them into distinct, and loosely coupled, highly cohesive components.

Internal component functionalities and data remain totally isolated and hidden from other components. The only way components can interact with one another is via interfaces.

### Inseparability and Non-Extensibility of Functionalities in Highly Cohesive Components

So why should we keep in mind both loose coupling and high cohesion while decomposing a system, even though they seem to be equivalent? Isn't it enough to only take into account high cohesion?

First of all, when we split a set of functionalities into two or more distinct components, we need to check for potential component co-dependencies which this separation could imply.

Let's say that functionalities in highly cohesive components are both _inseparable_ and _non-extensible_, which are two principles that can be exploited when decomposing a system.

It follows an explanation on how both inseparability and non-extensibility can help designers to decompose a system into loosely coupled and highly cohesive components.

Suppose we are given two loosely coupled components _A_ and _B_ each one consisting of a set of respectively _n_ and _m_ highly cohesive functionalities _f_<sup>_A_</sup><sub>1</sub>, _f_<sup>_A_</sup><sub>2</sub>, ..., _f_<sup>_A_</sup><sub>_n_</sub>, and _f_<sup>_B_</sup><sub>1</sub>, _f_<sup>_B_</sup><sub>2</sub>, ..., _f_<sup>_B_</sup><sub>_m_</sub>.

Such functionalities in _A_ and _B_ are both inseparable and non-extensible, which means we can't remove functionalities from _A_ and put them into _B_ or vice versa, let's see why.

Suppose we arbitrary remove one functionality from _A_, say _f_<sup>_A_</sup><sub>_n_</sub>, and put it into _B_. The resulting two components _A_\* and _B_\* will consist of _n_-1 and _m_+1 functionalities, respectively.

In particular, we will have _A_\* made of _f_<sup>_A_</sup><sub>1</sub>, _f_<sup>_A_</sup><sub>2</sub>, ..., _f_<sup>_A_</sup><sub>_n_-1</sub>, and _B_\* made of _f_<sup>_B_</sup><sub>1</sub>, _f_<sup>_B_</sup><sub>2</sub>, ..., _f_<sup>_B_</sup><sub>_m_</sub>, _f_<sup>_A_</sup><sub>_n_</sub>. Let's see why _f_<sup>_A_</sup><sub>_n_</sub> is inseparable from _A_, and functionalities in _B_ cannot be extended by adding _f_<sup>_A_</sup><sub>_n_</sub>.

Due to the fact that the original components _A_ and _B_ were loosely coupled and they were both made of highly cohesive functionalities:

* _f_<sup>_A_</sup><sub>_n_</sub> **is inseparable** from _A_. In fact, functionalities _f_<sup>_A_</sup><sub>1</sub>, _f_<sup>_A_</sup><sub>2</sub>, ..., _f_<sup>_A_</sup><sub>_n_-1</sub> in _A_\* strictly depend on functionality _f_<sup>_A_</sup><sub>_n_</sub> in _B_\* and vice versa, which increases the co-dependency between _A_\* and _B_\*.
* Functionalities in _B_ **can't be extended** by adding _f_<sup>_A_</sup><sub>_n_</sub>. In fact, _f_<sup>_A_</sup><sub>_n_</sub> is not strongly related to the other functionalities _f_<sup>_B_</sup><sub>1</sub>, _f_<sup>_B_</sup><sub>2</sub>, ..., _f_<sup>_B_</sup><sub>_m_</sub> in _B_\* and vice versa, which reduces _B_\* cohesiveness.

In other words, such components _A_\* and _B_\* would immediately exhibit mutual dependencies and less cohesiveness compared to the original components _A_ and _B_.

This was an example on how to take into account both loose coupling and high cohesion when decomposing a system by making use of both inseparability and non-extensibility principles.

## Summing Up

* Software architecture is the result of a sequence of design decisions.
* Tackling software erosion is performed by preventing the accumulation of technical debt.
* Technical debt results from architecture constraint violations.
* Software architecture must clearly describe constraints on how components interact.
* Internal component information remain totally isolated and hidden.
* The only way components can exchange data is via interfaces.
* A modular architecture is made of loosely coupled and high cohesive components.
* Architecture decomposition is an iterative design process.
* Decomposition groups together closely related functionalities into distinct components.
* Taking into account both loose coupling and high cohesion can be done by making use of both inseparability and non-extensibility principles.

[1]: https://en.wikipedia.org/wiki/Software_architecture
[2]: https://en.wikipedia.org/wiki/Component-based_software_engineering#Definition_and_characteristics_of_components
[3]: https://en.wikipedia.org/wiki/Software_architecture#Software_architecture_erosion
[4]: {% link _posts/2019-03-13-technical-debt.md %}
[5]: https://en.wikipedia.org/wiki/Interface_(computing)
[6]: https://en.wikipedia.org/wiki/Modular_programming
[7]: https://en.wikipedia.org/wiki/Maintainability
[8]: https://en.wikipedia.org/wiki/Extensibility
[9]: https://en.wikipedia.org/wiki/Reusability
[10]: https://en.wikipedia.org/wiki/Coupling_(computer_programming)
[11]: https://en.wikipedia.org/wiki/Cohesion_(computer_science)
[12]: https://en.wikipedia.org/wiki/Loose_coupling
[13]: https://en.wikipedia.org/wiki/Cohesion_(computer_science)#High_cohesion
[14]: {% link _posts/2019-03-02-unix-philosophy.md %}
[15]: https://en.wikipedia.org/wiki/Decomposition_(computer_science)
[16]: https://en.wikipedia.org/wiki/Separation_of_concerns
