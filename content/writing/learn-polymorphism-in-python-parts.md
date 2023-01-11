---
author: Paritosh Baghel
title: Learn Polymorphism through Python
date: 2023-01-11
description: Learn Polymorphism through Python
tags : [
    "Python",
    "Polymorphism",
]
---

Polymorphism is one of the fundamental concepts in object-oriented programming (OOP). It allows objects of different classes to be treated as objects of a common superclass. In other words, polymorphism enables objects to take on multiple forms. In this blog post, we'll explore how to use polymorphism in Python.

First, let's define a simple class hierarchy. We'll start with a base class called "Animal" and two derived classes, "Dog" and "Cat". Our Animals class will have a single method called "speak()", which we'll override in the derived classes to make the dog bark and the cat meow. Here's the code for the base class:

```python

class Animals:
    def speak(self):
        pass


```

And here's the code for the derived classes:

```python

class Dog(Animals):
    def speak(self):
        print("Bark")

class Cat(Animals):
    def speak(self):
        print("Meow")


```

Notice that the derived classes "Dog" and "Cat" inherit from the base class "Animals" and override the speak() method to provide their own implementation.

Now, let's create some objects of the Dog and Cat classes and call their speak() methods:

```bash

dog = Dog()
dog.speak() # prints "Bark"

cat = Cat()
cat.speak() # prints "Meow"

```

In this example, the variable "dog" is an object of the class "Dog" and the variable "cat" is an object of the class "Cat". Since both classes inherit from the base class "Animals" we can treat them as objects of the base class. This is where polymorphism comes in: we can define a function that takes an object of the base class "Animals" and calls the speak() method on it, and it will work regardless of whether the object is a dog or a cat.


```python

def make_animal_speak(animal: Animals):
    animal.speak()

make_animal_speak(dog) # prints "Bark"
make_animal_speak(cat) # prints "Meow"


```

This example demonstrates that an object of a derived class can be used wherever an object of its base class is expected. This is the essence of polymorphism: the ability to use objects of different types interchangeably.

It is worth mentioning that polymorphism is also implemented through duck typing in Python, where it is not important what the class of the object is but that it has the method that is expected which allows for flexibility in the types of objects passed to a function.

In conclusion, polymorphism is a powerful feature of OOP that allows objects of different classes to be treated as objects of a common superclass and it can be implemented in Python through inheritance and duck typing. Understanding how to use polymorphism in your code can help you write more flexible and reusable code.