---
title: "Python: Concatenating Multiple Text String Variables"
date: 2020-03-17
tags: [python, variables, strings, text, spaces, concatenating]
excerpt: "Python Concatenating Multiple Text String Variables"

---

Hello and welcome to a quick overview of concatenating multiple string variables into a sentence. Please note, Python variables are case sensitive, so capitalization matters.

#### What is concatenating strings?

Concatenating is using the plus (+) sign between strings to build longer strings.

#### Example 1: How to concatenate with _NO_ spaces between the string variables:
```
>>>a = "I"
>>>b = "love"
>>>c = "Python!"

>>>print(a+b+c)
```
IlovePython!

---

Now, notice the difference using commas:

#### Example 2: How to compse a string list with spaces between the string variables:
```
>>>a = "I"
>>>b = "love"
>>>c = "Python!"

>>>print(a,b,c)
```
I love Python!

The output "I love Python!" now contains spaces between the text.

#### Conclusion
Concatenating utilizes the plus sign between strings to create a single, long run-on string. If the intent is to create something like a sentence utilizing different strings, then commas are the best way to go.

