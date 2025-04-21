---
layout: post
title: Modular Design with Pipe and Filter
description: Quick introduction to the pipe-and-filter design pattern by referring to the Unix philosophy.
---

Often shaded by more recent and trendier [architectural patterns][1]{:target="_blank"} getting more attention, _Pipe and Filter_ can help us make our software systems more modular!

By emphasizing the use of simple and specific tools that _do one thing well_ and that can be _easily combined together_, it aligns closely with the [Unix philosophy][2]{:target="_blank"}.

## How it works

Simply put, data manipulations occur along a sequence called _pipeline_, which is made of independent tools called _filters_, that are connected together via _pipes_.

See _["Pipe and Filter Architecture"][3]{:target="_blank"}_ for a more detailed description.

## Main strength and benefits

As a matter of fact, Pipe and Filter is the ideal pattern for sequential data processing.

Clearly, it promotes modularity by making it easier to maintain and test each filter independently from the rest of the architecture.

And it makes reusability straightforward! Similar to Unix tools, filters can be combined together in different ways for a variety of processing tasks.

So let’s make use of the Pipe and Filter pattern, either for the entire system or just parts of it!

## Related posts

* [Unix Phylosophy with an Example][4]
* [Software Architecture Design for Busy Developers][5]
* [Testability = Modularity][6]

[1]: https://en.wikipedia.org/wiki/Architectural_pattern
[2]: https://en.wikipedia.org/wiki/Unix_philosophy
[3]: https://www.geeksforgeeks.org/pipe-and-filter-architecture-system-design/
[4]: {% link _posts/2019-03-02-unix-philosophy.md %}
[5]: {% link _posts/2019-09-05-software-architecture-design.md %}
[6]: {% link _posts/2020-01-15-testability-modularity.md %}
