---
author: Paritosh Baghel
title: "Python Data Structure - List"
date: 2022-06-22
description: "Python: List"
tags : [
    "Python",
    "List",
]
---


## Introduction

In computer science, a data structure is a data organization, management, and storage format that is usually chosen for efficient access to data. Python provides several data structurs for data storage and retrivals. In todays blog we will discuss one of the widly used data structure called `list`.


## List

Lists are mutable sequences, typically used to store collections of homogeneous items. e.g. If we want to store the names of comedians, we can declare a list like below.

``` Python
 # Declare a list of comedians
 first_names = ["David", "Conan", "Bill"]
```

## How to iterate the list

There are couple of ways you can enumerate list. 

### Using For loop 

This is a standard way to iterate through list elements.

``` Python
 # Declare a list of comedians
 first_names = ["David", "Conan", "Bill"]

 for name in first_names:
    print(name)

 # Prints
 David
 Conan
 Bill

```

### Using enumerate()

The enumerate() function is a built-in function that returns an enumerate object. This lets you get the index of an element while iterating over a list along side with value itself. In example below it will print the index of comedian with names.

``` Python
 # Declare a list of comedians
 first_names = ["David", "Conan", "Bill"]

 # Note: index is available now.
 for index, name in enumerate(first_names):
    print(index, ",",name)

 # Prints
 0 David
 1 Conan
 2 Bill

```

Index certainly is useful in cases where you want to break out of loop based upon some other conditions.

**Note**: enumerate method returns an iterator, it means there is no overhead if you call enumerate method.

### Using list comprehension

List comprehension offers a shorter syntax when you want to create a new list based on the values of an existing list. e.g. if you want to create a new list based upon the existing list, you write something similar,

``` Python
# Before

fruits = ["apple", "banana", "cherry", "kiwi", "mango"]
newlist = []

for x in fruits:
  if "a" in x:
    newlist.append(x)

print(newlist)
 
```

``` Python
# After

fruits = ["apple", "banana", "cherry", "kiwi", "mango"]

newlist = [x for x in fruits if "a" in x]

print(newlist)
 
```

Now it is certainly Beautiful is better than ugly. [Learn More about Zen of Python]({{< ref  path="The-Zen-of-Python.md"  >}} "Learn More about Zen of Python") 