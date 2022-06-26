---
author: Paritosh Baghel
title: Python Virtual Environment
date: 2022-06-26
description: Python Virtual Environment
tags : [
    "Python",
    "Virtual Environment",
]
---

## Why you should care about Virtual Environments?

Isolation provides reliability and reproducibility during deployments. Python enables a virtual environment to isolate application packages from system packages.

Let us imagine we are building a product that requires `NumPy` packages, one using version 2.2 and the other using version 3.5. If we use system-wide packages, one version will override another version. We do not want this kind of behavior during development or deployment.

Basically, setting up virtual environments is the best way to isolate different Python projects, especially if these projects have different and conflicting dependencies. As a piece of advice for new Python programmers, always set up a separate virtual environment for each Python project, and install all the required dependencies inside it — never install packages globally.

Isolation provides reliability and reproducibility during deployments. The virtual environment also helps during deployment as you might not have access to system-wide packages.

## How do I can check for global packages

You can run `pip list` command to get the list of packages. It enables you to monitor system-wide packages to avoid any future conflicts.

```bash
pip list
```

## Working with virtual environment

Python provides a in-built way to create and activate virtual environment. 


### Creating a Python Virtual Environment

First make a project folder, and create a virtual environment inside it. To do so, open the terminal app, write the following command, and hit return.

```bash
mkdir virtual-environment-sample && cd virtual-environment-sample
```

Run following command to create virtual environment:

```bash
python3 -m venv virtual-environment-sample-venv
```

This command will create folder named `virtual-environment-sample-env` in current directory. This folder contains `bin` folder in order to activate virtual enviroment. Let's activate it using following command:

```bash
source virtual-environment-sample-env/bin/activate
```

After activation, your command prompt should look similiar. Congrates you have activated the virtual enviroment succesfully.

```bash
(virtual-environment-sample-env) //removed for clarity
```

### Installing Packages in a Virtual Environment

We are now inside an isolated virtual environment where only pip and setup tools are installed by default. Let's check the pre-installed packages on the virtual environment by running the `pip list` command.

Note: Any changes to current setup will only affect current project, it has no knowledge of system wide packages.

Let us upgrade `pip` to test this theory. First let us check python version

```bash
python --version
```

Now upgrade `pip` using following commands:

```bash
 python -m pip install --upgrade pip
```

If you compare `pip` in system-wide packages and application packages, both are of different version. This is really great for development as I can develop software in isolation.

### Deactivating a Python Virtual Environment

Once you are done working with a virtual environment, or you want to switch to another virtual environment, you can deactivate an environment by running this command:

```
deactivate
```


## Summary

Python virtual environment is a very simple to isolate dependencies. There are other open source project which do the same thing e.g. conda, poetry. We will discuss this in future too.


## References

https://docs.python.org/3/library/venv.html
https://docs.conda.io/en/latest/miniconda.html
https://python-poetry.org/