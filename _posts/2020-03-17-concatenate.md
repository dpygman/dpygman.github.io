---
title: "Python: Concatenating Multiple Text String Variables"
date: 2020-03-17
tags: [python, variables, strings, text, spaces, concatenating]
excerpt: "Python Concatenating Multiple Text String Variables"

---

Hello and welcome to a quick overview of concatenating multiple string variables into a sentence. Please note, Python variables are case sensitive, so capitalization matters.

#### Example 1: How to concatenate with _NO_ spaces between the string variables:

```
>>>a = "I"
>>>b = "love"
>>>c = "Python!"

>>>print(a+b+c)
```
IlovePython!

Now, notice the difference using commas:

#### Example 2: How to concatenate with spaces between the string variables:

```
>>>a = "I"
>>>b = "love"
>>>c = "Python!"

>>>print(a,b,c)
```
I love Python!

The output "I love Python!" now contains spaces between the text.