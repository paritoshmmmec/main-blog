---
author: Paritosh Baghel
title: "How to declare variable in golang"
date: 2022-06-30
description: "How to declare variable in golang"
math: true
tags : [
    "golang",
]
---

## Introduction

I have been investing some time learning `golang` syntax. This blog contains  

1) Zero Values : Go, like most modern languages, assigns a default zero value to any variable that
is declared but not assigned a value. Having an explicit zero value makes code
clearer and removes a source of bugs found in C and C++ programs. As we talk
about each type, we will also cover the zero value for the type.

2) Literals : A literal in Go refers to writing out a number, character, or string. There are four
common kinds of literals that you’ll find in Go programs. (There’s a rare fifthkind of literal that we’ll cover when discussing complex numbers.)
Integer literals are sequences of numbers; they are normally base ten, but
different prefixes are used to indicate other bases: 0b for binary (base two), 0o
for octal (base eight), or 0x for hexadecimal (base sixteen). You can use either or
upper- or lowercase letters for the prefix. A leading 0 with no letter after it is
another way to represent an octal literal. Do not use it, as it is very confusing.
