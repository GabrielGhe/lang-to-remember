PythonToRemember
=================
Things to remember for python

<h3 id="tableOfContent">Table of content</h3>
<ol>
  <li><a href="#1-string">Strings</a></li>
  <li><a href="#2-string">Probability</a></li>
</ol>

<h3 id="string"><a href="#table-of-content">1. String</a></h3>
```python
x = raw_input()  # "A bcdefg  "

len(x)    # 10
x[0]      # A
sorted(x) # [' ', ' ', ' ', 'A', 'b', 'c', 'd', 'e', 'f', 'g']
"".join( sorted(x) )  # "   Abcdefg"

```

<h3 id="string"><a href="#table-of-content">2. Probability</a></h3>
```python
import itertools

itertools.combinations(array,x) # array choose x
for comb in itertools.combinations(array,x):
  # do stuff
```
