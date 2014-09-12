PythonToRemember
=================
Things to remember for python

<h3 id="tableOfContent">Table of content</h3>
<ol>
  <li><a href="#1-arrays">Arrays</a></li>
  <li><a href="#2-dicts">Dicts</a></li>
  <li><a href="#3-numbers">Numbers</a></li>
  <li><a href="#4-probability">Probability</a></li>
  <li><a href="#5-string">Strings</a></li>
  <li><a href="#6-other">Other</a></li>
</ol>

<h3 id="arrays"><a href="#table-of-content">1. Arrays</a></h3>
```python
x = list("4321")  # ["4", "3", "2", "1"]
x.append("val1")  # ["4", "3", "2", "1", "val1"]
x.pop()           # ["4", "3", "2", "1"]
x.sort()          # ["1", "2", "3", "4"]
x.reverse()       # ["4", "3", "2", "1"]
x = x[::-1]       # ["1", "2", "3", "4"]
max(x)            # "4"

y = ["ab", "cde", "efgh", "ij"]
sorted(y, key = len)    # ['ab', 'ij', 'cde', 'efgh']
sorted(y, key = len, reverse = True)  # ['efgh', 'cde', 'ab', 'ij']
```

<h3 id="dicts"><a href="#table-of-content">2. Dicts</a></h3>
```python
dict = {"y": 6, "x": 5}
dict.keys()   # ["y", "x"]
dict.values() # [6, 5]
dict["z"] = 4 # {"y": 6, "x": 5, "z": 4}
```

<h3 id="numbers"><a href="#table-of-content">3. Numbers</a></h3>
```python
int("4")    # 4
int(5, 2)   # 101
2**3        # 8 (2^3)
4**.5       # 2.0
```

<h3 id="probability"><a href="#table-of-content">4. Probability</a></h3>
```python
import itertools

itertools.combinations(array,x)  # array choose x
for comb in itertools.combinations(array,x):
  # do stuff
  
itertools.permutations(arr, x)   # permutation
for comb in itertools.permutations(array,x):
  # do stuff
  

```

<h3 id="string"><a href="#table-of-content">5. String</a></h3>
```python
x = raw_input()  # "A bcdefg  "

len(x)      # 10
x[0]        # "A"
sorted(x)   # [' ', ' ', ' ', 'A', 'b', 'c', 'd', 'e', 'f', 'g']

x.lower()   # "a bcdefg  "
x.upper()   # "A BCDEFG  "

x += str(5) # "A bcdefg  5"
x[:-1]      # "A bcdefg  "
x[2:4]      # "bc"         x[startIndex:endIndexExluded:step]

x.title()       # "A Bcdefg  "
x[0].isalpha()  # True
x[0].isdigit()  # False

x.split()       # ["A", "bcdefg"]
"".join( sorted(x) )  # "   Abcdefg"
```

<h3 id="other"><a href="#table-of-content">6. Other</a></h3>
```python
# ternery
5 if booleanValue else 6  # (booleanValue)? 5 : 6;

# generate new list from existing list
x = ['a', '1', 'b', '2', 'c', '3', 'd', '4']
x = [c for c in x if c.isalpha()]   # ['a', 'b', 'c', 'd']
x = [c for c in x if c.isdigit()]   # ['1', '2', '3', '4']

# get idx and value in loop
for idx, val in enumerate(array):

# sets
# https://docs.python.org/2/library/sets.html
set([1, 1, 3, 5, 6, 6, 4])          # set([1, 3, 4, 5, 6])
```
