---
author: Paritosh Baghel
title: "Installing Python on debian"
date: 2022-06-18
description: "Python - Install python on debian"
tags : [
    "Python",
    "debian",
]
---

Python 3.9 is the latest major release of the Python language. It includes many new features such as new dict operators, new str functions, support for IANA time zone, and more .

In this article, we'll show you how to install Python 3.9 on Debian 10.

## Installing Python 3.9 on Debian 10

### Install the dependencies necessary to build Python:

```bash
sudo apt install wget
sudo apt install build-essential zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev libssl-dev libsqlite3-dev libreadline-dev libffi-dev curl libbz2-dev
```

### Download the latest release's source code from the Python download page with wget :

```bash
wget https://www.python.org/ftp/python/3.9.1/Python-3.9.1.tgz
```

### Once the download is complete, extract the gzipped archive :
```bash
tar -xf Python-3.9.1.tgz
```

### Navigate to the Python source directory and execute the configure script:
```bash
cd Python-3.9.1
./configure --enable-optimizations
```

The --enable-optimizations option optimizes the Python binary by running multiple tests. This makes the build process slower.

The script runs a number of checks to make sure all of the dependencies on your system are present:

### Start the Python 3.9 build process:
```bash
make -j 2
```
For faster build time, modify the -j to correspond to the number of cores in your processor. You can find the number by typing nproc.

### When the build process is complete, install the Python binaries by typing:
```bash
sudo make altinstall
```

That's it. Python 3.9 has been installed and ready to be used. To verify it, type:

```bash
python3.9 --version
```

## Conclusion 
We’ve shown you how to install Python 3.9 on your Debian 10 system. You can now create a virtual environment and start developing your Python projects.
