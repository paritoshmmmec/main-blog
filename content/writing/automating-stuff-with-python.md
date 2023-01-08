---
author: Paritosh Baghel
title: "Automate stuff with python - Calibre"
date: 2023-01-07
description: "Automate stuff with python - Calibre"
tags : [
    "Automate",
    "python",
    "Calibre"
]
---

### Introduction

One of the reasons python language is so popular as it enables people to automate small chores around the work. Recently I was stuck with one of the problems. I use `Calibre` Library for ebook management regularly. If you have tried `Calibre` tool yet, I would highly recommend it.

### Problem

One of the challenges with Calibre is that it organizes books into nested folders based on the author's name, which can make it difficult to locate a specific book if you don't remember the author's name. If you want to search for a book without using the `Calibre` tool, it can be time-consuming to manually browse through the folders organized by author name, even if you know the name of the author you are looking for. I noticed this frustration in the `Calibre` community too.

### Solution

1. Read the source folder and make a list of all files (nested or otherwise).
    
2. Loop through files and filter them by media type.
    
3. Copy the file using \`shutil\` library.
    
4. Enjoy your coffee.
    

```python

import pathlib
import shutil
    
sourcefolder = "C:\\Users\\Paritosh Baghel\\Calibre Library"
destination = "C:\\codebase\\books"
file_list_source = [str(path) for path in pathlib.Path(sourcefolder).rglob("*.*") if path.is_file()]

for source_file in file_list_source:
  if 'pdf' in source_file or 'epub' in source_file or 'mobi' in source_file:
    shutil.copy(source_file, destination)

```

### Conclusion

Python can be used to automate tedious housework. You'll gain a broad understanding of programming and save time by using it.