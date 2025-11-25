---
layout: post
title: Modular Code with Reusable Standalone Modules
---

Let’s explore how reusable standalone modules help us implement modular software in a practical and convenient way!

## Introduction

Reusable standalone modules are software components that can be either run as independent applications, or used as part of larger codebases in a straightforward way. Their independence and specialization make them operable across different contexts.

### Improved Modularity

Let's recap a system is modular when both _high cohesion_ and _loose coupling_ hold true, namely when each component focuses on a well-defined responsibility and when components exhibit minimal dependencies on one another.

Good news is: reusable standalone modules provide us with highly cohesive components which are loosely coupled by design! In fact, each component focuses on a very specific task and generally doesn't rely on external modules.

#### Understandability, Maintenance and Testing

Reusable standalone modules can be easily understood or tested in isolation, without the need to study the rest of the system. Furthermore, their modifications are less likely to impact other parts of the codebase.

## How-To: Reusable Standalone Modules

Before diving in, let's define a _reusable function_ as one that is focused on one specific task and has no side effects, i.e. doesn't modify global, local static, or input variables.

Basically, a reusable standalone module consists of two parts:

1. A set of <u>reusable functions</u>, which implement functionality provided by the module; and
2. An <u>execution entry point</u>, which consists in a special code block that runs when the module is executed directly from the command line as a standalone application.

This structure ensures the module can work either as a library or as an independent application.

### A Reusable Standalone Module in Python

As a toy example, let's see the following Python module named `math_utils.py`.

```py
# Reusable functions
def add(a, b):
    return a + b

def multiply(a, b):
    return a * b

# Execution entry point
if __name__ == "__main__":
    import argparse
    parser = argparse.ArgumentParser()
    parser.add_argument("operation", choices=["add", "multiply"])
    parser.add_argument("a", type=float)
    parser.add_argument("b", type=float)

    args = parser.parse_args()

    if args.operation == "add":
        result = add(args.a, args.b)
    elif args.operation == "multiply":
        result = multiply(args.a, args.b)

    print(result)
```

Clearly, it's a reusable standalone module: it defines two reusable functions which can be imported into different codebases, along with an execution entry point that runs when the module gets called as a standalone application.

The execution entry point is typically responsible of handling command-line arguments by the user: based on the provided input, it invokes the appropriate functions and uses their return values to compute the output.

#### Sample Usage

##### 1. Import as a module

```py
from math_utils import add, multiply

print(add(7, 3))
print(multiply(4, 5))
```

##### 2. Run directly as a standalone script

```bash
$ python math_utils.py add 7 3
10
$ python math_utils.py multiply 4 5
20
```

## Summing Up

Reusable standalone modules make code easier to understand, test, and maintain and can be used either independently or imported into other code. Thus they offer a practical way of building modular, reliable as well as versatile software components.

### Releted posts

* [Software Architecture Design for Busy Developers][1]
* [Unix Phylosophy with an Example][2]
* [Testability = Modularity][3]

[1]: {% link _posts/2019-09-05-software-architecture-design.md %}
[2]: {% link _posts/2019-03-02-unix-philosophy.md %}
[3]: {% link _posts/2020-01-15-testability-modularity.md %}
