---
layout: post
title: Mind the Architecture-Code Gap
description: This article introduces the concepts of software architecture, software erosion and technical debt.
redirect_from:
  - /blog/2019/03/13/mind-the-architecture-code-gap.html
---

[Software architecture][1]{:target="_blank"} defines systems to be developed in the form of rigorous diagrams which depict how the source code is going to be structured.

Due to the inevitable demand for additional functionalities by clients, architectural models must account for [modular code][2]{:target="_blank"} which is easy to reuse, modify, and extend.

Regardless of the fact that software architecture is crucial to this end, oftentimes the source code becomes increasingly misaligned with the corresponding architecture.

Structural quality defined by architectural models fades away behind tons of unstructured lines of code which are difficult to maintain and improve. See [_big ball of mud_][3]{:target="_blank"} and [_software erosion_][4]{:target="_blank"}.

Such undesirable phenomenon is due to [time-to-market][5]{:target="_blank"} pressures which disregard software quality in favour of merely what's visible to the end user.

## Be Careful of the Gap

The gap between architecture and code is related to the notion of [technical debt][6]{:target="_blank"}, which refers to the implied cost of future rework needed to make up for quick-and-dirty code changes.

Summing up, software erosion is mainly due to the accumulation of architectural violations by developers, which are frequently encouraged by business pressures.

This fact is not going to let go of the need to quickly place products into the market. So let's work towards keeping the gap in check!

## What to read next

* [Avoid Spaghetti Code with Scope Minimization][7]
* [Software Architecture Design Fundamentals for Busy Developers][8]
* [Testability = Modularity][9]

[1]: https://en.wikipedia.org/wiki/Software_architecture
[2]: https://en.wikipedia.org/wiki/Modular_programming
[3]: https://en.wikipedia.org/wiki/Big_ball_of_mud
[4]: https://en.wikipedia.org/wiki/Software_architecture#Software_architecture_erosion
[5]: https://en.wikipedia.org/wiki/Time_to_market
[6]: https://en.wikipedia.org/wiki/Technical_debt
[7]: {% link _posts/2022-02-10-spaghetti-code.md %}
[8]: {% link _posts/2019-09-05-software-architecture-design.md %}
[9]: {% link _posts/2020-01-15-testability-modularity.md %}
