---
jupytext:
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.10.3
kernelspec:
  display_name: Python 3
  name: python3
---

# For loops and vectors problems


## Prerequisites

- Watch the [video about vectors](https://www.youtube.com/watch?v=fNk_zzaMoSs)
  by 3Blue1Brown (optionally read [video text](https://www.3blue1brown.com/lessons/vectors)).
- View the visualizations about [radians](https://twitter.com/FreyaHolmer/status/1173752820954214400),
  [sin/cos/tan](https://twitter.com/FreyaHolmer/status/1173376419168247810),
  [dot product](https://twitter.com/FreyaHolmer/status/1200807790580768768),
  and [cross product](https://twitter.com/FreyaHolmer/status/1203059678705602562)
- Review Collections: Lists section. This is important because we can use lists
  to represent vectors in Python, for example the two-dimensional vector can be defined as `v = [3,2]`
- Complete the section on for loops in 07-Loops notebook.
  The for loop is important because it allows you to do operations for each element in the list.
- Review the Fundamentals of math notebook from Sympy (Appendix C in print book)
- Complete the SymPy > Vectors notebook to learn how to define and use vectors in SymPy.
  Note we use Matrix object giving it a list as input, e.g. `v = Matrix([3,2])`
  This is a little weird, but OK because a vector is a special type of matrix.
- Solve all exercises in Chapter 7, as well as E6.4, E6.5
- Solve all problems from P9.57 until P9.65 (inclusive)


+++

## Lists and for loops

Let's review what we've learned about Python lists and for loops because they will be useful for vector calculations in the next step.

```{code-cell}
scores = [61.0, 85.0, 92.0, 72.0]  # define a list of floats
scores
```

```{code-cell}
# lists have a "length"
len(scores)
```

```{code-cell}
# elements of a list are acccessed using [ ] and 0-based index
scores[0]  # first score
```

```{code-cell}
# lists can be sorted
sorted(scores)  # returns a new list of sorted scores
```

```{code-cell}
scores
```

```{code-cell}
scores.sort()  # in-place sort the list
scores
```

```{code-cell}
scores.reverse()
scores
```

```{code-cell}
scores.append(22)
```

```{code-cell}
scores
```

```{code-cell}
scores.insert(2, 25)
scores
```

```{code-cell}
scores.pop()
```

Just like `.sort()` method, lists have all kinds of useful methods `.insert`, `.remove`, `.pop`, `.reverse`, ...  

You can see all those methods by starting to type `scores.` then pause for a second to see the auto-complete suggestions:

```{code-cell}
# scores.
```

```{code-cell}
scores = [61.0, 85.0, 92.0, 72.0]
scores.sort()
```

## For loops

The "for loop" is a Python code construct of the form:
```
for el in container:
    <operations on el>

```
that allows to repeat a block of operations **for each element of the list**.


```{code-cell}
# Example 1: print all the scores
for score in scores:
    print(score)
```

```{code-cell}
# Example 2: compute the average score  ==  sum(scores)/len(scores)
total = 0
for score in scores:
    total = total + score

total/len(scores)
```

The name of the variable used for the for loop is totally up to you, but in general you should choose logical names for elements of the list.

Here is a for loop that uses the single-letter variable:

```{code-cell}
for s in scores:
    print(s)



for (i=0; i<length(scores); i=i+1){
    s = scores[i];
    print(s);
}
```

```{code-cell}
scores
```

```{code-cell}
enumerate(scores)
```

```{code-cell}
# Bonus concept: use `enumerate` to get pairs (index, value) from a list
# enumerate(scores) == [(0, 61.0), (1, 72.0), (2, 85.0), (3, 92.0)]

# example
for index, score in enumerate(scores):
    # this for loop has two variables index and score
    print("Processing score", score, "which is at index", index, "in the list")
```

```{code-cell}
# New concept: use `zip(list1,list2)` to get pairs (value1, value2) from two lists 
# list(zip([1,2,3], ['a','b','c'])) == [(1, 'a'), (2, 'b'), (3, 'c')]

# example
list1 = [1,2,3]
list2 = [3,3,5]
list3 = [11, 22, 33]

for value1, value2, value3 in zip(list1, list2, list3):
    print("Processing  value1 =", value1, " and  value2 =", value2, 'val3=', value3)

```

```{code-cell}
list1 = [1,2,3]
list2 = [3,3,5]


list(zip(list1, list2))
```

```{code-cell}

```

```{code-cell}

```

### List functions

Your turn to play with lists now! Complete the code required to implement the functions `compute_mean` and `compute_std` below.


#### Question 1: Mean

The formula for the mean of a list of numbers $[x_1, x_2, \ldots, x_n]$ is:
$$
    \text{mean} = \overline{x}
    = \frac{1}{n}\sum_{i=1}^n x_i
    = \tfrac{1}{n} \left[ x_1 + x_2 + \cdots + x_n \right].
$$


Write the function `compute_mean(numbers)`: a function that computes the mean of a list of numbers


```{code-cell}
def compute_mean(numbers):
    """
    Computes the arithmetic mean of the `numbers` list using a for loop.
    """
    total = 0
    for number in numbers:
        total = total + number
    mean = total/len(numbers)  
    return mean


compute_mean([100,101])
```

```{code-cell}
# TEST CODE (run this code to test you solution)

def random_list(n=10, min=0.0, max=100.0):
    """Returns a list of length `n` of random floats between `min` and `max`."""
    import random
    values = []
    for i in range(n):
        r = random.random()
        value = min + r*(max-min)
        values.append(value)
    return values


def test_compute_mean(function):
    """
    Run a few lists to check if value returned by `function` matches expected.
    """
    import math, statistics
    assert function([1,1,1]) == 1
    assert function([61,72,85,92]) == 77.5
    list10 = random_list(n=10)
    assert math.isclose(function(list10), statistics.mean(list10))
    list100 = random_list(n=100)
    assert math.isclose(function(list100), statistics.mean(list100))
    print("All tests passed. Good job y'all!")



# RUN TESTS
test_compute_mean(compute_mean)
```

```{code-cell}
(1 + 1e-15)  ==  1 
```

```{code-cell}
import math
math.isclose(1 + 1e-10, 1)
```


```{code-cell}

```

#### Question 2: Sample standard deviation

The formula for the sample standard seviation of a list of numbers is:
$$
    \text{std} = s
    = \sqrt{ \tfrac{1}{n-1}\sum_{i=1}^n (x_i-\overline{x})^2 }
    = \sqrt{ \tfrac{1}{n-1}\left[ (x_1-\overline{x})^2 + (x_2-\overline{x})^2 + \cdots + (x_n-\overline{x})^2\right]}.
$$

Note the division is by $(n-1)$ and not $n$. Strange, no? You'll have to wait until stats to see why this is the case.

Write `compute_std(numbers)`: computes the sample standard deviation


```{code-cell}
import math
import statistics

def compute_std(numbers):
    """
    Computes the sample standard deviation (square root of the sample variance)
    using a for loop.
    """
    mean = compute_mean(numbers) 
    total = 0
    for number in numbers:
        total = total + (number-mean)**2
    var = total/(len(numbers)-1)    
    return math.sqrt(var)

numbers = list(range(0,100))
compute_std(numbers)
```

```{code-cell}
# compare to known good function...
statistics.stdev(numbers)
```

```{code-cell}
# TEST CODE (run this code to test you solution)

def test_compute_std(function):
    """
    Run a few lists to check if value returned by `function` matches expected.
    """
    import math, statistics
    assert function([1,1,1]) == 0
    assert math.isclose(function([61,72,85,92]), 13.771952173409064)
    list10 = random_list(n=10)
    assert math.isclose(function(list10), statistics.stdev(list10))
    list100 = random_list(n=100)
    assert math.isclose(function(list100), statistics.stdev(list100))
    print("All tests passed. Good job y'all!")


# RUN TESTS
test_compute_std(compute_std)
```

```{code-cell}

```





## Vectors
A vector $\vec{v} \in \mathbb{R}^n$ is an $n$-tuple of real numbers:

$$
 \vec{v} = (v_1,v_2,v_3, \ldots, v_n) \  \in \  \mathbb{R}^n.
$$

To specify the vector $\vec{v}$, 
we specify the values for its components $v_1$, $v_2$, $v_3$, ..., $v_n$.

In Python, we can represent vectors as lists:

```{code-cell}
# the two-dimensional vector represented as a Python list
v = [3,2]
v
```

```{code-cell}
# try playing around with a vector using a for loop...
```

### Other ways of representing vectos (optional reading)

```{code-cell}
# Option 2: vector as a n-by-1 SymPy Matrix (useful for doing math calculations)
from sympy import Matrix
v_sym = Matrix([3,2])
v_sym
```

```{code-cell}
# Option 3: numpy array (useful for doing fast numerical calculations)
import numpy as np
v_np = np.array([3,2])
v_np
```

```{code-cell}
# Option 4: pandas series (used in statistics and data science)
# Option 5: pytorch array (used in machine learning)
```

### Vector functions

To get to know vectors better, you'll now implement a few common vector operations. Make sure all the functions you create work for vector of any length.

+++

### Question 3: 

Writh `norm(v)` a function that takes `n`-dimensional vector and computes its [Euclidean norm](https://en.wikipedia.org/wiki/Norm_(mathematics)#Euclidean_norm)

```{code-cell}
def norm(v):
    """
    Compute the L2-norm (Euclidean norm) of the vector `v` (a list).
    """
    total=0
    if len(v) in range(2,10):
       for number in v:
          total=total+(number)**2
       from math import sqrt    
       norm_of_v= math.sqrt(total)
       return float(norm_of_v)
          
```

```{code-cell}
# TEST CODE (run this code to test you solution)
import numpy

def test_norm(function):
    """
    Run a few lists to check if value returned by `function` matches expected.
    """
    from math import isclose
    assert isclose(function([1,1,1]), 1.7320508075688772)
    assert isclose(function([61,72,85,92]), 156.8247429457482)
    list3 = random_list(n=3)
    assert isclose(function(list3), numpy.linalg.norm(list3))
    print("All tests passed. Good job y'all!")
    
# END OF TEST CODE


# Let's run the tests...
test_norm(norm)
```

```{code-cell}

```


### Question 4

Write `dot(u,v)` a function that takes two n-dimensional vectors and computes their dot product:

```{code-cell}
def dot(u,v):
    """
    Takes two n-dimensional vectors and computes their dot product.
    """ 
    total = 0
    for ui, vi in zip(u,v):
        total = total + (ui*vi)
    return float(total)


```

```{code-cell}
# TEST CODE (run this code to test you solution)

def test_dot(function):
    """
    Run a few lists to check if value returned by `function` matches expected.
    """
    from math import isclose
    import numpy as np
    assert function([1,2], [3,4]) == 1*3 + 2*4
    u3 = random_list(n=3)
    v3 = random_list(n=3)
    assert isclose(function(u3,v3), np.array(u3).dot(np.array(v3)))
    for n in range(4, 10):
        un = random_list(n=n)
        vn = random_list(n=n)
        assert isclose(function(un,vn), np.array(un).dot(np.array(vn)))
    print("All tests passed. Good job y'all!")


# Let's run the tests...
test_dot(dot)
```

```{code-cell}

```



### Question 5:

Write `cross(u,v)`: a function that takes two 3-dimensional vectors and computes their cross product

```{code-cell}
def cross(u, v):
    """
    A function that computes the cross product u x v of the inputs u and v, which
    are assumed to be 3-dimensional vectors.
    Returns a list.
    """
    if len(u) != 3 or len(v) != 3:
        # this will make the function reject vectors that are not 3-dimensional
        raise ValueError("Inputs vects must have dim. 3, else cross product not defined.")
    cross = [(u[1]*v[2]-u[2]*v[1]),
             (u[2]*v[0]-u[0]*v[2]),
             (u[0]*v[1]-u[1]*v[0])]
    return [float(cross[0]),
            float(cross[1]),
            float(cross[2])]

```

```{code-cell}
# TEST CODE (run this code to test you solution)

def test_cross(function):
    """
    Run a few lists to check if value returned by `function` matches expected.
    """
    import numpy as np
    u3 = random_list(n=3)
    v3 = random_list(n=3)
    w3_computed = np.array( function(u3,v3), dtype=float)
    np.isclose(w3_computed, np.cross(np.array(u3), np.array(v3)))
    print("All tests passed. Good job!")


# Let's run the tests...
test_cross(cross)
```


```{code-cell}

```

### Question 6

Write the function `angle_between(u,v)`: a function that takes two n-dimensional vectors and computes their angle between them (answer returned should be in radians)

```{code-cell}
def angle_between(u, v):
    """
    Compute the angle between vectors `u` and `v` (answer returned in radians).
    """                                       
    cos_theta = dot(u,v)/(norm(v)* norm(v))
    import math  
    return math.acos(cos_theta)                                 # or ME: import math

```

```{code-cell}
# TEST CODE (run this code to test you solution)

def test_angle_between(function):
    """
    Run a few lists to check if value returned by `function` matches expected.
    """
    from math import isclose
    isclose(function([1,0], [0,1]), 1.5707963267948966)
    isclose(function([1,1], [1,0]), 0.7853981633974484)
    isclose(function([1,0],[-1,0]), 3.141592653589793)
    print("All tests passed. Good job!")


# Let's run the tests...
test_angle_between(angle_between)
```

```{code-cell}

```


### Things to discuss

```{code-cell}

## 1. imports
from math import acos
acos(1)
# vs
import math
math.acos(1)



## 2. list membership
v = [3,2]
len(v) == range(2,10)



## 3. joint-iteration over two lists using zip


## 4. float(cross) error


## 5. syntax for defining vs. calling functions


```

```{code-cell}

```

```{code-cell}

```
