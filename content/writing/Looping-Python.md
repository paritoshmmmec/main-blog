---
author: Paritosh Baghel
title: "Python Recipe bytes:Looping"
date: 2023-01-04
description: "Python Recipe bytes:Looping" 
tags : [
    "Python Recipe bytes:Looping"
]
---

### How do I loop a list of names?

```python

names = ["John", "Vicky"]

for name in names:
    print(name)

```

### How do I loop a list with index for each item?

```python

names = ["John", "Vicky"]

for (index, name) in enumerate(names):
    print(f"Index number : {index} first name {name} trophies")

```

### How do I loop a dictionary with key only?

```python

number_of_trophies_won_by_country = {"Aregentina": 3, "Brazil": 5, "Italy": 3}

for country in number_of_trophies_won_by_country:
  print(f"{country} won {number_of_trophies_won_by_country[country]} trophies")

```

### How do I loop a dictionary with list of keys?

```python

for country in number_of_trophies_won_by_country.keys():
  print(f"{country} won {number_of_trophies_won_by_country[country]} trophies")

```


### How do I loop a dictionary with list of values only (I dont care about keys)?

```python

for number_of_trophies in number_of_trophies_won_by_country.values():
  print(number_of_trophies)

```

### How do I loop a dictionary with key and value in one shot?

```python

for (country, number_of_trophies) in number_of_trophies_won_by_country.items():
  print(f"{country} won {number_of_trophies} trophies")

```

### How do I loop a dictionary with index of each item?

```python

for (index, country) in enumerate(number_of_trophies_won_by_country):
  print(f"index: {index} {country} won {number_of_trophies_won_by_country[country]}")

```