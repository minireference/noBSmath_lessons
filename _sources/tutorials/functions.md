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

# Python Coding Tutorial Part 2: functions

Functions are one of the most important concepts in math and programming.


    y = f(x)  # common convention in math to call function inputs x, and outputs y

We can also draw as `x -----f----> y` the function is a map from input values x to an output value y


    def f(x):
        <steps to compute y from x>
        return y


Functions!! Finally we get to the good stuff! The previous two sessions were important
foundations, but now we get to unlocking the first superpower — modelling.
Once you know the basic properties of 10 or so functions,
you can build precise mathematical models for any real-world system.


Functions are all over the place:
- In high school math (the green book) we learn the basic vocabulary of y=f(x) functions
  and their parameters, which allows us to describe any real world process
- In calculus we analyze functions f(x) behaviour over time
  (integral of f = sum of values of f(x) between x=start and x=finish;
  and derivative of f at a = the slope of the graph of f(x) when x=a)
- In linear algebra we study linear transformations, which are functions
  that satisfy f(ax+by)=af(x)+bf(y), meaning a linear combination of inputs
  produces the same linear combination of outputs.
- In probability theory we use functions to describe the probability density of
  a random variables. For example X = Normal(mu, sigma^2) is a random variable
  whose density is described by the function p(x) = K*exp(-((x-mu)/sigma)^2/2)
  in stats we talk about functions computed from samples (estimators)
- In ML we learn about probabilistic models and use them to predict y from given input x


+++

## Python functions

Functions in Python are similar to functions in math: a transformation that takes certain inputs and produces certain outputs. The math functions you're familiar with take numbers as inputs and produce numebrs as outputs, but a Python function can take on any type of input and produce any type of output.

Functions allow us to build chunks of reusable code that we can later reuse in other programs.

We declare a function with the keyword `def`.

```python
def function_name(function inputs):
    """
    doc string that describes what the function does (optional)
    """
    <function body line 1>
    <function body line 2>
    <function body line ...>
    <function body line n-1>
    return <function output value>
```

We enter the name of the function, then define the functions arguments inside parentheses—the names of the variables that the function receives as inputs. Then the function body is written as an indented block of code (all lines start with four spaces indentation). The output of the function is specified using the `return` keyword. The return statement is usually the last line in the function body.

Certain functions do not return a value (we call these _procedures_) and they consist of sequences of commands we want to execute, that don't have any outputs. FunctIons can also be attached to objects, in which case they are called _methods_. We'll talk about these layer on, for now let's focus on simple math-like functions that receive some input and produce output:

### Example 1

A first example of a simple math-like function. The function is called `f`,
takes numbers as inputs, and produces numbers as outputs:

```{code-cell}
def f(x):
    return 2*x + 3

f(10)
```

```{code-cell}

```


### Example 2

```{code-cell}
# Example from Session 1
import random

def flip_coin():
    r = random.random()
    if r < 0.5:
        print("heads")
    else:
        print("tails")

flip_coin()  # no return value, but prints output
```

### Example 3

Write a function `water_phase(temp)` that takes input temperature `temp` in Celcius,
uses if/else statements to find what state water is in (assume pressure is 1atm).
The function returns a string, which is one of "Solid", "Liquid", "Gas".

```{code-cell}
def water_phase(temp):
    """
    Returns phase of water at `temp`.
    Input temp is temperature in Celcius (int or float)
    temp must be greater than −273.15.
    """
    if temp > 0 and temp < 100:
        return 'Liquid'
    elif temp <= 0:
        return 'Solid'
    elif temp >= 100:
        return 'Gas'
```

```{code-cell}
# help(water_phase)
water_phase?
```

```{code-cell}
## tests to try: correct implementation of `water_phase` should return all True
print( water_phase(20.0) == "Liquid" )
print( water_phase(-20.0) == "Solid" )
print( water_phase(200.0) == "Gas" )
print( water_phase(0.0) in ["Liquid", "Solid"] )
```

```{code-cell}
## range tests
results = []

for temp in range(1, 100):
    result = (water_phase(temp) == 'Liquid')
    results.append(result)

# temp <= 0
for temp in range(-100, 1):
    result = (water_phase(temp) == 'Solid')
    results.append(result)

# temp >= 100
for temp in range(100, 5000):
    result = (water_phase(temp) == 'Gas')
    results.append(result)

print('Completed a total of', len(results), 'checks...')
all(results)  # True if all results are True
```

```{code-cell}
# any = OR for a list
# all = AND for a list
all([True, True, False])
```

```{code-cell}

```


## Exercise 2

Write a Python function called `aH_to_pH` that converts aH to pH


```{code-cell}
import math
def ah_to_pH(aH):
    """
    Returns the value of aH convetred to pH.
    """
    if aH <= 0:
        print("Error aH must be a postive number")
        return
    pH = -1*math.log(aH,10)
    return pH
```

Test: if aH=7×10−6  the value of the output should be ...


```{code-cell}
# tests for ah_to_pH
ah_to_pH(1e-7) == 7.0
# ah_to_pH(-11)
```

Write a Python function called `pH_to_aH`  that converts pH to aH


```{code-cell}
# Exercise 3
import math
def ph_to_aH(pH):
  "value of pH converted to aH: "
  aH=10**(-1*pH)
  return aH
```

Test: if pH=7 the value of the expression should match the answer to the second problem in Mission 2


### Exercise 4

```{code-cell}
import random
def roll_die():
  call_die = random.randint(1, 6)
  return call_die
```

```{code-cell}
roll_die()
```

```{code-cell}
for n in range(0,10000):
    if roll_die() not in [1,2,3,4,5,6]:
        print("error")
```


### Exercise 5
Complete the function called `roll_backgammon_dice`
(call roll_die twice; returns a list with two elements,
if roll result is "double six" = [6,6], print additional string "Dü Şeş" on the screen

```{code-cell}
import random
def roll_backgammon_dice():
    first = random.randint(1,6)
    second = random.randint(1,6)
    if first == 6 and second == 6:
        print("Dü Şeş")
    return [first, second]
```

```{code-cell}
for n in range(0,100):
    dice = roll_backgammon_dice()
    if dice[0] not in [1,2,3,4,5,6]:
        print("error")
    if dice[1] not in [1,2,3,4,5,6]:
        print("error")
    
```

Noe: to create a list of two values:
- start with an opening square bracket `[` ,
- then put the first value,
- comma `,`,
- then the second value,
- finally close the square bracket `]`

```{code-cell}
first_val = 3
second_val = 4

my_list = [first_val, second_val]
my_list
```

