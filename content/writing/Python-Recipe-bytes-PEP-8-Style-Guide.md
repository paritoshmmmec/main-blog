---
author: Paritosh Baghel
title: "Python Recipe bytes: PEP 8 Style Guide"
date: 2023-01-06
description: "Python Recipe bytes: PEP 8 Style Guide" 
tags : [
    "Python"
]
---

Python Enhancement Proposal #8, otherwise known as PEP 8, is the style guide for how to format Python code. You are welcome to write Python code any way you want, as long as it has valid syntax. However, using a consistent style makes your code more approachable and easier to read. Sharing a common style with other Python programmers in the larger community facilitates collaboration on projects. But even if you are the only one who will ever read your code, following the style guide will make it easier for you to change things later, and can help you avoid many common errors.

PEP 8 provides a wealth of details about how to write clear Python code. It continues to be updated as the Python language evolves. It’s worth reading the whole guide online ([https://www.python.org/dev/peps/pep-0008/](https://www.python.org/dev/peps/pep-0008/)). Here are a few rules you should be sure to follow.

#### Whitespace

1. Use spaces instead of tabs for indentation.
    
2. Use four spaces for each level of syntactically significant indenting.
    
3. Lines should be 79 characters in length or less.
    
4. Continuations of long expressions onto additional lines should be indented by four extra spaces from their normal indentation level.
    
5. In a file, functions and classes should be separated by two blank lines.
    
6. In a class, methods should be separated by one blank line.
    
7. In a dictionary, put no whitespace between each key and colon, and put a single space before the corresponding value if it fits on the same line.
    
8. Put one—and only one—space before and after the `=` operator in a variable assignment.
    
9. For type annotations, ensure that there is no separation between the variable name and the colon, and use a space before the type information.
    

#### Naming functions

1. Functions, variables, and attributes should be in `lowercase_underscore` format.
    
2. Protected instance attributes should be in `_leading_underscore` format.
    
3. Private instance attributes should be in `__double_leading_underscore` format.
    
4. Classes (including exceptions) should be in `CapitalizedWord` format.
    
5. Module-level constants should be in `ALL_CAPS` format.
    
6. Instance methods in classes should use `self`, which refers to the object, as the name of the first parameter.
    
7. Class methods should use `cls`, which refers to the class, as the name of the first parameter.
    

#### Expressions and Statements

1. Use inline negation (`if a is not b`) instead of negation of positive expressions (`if not a is b`).
    
2. Don’t check for empty containers or sequences (like `[]` or `''`) by comparing the length to zero (`if len(somelist) == 0`). Use `if not somelist` and assume that empty values will implicitly evaluate to `False`.
    
3. The same thing goes for non-empty containers or sequences (like `[1]` or `'hi'`). The statement `if somelist` is implicitly `True` for non-empty values.
    
4. Avoid single-line `if` statements, `for` and `while` loops, and `except` compound statements. Spread these over multiple lines for clarity.
    
5. If you can’t fit an expression on one line, surround it with parentheses and add line breaks and indentation to make it easier to read.
    
6. Prefer surrounding multiline expressions with parentheses over using the `\` line continuation character.
    

#### Imports

1. Always put `import` statements (including `from x import y`) at the top of a file.
    
2. Always use absolute names for modules when importing them, not names relative to the current module’s own path. For example, to import the `foo` module from within the `bar` package, you should use `from bar import foo`, not just `import foo`.
    
3. If you must do relative imports, use the explicit syntax `from . import foo`.
    
4. Imports should be in sections in the following order: standard library modules, third-party modules, your own modules. Each subsection should have imports in alphabetical order.