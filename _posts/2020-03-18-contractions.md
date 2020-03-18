---
title: "Python: Using Contractions"
date: 2020-03-18
tags: [python, contractions]
excerpt: "Python: Using Contractions"

---

## Informal Writing in Python utilizing Contractions
In some instances, programmers want to use informal writting in Python.

__Example__

Cannot to Can't

Since many programmers avoid informal writting, they many never learn how to utilize Python code to insert contractions into 'single quote' strings.

Note: While utilizing "double quotes" resolves the potential issue, many programers prefer to utilize 'single quotes' to reduce shift keystrokes (e.g., shift + ").

### So how do 'single quote' programmers insert contractions into a string?

__Single Quote Example:__
```
>>>a='can\'t'
>>>print(a)
```
can't

Inserting the backslash \ symbol instructed Python to continue past the 'single quote' to close the string.

__Double Quote Example__
```
>>>a="can't"
>>>print(a)
```
can't

The "double quotes" cause Python to skip over the 'single quote' in can't and continue to the last "double quote" to end the string.
