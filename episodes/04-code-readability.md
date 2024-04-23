---
title: Code readability
teaching: 60
exercises: 30
---

:::::::::::::::::::::::::::::::::::::: questions 

- Why does readable code matter?
- How can I organise my code to be more readable?
- What types of documentation can I include to improve the readability of my code?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Organise code into reusable functions that achieve a singular purpose
- Create function and variable names that help explain the purpose of the function or variable
- Write informative inline comments and docstrings to provide more detail about what the code is doing

::::::::::::::::::::::::::::::::::::::::::::::::

### Variable names

:::::::::::::::::::::::::::::::::::::: challenge

### Give a descriptive name to a variable

Below we have a variable called `var` being set the value of 9.81.
`var` is not a very descriptive name here as it doesn't tell us what 9.81 means, yet it is a very common constant in orbital mechanics!
Go online and find out which constant 9.81 relates to and suggest a new name for this variable.

Hint: the units are _metres per second squared_!

```python
var = 9.81
```

:::::::::::::: solution

### Solution

Yes, 9.81 m/s^2 is the [gravitational force exerted by the Earth](https://en.wikipedia.org/wiki/Gravity_of_Earth).
It is often referred to as "little g" to distinguish it from "big G" which is the [Gravitational Constant](https://en.wikipedia.org/wiki/Gravitational_constant).
A more decriptive name for this variable therefore might be:

```python
g_earth = 9.81
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

## Further reading

We recommend the following resources for some additional reading on the topic of this episode:

- ...
- ...

Also check the [full reference set](learners/reference.md#litref) for the course.


:::::::::::::::::::::::::::::::::::::::: keypoints

- Readable code is easier to understand, maintain, debug and extend!
- Creating functions from the smallest, reusable units of code will help compartmentalise which parts of the code are doing what actions
- Choosing descriptive variable and function names will communicate their purpose more effectively
- Using inline comments and docstrings to describe parts of the code will help transmit understanding, and verify that the code is correct

::::::::::::::::::::::::::::::::::::::::::::::::::

