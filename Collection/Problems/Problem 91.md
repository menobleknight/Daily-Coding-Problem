## Problem 91

***Asked by Dropbox.***

**What does the below code snippet print out? How can we fix the anonymous functions to behave as we'd expect?**
```python
functions = []
for i in range(10):
    functions.append(lambda : i)

for f in functions:
    print(f())
```
<!-- https://github.com/vineetjohn/daily-coding-problem -->
