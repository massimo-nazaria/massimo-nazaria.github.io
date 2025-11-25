---
layout: post
title: Make it Work First, Then Make it Work Fast
---

> “Premature optimization is the root of all evil.”<br>— Donald Knuth

Falling into the trap of improving code performance too early over the development process almost inevitably leads to [premature optimization][1]{:target="_blank"}, which is commonly regarded as something to stay away from. Let's recap why.

By making wrong assumptions on potential performance issues before the real bottlenecks are identified via [profiling][2]{:target="_blank"}, we might waste time [unnecessarily optimizing][3]{:target="_blank"} code parts that will seldom be used in production.

Not only does premature optimization waste time, it also produces overcomplicated code which is harder to understand and maintain: it makes coding and debugging activities much more difficult and error prone.

## Make it Work, Make it Right, Make it Fast

In the Unix world there's a long-established saying which reads _"Prototype before polishing. Get it working before you optimize it"_, which Kent Beck has famously reframed to _"Make it run, then make it right, then make it fast"_.

### The Approach in a Nutshell

1. First and foremost, <u>make it work</u>: focus on correctness by writing and testing clear and simple code that solves the problem at hand.
2. After that, <u>make it right</u>: refactor the working code for understandability and modularity by giving it proper structure, clear naming and commentary.
3. Last, <u>make it fast</u>: profile the code in order to find the actual bottlenecks and optimize only when it's truly necessary.

## Summing Up

Premature optimization originates from early wrong assumptions on potential bottlenecks. Not only does it waste time, it also makes code harder to maintain.

So let's avoid it! And when it arises the temptation of tweaking code, repeat the mantra: _"Make it Work First, then Make it Work Fast"_.

## Further Readings

* [Eric S. Reymond, _The Art of Unix Programming_ (Rule of Optimization)][4]{:target="_blank"}
* [Wiki Wiki Web, _Make it Work, Make it Right, Make it Fast_][5]{:target="_blank"}


[1]: https://wiki.c2.com/?PrematureOptimization
[2]: https://en.wikipedia.org/wiki/Profiling_(computer_programming)
[3]: https://en.wikipedia.org/wiki/Program_optimization#When_to_optimize
[4]: http://www.catb.org/~esr/writings/taoup/html/ch01s06.html#rule_of_optimization
[5]: https://wiki.c2.com/?MakeItWorkMakeItRightMakeItFast
