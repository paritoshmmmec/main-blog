---
author: Paritosh Baghel
title: "Ways to initialize String in Rust"
date: 2023-10-10
description: "Ways to initialize String in Rust"
tags : [
    "rust",
]
---

{{< highlight rust >}}
fn main() {
    let hello_world = String::from("I 💖 rust");
    println!("{hello_world}");

    let another_world = String::from_str("Hello my 💖!!!!").unwrap();
    println!("{another_world}");

    let sparkle_heart =  vec![240, 159, 146, 150];
    let sparkle_heart = String::from_utf8(sparkle_heart).unwrap();
    println!("{sparkle_heart}");

    let mut sparkle_heart = String::new();
    sparkle_heart.push_str("Hello world!!!");
    println!("{sparkle_heart}");
}

{{< /highlight >}}