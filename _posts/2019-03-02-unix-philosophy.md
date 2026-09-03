---
layout: post
title: Unix Philosophy with an Example
description: This article introduces the Unix Philosophy by explaining the concepts of filter and pipeline with a playful example.
redirect_from:
  - /blog/2019/03/02/unix-philosophy-with-an-example.html
---

The [Unix philosophy][1]{:target="_blank"} is a set of software development concepts and norms which have shaped the way modern software is built.

Initiated in the late 60s and established over time by developers of [Unix-like operating systems][2]{:target="_blank"}, the Unix philosophy brought the concepts of [modularity][3]{:target="_blank"} and [reusability][4]{:target="_blank"} into software engineering best practices.

[Peter Salus][5]{:target="_blank"} summarized the Unix philosophy as follows:

* Write programs that do one thing and do it well.
* Write programs to work together.
* Write programs to handle text streams, because that is a universal interface.

Let's briefly introduce command-line *filters* and *pipelines* in order to see how these rules apply within the most popular operating systems.

## Introduction to Filters and Pipelines

A [filter][6]{:target="_blank"} is a program that gets input data from the _standard input_ and writes output data to the _standard output_. Filters are frequently used in text processing and are combined together in order to perform more complex text transformations with the use of [pipelines][7]{:target="_blank"}.

The latter, are basically sequences of filters separated by the pipe operator (i.e., the vertical bar `|`), which makes the output of  a filter become the input of the next filter in the sequence.

Let's have a look at a playful example.

## A Command-Line Example

### Roll a Die

The following one-liner simulates the rolling of a traditional die with 6 faces.

```sh
$ seq 1 6 | shuf | head -n 1
3
```

As the Unix philosophy suggests, it uses three programs that do one single thing (and do it well) by combining them together with pipes.

The table below describes what these programs do.

| Command     | Description                                           |
|-------------|-------------------------------------------------------|
| `seq 1 6`   | Prints integer numbers from 1 to 6.                   |
|-------------|-------------------------------------------------------|
| `shuf`      | Randomly permutes lines from an input text stream.    |
|-------------|-------------------------------------------------------|
| `head -n 1` | Extracts the 1st line from an input text stream.      |

Let's break the pipeline apart and see how it works.

First, the command `seq` produces all the possible outcomes from rolling a die.

```shell
$ seq 1 6
1
2
3
4
5
6
```

Second, the pipe operator `|` makes the output above become the input of the command `shuf`. As a result, the outcomes are randomly permuted.

```shell
$ seq 1 6 | shuf 
3
2
5
1
4
6
```

Finally, the command `head` extracts the 1st outcome from the sequence above. In this example, the result of our simulation is 3.

```shell
$ seq 1 6 | shuf | head -n 1
3
```

[1]: https://en.wikipedia.org/wiki/Unix_philosophy
[2]: https://en.wikipedia.org/wiki/Unix-like
[3]: https://en.wikipedia.org/wiki/Modular_programming
[4]: https://en.wikipedia.org/wiki/Reusability
[5]: https://en.wikipedia.org/wiki/Peter_H._Salus
[6]: https://en.wikipedia.org/wiki/Filter_(software)
[7]: https://en.wikipedia.org/wiki/Pipeline_(software)
