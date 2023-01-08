---
author: Paritosh Baghel
title: "Testing replit to embed in blog"
date: 2023-01-08
description: "Testing replit to embed in blog"
tags : [
    "replit",
    "python"
]
---

This blog article is for my blog's "Replit" embed code. To activate this feature, I need to make a minor adjustment.

First, I have enable following setting in config

```yaml

markup:
  goldmark:
    renderer:
      unsafe: true


```

Second, Declare an IFrame in markdown in order to display it.

<iframe frameborder="0" width="100%" height="500px" src="https://replit.com/@paritoshsingh/pythonprint?embed=true&output=embed"></iframe>

