---
author: Paritosh Baghel
title: Motivation for Writing Tests First
date: 2021-03-12
description: Motivation for Writing Tests First
math: true
tags : [
    "TDD",
    "test",
]
---

### Introduction

You might be wondering that "ugh, not another article about TDD" and I agree with you. There are millions of articles that are out there. If you are new to TDD, please read them before reading this blog.

I would say that I am not writing this article to inform you about regular TDD articles (test, code and refactor ) but rather telling you about why you should use TDD more and move away from Jargon itself. 

Over the years, developers I worked or currently working with 
loathe Test-driven development and in my opinion, the problem is no one clearly tells developers why to think in terms of Test first can significantly increase code quality and stability for change to come.

### Component-based development

Developers may be able to break down complex systems into smaller components or units of development, so each unit can be developed or tested individually. This is what refers to lego based development. By embracing the test-first approach can let you enable this feature. 

![Untitled Diagram.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1602333482741/bz-9yHbN4.jpeg)


### Detect code smells 

While writing tests for a given unit of functionality, code smells can be detected very early in the life cycle of development e.g.
 
- Too much **dependency **on some component: If unit tests are big and hard to set up or stub, something is wrong with the current component being tested (SUT). Too many parameters also can introduce unexpected complexity.

- **Unexpected responsibility**: Writing tests can give a sense of a clear cut sense of responsibility for the current component (SUT). If a component is charging the customer and creating the order, it might need to be broken down into its own components.


### Specification for input and output

By writing tests, you can write an exact specification of a component or SUT. This means developers who are consuming this component can be sure what this component does or when this component will return failure. This is very similar to how structural engineers write their specifications. By specifying the component's responsibility, code review can help you improve the codebase.


![buyingspecif-bcon.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1602361634617/rV7RJhrYI.jpeg)


### Can be tested individually 

Unit testing a component without worrying about the dependencies can give you a real advantage when you are trying to reproduce a behavior or adding a new feature. This also can give code reviewers an advantage while reviewing functionality.

This is very similar to an ammeter that can detect the current b/w two points of an electric component. 



![ammeter-circuit.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1602362482302/gzXLgkTqE.jpeg)


### Evaluate design decisions

The only thing constant in the software industry is requirement changes so does the codebase. If software constantly changing, so the requirement of the component will also change. It means the design of components will also change. If you have backing tests previously, embracing change can be very simple.

With the help of tests, you will make sure you are not breaking the existing functionality. New developers can make changes on their own because every component has document test cases. 

### Summary

Test-based written software can embrace changes easily and can make you very productive. It can be hard in the beginning but after some time it can be very rewarding.