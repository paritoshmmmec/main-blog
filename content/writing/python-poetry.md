---
author: Paritosh Baghel
title: "Poetry: Manage Python dependencies and packages" 
date: 2022-06-30
description: "Poetry: Manage Python dependencies and packages" 
tags : [
    "Python",
    "Beginner",
]
---

## Introduction

In our recent `fastapi` project, we used poetry as a dependency management tool and we're very happy about it. Although the `Poetry` [site](https://python-poetry.org/) is very well documented, I wanted to log my thoughts about it.

## What is Poetry

Poetry is a tool for dependency management and packaging in Python. It allows you to declare the libraries your project depends on and it will manage (install/update) them for you. It also provides a way to create and manage a virtual environment to run a program. Poetry can be used as a replacement for conda to manage packages and virtual environments.

## How to install and use it

Details installation instruction are [here](https://python-poetry.org/docs/#installation).


Once installed, create a new project using the following command:

```bash
poetry new poetry-demo
```

once done it will spit out the following structure:

```bash
poetry-demo
├── pyproject.toml
├── README.rst
├── poetry_demo
│   └── __init__.py
└── tests
    ├── __init__.py
    └── test_poetry_demo.py
```

A Couple of gotchas:

1) Poetry can't fully manage Python versions on its own using the version specified in the `pyproject.toml`. If on the host machine, there are a couple of versions of python have been installed, it will use the default `python` version to create the virtual environment. The Workaround is to use `pyenv` or some other tool to manage multiple `python` versions, or you can use `poetry env use path/to/python` to create a virtual environment.

2) Poetry is slow (not its fault), so if your project has complex dependencies, the first install will be pretty slow so don't get frustrated. 

## How to run a python program

Let us install the dependencies by running the following command:

```bash
poetry install 
```

This command will also create a virtual environment for you which is great. Now let's add a `hellopoetry.py` in the root directory and add the following code:

```python
print("Hello Poetry")
```

Now execute this script using the following command:

```bash 
 poetry run python hellopoetry.py
```

and voila!! you have run a basic python script using poetry.


## How to add packages

Add the `requests` package in to project by using this command:

```bash 
 poetry add requests
```

Although we do have not a specified version in the above command, Poetry has done a great job finding the correct version for it. Thanks to its fast dependency resolver!!! 

Remove the package from the project by using this command:

```bash 
 poetry add requests
```

Add a specific version to the project by using this command:

```bash 
 poetry add  requests=^2.28.0
```

Add a specific version to the project by modifying `pyproject.toml`:

```bash 
 //Add dependencies manually and then run the following command
 poetry update
```

## Summary

If you are starting a new project, Poetry is definitely a choice to manage packages and dependencies