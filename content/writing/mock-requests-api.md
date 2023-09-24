---
author: Paritosh Baghel
title: How to mock request operation correctly
date: 2023-09-23
description: How to mock request operation correctly
tags : [
    "Python",
    "Unit Testing",
    "Requests"
]
---

# Introduction

Mocking is a way to replace dependencies while writing unit tests. Python is very flexible thus provides various way to achieve same thing. I recently was writing a unit test and found that `requests` library can be mocked in several ways. 
After digging, I found couple of ways to fix it.

#### Directory structure

* src
  * sut.py (subject under test file)
* tests
  * test_sut.py

# First way: Using `side_effect` method

``` 
{{< highlight python >}}

class Sut:
    def call_api(self):
        return requests.get("https://httpbin.org/ip").json()

{{< /highlight >}}
```


```

@patch('src.sut.requests.get')
def test_request_api_call_version2(mock_request_call):
    mock_request_call.return_value = MockedResponse()
    sut = Sut()
    data = sut.call_api()
    assert data
    assert data == {"ip": "mocked_ip"}


```