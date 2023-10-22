---
author: Paritosh Baghel
title: "Rust notes"
date: 2023-10-21
description: "Rust notes"
tags : [
    "Rust notes",
]
---

- Learn the difference between stack and heap.
- Understand reference and value type.
- Rust has some really strange syntax, but dont give up.
- Data structure is core to any program so master 
- Value type gets allocated on the stack due to its fixed size, whereas the reference type gets allocated on the heap because the size is not known until it is required. Heap allocation is slower than stack allocation.
- Rust does not have a garbage collector so memory management is mostly your responsibility (well sort of). Compiler will enable you to efficiently manage your memory and write better programs.
- Rust Complier is your friend, stop fighting it. It will help you write better programs.
- There can only be one owner for each variable. However, It is possible to borrow or transfer ownership.
- Assignment means you are the owner of variable
- You can borrow ownership with `&` and mutate it using `mut` keyword.
- Any modification needs to be explicitly stated using `mut` keyword. 