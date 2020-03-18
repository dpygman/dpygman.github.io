---
title: "Concatenating Multiple String Variables"
date: 2020-03-17
tags: [python, variables, strings, text, spaces]
excerpt: "Concatenating Multiple String Variables"

---

Hello and welcome to a quick overview of concatenating multiple string variables into a sentence. Please note, Python variables are case sensitive, so capitalization matters.

#### Example 1: How to concatenate with _NO_ spaces between the string variables:

```
a = "I"
b = "love"
c = "Python!"

print(a+b+c)
```
IlovePython!

Now, notice the difference using commas:

#### Example 2: How to concatenate with spaces between the string variables:

```
a = "I"
b = "love"
c = "Python!"

print(a,b,c)
```
I love Python!

The output "I love Python!" now contains sapces between the text.

### Variable Naming Restrictions
1. No Python keywords or functions
2. No spaces
3. Only letters or underscores as a line's first text
4. Only composed of letters, numbers, and underscores
