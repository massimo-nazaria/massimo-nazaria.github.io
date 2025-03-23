---
layout: post
title: Testability = Modularity
description: This article shows how modularity and testability are strongly related by explaining how testability issues imply modularity issues.
redirect_from:
  - /blog/2020/01/15/testability-equals-modularity.html
---

Let's see how a testable [software architecture][1]{:target="_blank"} is also modular, and vice versa!

## Practical Definition of Testability

[Testability][2]{:target="_blank"} is the quality which enables the developer to easily test a software [component][3]{:target="_blank"} separately from the rest of the architecture.

Thus, a testable architecture is one which is made of components that are easily testable in isolation.

How do the latter sentences relate to [modularity][4]{:target="_blank"}?

## Testability Issues Imply Modularity Issues

Simply put, any difficulty in testing a component separately from its architecture context, indicates lack of modularity.

Consequently, if it's difficult to test a component in isolation, then the architecture is neither testable nor modular.

## Reasons Behind Lack of Testability

Lack of testability (i.e., lack of modularity) in an architecture sets in in the presence of _highly coupled_ and _low cohesive_ components, contrary to the definition of modularity.

Brief recap from "_[Software Architecture Design Fundamentals for Busy Developers][5]_": a modular architecture is made of _[loosely coupled][6]{:target="_blank"}_ and _[highly cohesive][7]{:target="_blank"}_ components.

As a matter of fact, highly coupled and low cohesive components are very difficult to test independently from each other, let's see how.

### Highly Co-Dependent Components with Low Cohesive Functionalities

Any highly coupled component being put in isolation will instantly exhibit unmet external dependencies, which require difficult [mocking][8]{:target="_blank"}.

Namely, the implementation of complex software artifacts must be carried out in order to replicate the missing functionalities which the component depends on.

The lower the cohesiveness of functionalities within a component under test, the higher the number of unmet co-dependencies to be replicated.

In conclusion, a non-modular architecture makes testing activities tedious, error-prone, and time-consuming because of difficult mocking to be undergone.

## Practical Testability-Based Architecture Design

Taking into account testability makes architecture design more practical and effective.

Namely, designers together with developers can help each other make better design decisions due to the following facts.

First, any testability issue in the initial design indicates lack of modularity, which is a clear and useful warning sign for designers.

Second, developers can concretely point out potential testability issues in the initial design, which makes the decision-making process more practical.

Last but not least, designing an architecture in the above-mentioned way helps to effectively tackle [software erosion][9]{:target="_blank"} phenomenon by:

* keeping the architecture modular (i.e., testable), as well as
* keeping the implementation aligned with the corresponding architecture.

## Related Posts

* [Software Architecture Design Fundamentals for Busy Developers][5]
* [Mind the Architecture-Code Gap][10]

[1]: https://en.wikipedia.org/wiki/Software_architecture
[2]: https://en.wikipedia.org/wiki/Software_testability
[3]: https://en.wikipedia.org/wiki/Component-based_software_engineering#Definition_and_characteristics_of_components
[4]: https://en.wikipedia.org/wiki/Modular_programming
[5]: {% link _posts/2019-09-05-software-architecture-design.md %}
[6]: https://en.wikipedia.org/wiki/Loose_coupling
[7]: https://en.wikipedia.org/wiki/Cohesion_(computer_science)#High_cohesion
[8]: https://en.wikipedia.org/wiki/Mock_object
[9]: https://en.wikipedia.org/wiki/Software_architecture#Software_architecture_erosion
[10]: {% link _posts/2019-03-13-technical-debt.md %}
