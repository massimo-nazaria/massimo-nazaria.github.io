---
layout: post
title: A Modularization Approach Against Technical Debt
description: This article describes an architectural design approach aimed at preventing the accumulation of technical debt.
---

## Introduction

Let's see an architectural design approach aimed at tackling technical debt.

### Why and How

The final goal is to mitigate the phenomenon of _[technical debt][4]{:target="_blank"}_ by effectively dealing with radical system modifications over the development life cycle.

Otherwise, the accumulation of technical debt can reduce modularity and make development tasks increasingly more difficult, time-consuming and error-prone.

Namely: we need to make it as easy as possible to restructure the architecture, and its codebase accordingly, in light of drastic design changes.

The presented modularization approach consists in enclosing crucial _[design decisions][5]{:target="_blank"}_ into distinct components in a modular architecture.

Particular emphasis during modularization is put on those decisions that are more likely to change over time.

### What is Modularity?

_Modularity_ refers to a _modular architecture_ and is measured by how much the corresponding codebase is easy to implement, modify and extend.

See _["Software Architecture Design for Busy Developers"][1]_.

### What is Modularization?

Modularization is the process of designing a modular architecture by decomposing a system into distinct highly cohesive components that are loosely coupled with one another.

#### About Modifiability

_Modifiability_ is a key aspect in a modular architecture, especially if the latter is designed so as to prevent technical debt as much as possible.

It's a quality attribute which tells us how an architecture can be easily modified with no undesirable effects.

Now, radical architectural modifications could very likely result in the accumulation of technical debt, if the architecture isn't highly modifiable.

#### About Internal Modifications

Good news is that a modular architecture is modifiable per se: any drastic component changes are allowed, as long as they stay _internal_.

In fact, an _internal modification_ doesn't alter the component _[interfaces][6]{:target="_blank"}_, thus it doesn't affect the rest of the architecture.

### What Technical Debt is Caused By

So a modular architecture is generally modifiable, _but_ drastic changes might affect several components by altering its interfaces.

Which makes such changes more difficult and time-consuming to be implemented as they require radical restructuring of the architecture and its codebase.

Whenever a proper fix to a problem requires a considerable time investment, that's where technical debt usually sets in.

Namely, in these cases, quick-and-dirty fixes are made because of the need of either shortening time-to-market or meeting strict deadlines by clients.

See _["Mind the Architecture-Code Gap"][2]_.

## Modularization Approach

Basically, the approach is aimed at maximizing the likelihood of potential changes to stay _internal_ to distinct components (i.e. no interfaces get altered).

**First step:** we prepare a list of [_architectural decisions_][5]{:target="_blank"} which are likely to change over time, then the decomposition can begin by analysing such a list.

**Next steps:** for each decision, we investigate a corresponding component to be designed in order to hide such a decision from the others.

**Note:** during modularization, we can refine the list of architectural decisions under analysis so as to make it easier to meet [fundamental modularity principles][1]{:target="_blank"}.

### Modularization Criterion: Modifiability

In particular, when considering each likely-to-change architectural decision, we ask ourselves:

* Will potential changes to such a decision be confined to one component, according to the modularization under analysis? Or, in other words:

* Will possible changes in such a decision require an _easy_ code refactoring that will affect just one component?

If we can answer _yes_ to one of the above, then probably the modularization at hand is viable!

Otherwise, it's probably the case that we revise the architectural decision to be made.

## Conclusion

Summing up, the presented modularization approach is aimed at dealing with technical debt in light of radical architectural modifications.

To this end, modularization is carried out on the basis of a list of architectural decisions.

Particular attention is paid to those crucial decisions that are likely to change over time.

Such decisions get hidden inside distinct components in order to maximize the likelihood that potentially needed modifications remain _internal_.

This way, each modification on a component doesn't affect the rest of the modular architecture.

This makes it easier to restructure the architecture and its codebase, and it also reduces potential undesirable effects.

As a consequence, it makes it easier to repay possible technical debts ASAP!

### Post Scriptum

Please be warned that technical debt is always _around the corner_: stay ready to tackle it!

## Further Reading

This post was highly inspired by [Parnas][3]{:target="_blank"}' 1973 paper _"On the Criteria To Be Used in Decomposing Systems into Modules"_.

[1]: {% link _posts/2019-09-05-software-architecture-design.md %}
[2]: {% link _posts/2019-03-13-technical-debt.md %}
[3]: https://en.wikipedia.org/wiki/David_Parnas
[4]: https://en.wikipedia.org/wiki/Technical_debt
[5]: https://en.wikipedia.org/wiki/Architectural_decision
[6]: {% link _posts/2019-09-05-software-architecture-design.md %}#component-boundaries-and-interfaces
