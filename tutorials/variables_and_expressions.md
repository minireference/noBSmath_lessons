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

# Variables and expressions

This notebook contains some exercises to get you familiar with basic Python programming notions.


## Programming 101

Programming consists of writing down instructions for a computer. The instuctions are also called "commands", "code", "source code", etc. Since this tutorial is about Python, all the instructions in the boxes you'll see below are written in the Python programming language. 

You can "run" the code in a given box by pressing the play button on the left side, or by pressing _Shift_ and _Enter_ keys at the same time. When you run a code cell, you're telling the computer to "execute" the Python instructions in that cell, which means to do the actions described in the code, and print the final value computed in that cell.

Running a code cell is similar to using the EQUALS button on the calculator: whatever math expression you entered, the calculator will compute its value and display it as the output. The process is identical when you execute some Python code, but you're allowed to input multiple lines of commands at once. The computer will execute the lines of code one by one in the order it sees them.

The result of final calculations in the cell gets automatically printed in the output cell right below the input cell. This feature allows you to skip the print statments, since the last output gets printed automatically for you. This makes it easy and fun to explore and "poke around" each example given in this notebook. Click the `[+ Code]` button below any cell to add a blank cell where you can try inputting some expressions and running them by pressing _Shift_ and _Enter_.



### Errors
Sometimes the executed commands will cause an error, and in these cases Python will give an error message describing the problem encountered. Get psychologically ready for those, because they can be very discouraging. REJECTED! The computer doesn't like what you entered. SyntaxError, ValueError, etc. The error messages look scary, but really they are there to help you—if you read what the error message tells you, you will know what needs to be fixed in your input. The error message literally describes the problem!



```{code-cell}
x = 3
print(x)
```
No problem with this cell (it just sets the variable `x` to the value `3`, then prints the value of x to the screen).

```{code-cell}
3/0
```
Here we get an error since we're trying to compute an expression that contains a divide by zero error: Python tell us a `ZeroDivisionError: division by zero` has occurred, i.e., check your math expressions!


## Variables

Similar to variables in math, a variable in Python is a convenient name we use to refer to any value: a onstant `c`, the input to a funciton `x`, the output of a function `y`, or any other intermediate value.


### Variables types

Similar to the notion of number sets in math $\mathbb{Z}$, $\mathbb{R}$ etc., computers variables also come in different types:

- **int** - integers ex: `34`,`65`, `78`, `-4`, etc. (rougly equivalent to $\mathbb{Z}$)
- **float** - ex: `4.6`,`78.5`, `1e-3` (full name is "floating point number"; similar to $\mathbb{R}$ but only with finite precision)
- **bool** a Boolean truth value with only two choices: `True` or `False`.
- **string** - text ex: `'Hello'`, `'Hello everyone'`
- **list** a sequence of values ​​- ex: `[69, 81, 92, 77]`. The beginning and the end of the list are denoted by the brackets `[` and `]`, and its elements are separated by commas.
- **dictionary** a collection of key-value pairs. Each key is associated with a value - ex: `{'first_name': 'Julie', 'last_name': 'Tremblay', 'score': 98}`. Dictionaries are denoted by curly braces `{` and `}` inside which we place `'key': value`, pairs separated by commas.
- **tuples**, **sets**, **functions**, etc. = there are seveal other interesting and useful Python building blocks, which we'll talk about in the next episode.

To assign a value to a variable, you use the symbol `=` as follows, from left to right:

* we start by writing the name of the variable
* then, we add the symbol `=`
* finally, we write the value of the variable

For example, here is how we define six variables: an integer, a decimal number, a Boolean value, a string, a list, and a dictionary:

```{code-cell}
score = 98
average = 77.5
above_the_average = True
message = 'Bonjour tout le monde'
scores = [61, 85, 92, 72]
profile = {'first_name':'Julie', 'last_name':'Tremblay', 'score':98}
```

```{code-cell}
len(scores)
```

```{code-cell}
# title-case = capitaliz the first letter of every word
message.title()
```


```{code-cell}
len(profile)
```

```{code-cell}
other_scores = [77.5, 7.75e1]
len(other_scores)
```

```{code-cell}
len(message)
```

```{code-cell}
message.split()
```

You can explore the different methods available on any python object `int`, `float`, `str`, etc.  by starting to type the dot `.` after the name, e.g., `message.` then pressing the TAB button to get an "autocomplete" dropdown of all the methods available on the variable `message`. Most of these methods are common to all strings in Python.


## Expressions

Similar to expresisons in algebra, a Python expression is can be any combination of variables and operations:


```{code-cell}
# Expression involving numerical values
sec_in_min = 60 
sec_in_day = sec_in_min * 60 * 24
sec_in_week = sec_in_day * 7
print('The number of seconds in a week is', sec_in_week)


# Expression involving strings
name = 'Julie'
message = 'Hello ' + name    # for strings, + means concatenate
print(message)

# Expression involving a list
scores = [61, 85, 92, 72]
average = sum(scores)/len(scores)
#        `sum` computes the sum of values in the list
#                and `len` gives you the length of the list
print('The average score is', average)


# Expression involving using the values of a dictionary
profile = {
    'first_name':'Julie',
    'last_name':'Tremblay',
    'score':98
}
message2 = 'Hello ' + profile['first_name'] + ' ' + profile['last_name'] + \
           ', your score is ' + str(profile['score']) + '%.'
print(message2)
```

```{code-cell}
profile['last_name'] 
```

Note in all the above examples, the code had the form:

```Python
var_name = <some expression>
```
which is the important new pattern you have to get used to in programming. Even though this looks like a math equation, the meaning you have to associate with it is much simpler—we are setting variable `var_name` to the value of the expression `<some expression>`.

Don't worry about the lists and dictionary examples—I know they are complicated and we haven't explained all the syntax. We'll get to that in just a little bit. First let's practice computing some Python expresions.

```{code-cell}
# Numeric expressions

expr1 = 1 + 2.4
print(expr1)  # 3.4

expr2 = 4 - 6
print(expr2)  # -2

expr3 = 0.5 * 3
print(expr3)  # 1.5

# expr4 = 5 / 0 
# print(expr4)  
```

```{code-cell}

```

```{code-cell}
expr4=5/0
```

### Integration problem

What is the pH of a solution with hydrogen ion activity, aH+ = 7×10−6  (the number of moles of hydrogen ions per litre of solution).   (see [pH definition](https://en.wikipedia.org/wiki/PH#Definition_and_measurement) on Wikipedia)


Write a Python expression that computes the pH given variable aH

   pH = some expression involving the variable aH

Test: if aH=7×10−6  the value of the expression should match the answer to the first problem



```{code-cell}
import math
aH = 1e-7
pH_value = -1*math.log(aH,10)
print('The pH value is', pH_value)
```

What is the hydrogen ion activity, aH+, in liquid with pH=7.47 (water at 0°C),  pH=7.00 (water at 25°C), and pH=6.14 (water at 100°C)? 

Write a Python expression that computes the aH given variable pH 

   aH =  some expression involving the variable pH



```{code-cell}
pH = 7
aH = 10**(-(pH))
print('When pH = 7, the molar concentration is', molar_conc_of_H)
```
Test: if pH=7  ... 


### String expressions

```{code-cell}
message3 = 'Hello' + ' ' + 'world'  # + means concatenate
print(message3)

message4 = 'Ai ' * 3                # * means repeat
print(message4 + 'Caramba!') 
```

```{code-cell}
message5= 'Hello'+' ''Tijana'+ ' and Bojana'
print(message5)
```

```{code-cell}
# Define a string of length 26 that contains all the lowercase latin letters
letters = 'abcdefghijklmnopqrstuvwxyz'

# Accessing individual characters within a string
print('The index of the letter "a" in the string letters is 0')
first_letter = letters[0]  # 'a'
print(first_letter)

print('The index of the letter "b" in the string letters is 1')
second_letter = letters[1]  # 'b'
print(second_letter)

print('The index of the last letter in the string letters is -1')
last_letter = letters[-1]  # 'z'
print(last_letter)

print('The last character in a string of length 26 corresponds to index 25')
print(last_letter == letters[25])

print('\n\n\n')  # '\n' is a special character (an escape sequence) that prints a newline
                 # we'll use this kind of preint-nelines statements to logically
                 # separate the out outplut lines

# Slicing = getting a substring that contains a range of values
first_four = letters[0:4]
print('The first four letters of the alphabet are:', first_four)
# the notation 0:4 is sugar syntax for range(0,4) which is equal to [0, 1, 2, 3]

```


```{code-cell}
print(letters)
letters[4:12]
```

```{code-cell}
scores[0:2]
```

### Boolean expressions

You can use `bool` variables and the logical operations `and`, `or`, `not`, etc. to build more complicated boolean expressions (disjunctions, conjunctions, negations, etc.).


```{code-cell}
print('not True ==', not True)
print('not False ==', not False)
print('True and True ==', True and True)
print('True and False ==', True and False)
print('True or False ==', True or False)
print('False or False ==', False or False)
```



## Types and type conversions

The function `type` tells you the type of any variable, meaning what kind of number or object it is.
Look back to the list above—the Python types are shown in **bold**.


```{code-cell}
# integrers
score = 98
type(score)
```

```{code-cell}
average = 77.5
type(average)
```

```{code-cell}
above_the_average = True
type(above_the_average)
```

You can convert between each of these types using the function which has the same name as the type of an object

- `int` : transform any expression into an int
- `float`: transform any expression into a flaot
- `bool`: transform any expression into a `True` or `False`
- `str`: transform an expression to it's string representaiton (i.e. this is what the function `print` does).

+++

### Useful anything-to-int conversions

```{code-cell}


# str --> int
number_as_str = '65'
print(number_as_str, 'has type', type(number_as_str))
number = int(number_as_str)
print(number, 'has type', type(number))

#  float --> int
precise_number_as_float = 3.2
print(precise_number_as_float, 'has type', type(precise_number_as_float))
rounded_number = int(precise_number_as_float)
print(rounded_number, 'has type', type(rounded_number))

#  bool --> int
true_value = True
false_value = False
print('When converted to an int, True is', int(True), 'and False is', int(False))
```

### Useful anything-to-float conversions

```{code-cell}
# str --> float
print(float('1.2'))  # note using decimal dot . not decimal , as in Europe
print(float('1e6'))  # one million = 1000000 = 1x10^6. The e is shorthand for x10^
print(float('4'))

# int/int --> float autoconversion
print('If you divide an integrer by an integer in Python using the / operator...')
print('...you get a float number', 6/5, 'has type', type(6/5))

print('There is also an divistion without autoconversion operator // which ...')
print('...you get an integer', 6//5, 'has type', type(6//5))
```

### Common anything-to-str conversions

```{code-cell}
# use the str function
str1 = str(42)
str2 = str(4.2)
str3 = str(True)
str4 = 'a string'
print('string representations', str1, str2, str3, str4)

# float -> str
import math
pi = math.pi  # constant equal to ratio of circumference to diameter of a circle
print('str(math.pi) =', str(math.pi))  # defaults to max precision

# control precision and print formatting using format. For more info, see
# https://python-reference.readthedocs.io/en/latest/docs/functions/format.html
print('pi to two decimals', '{:.2f}'.format(pi))
print('pi to seven decimals', '{:.7f}'.format(pi))
```

```{code-cell}

```

```{code-cell}

```

### Converting expressions to boolean values

Up until now we were in the land of math and text manipulation of numbers, which all make sense intuitively. 

Next we'll talk about the boolean values of Python expressions. This will feel a little weird at first since we're forcing some arbitray Python object (could be a number, a string, a list, a dictionary, etc) and asking the questions is the value `True` or `False` ?

There is a specific convention about which values are considered "truthy" (i.e. get converted to `True` when converted to boolean using `bool`) and which expressions are falsy (i.e. get converted to `False` when passed through `bool`). 

I know this seems like boring details, but please read the next example carefully because "truthyness" and "falsyness" will play a big role in coding: every time you use an if or elif statement in Python, we are implicitly calling `bool` on an expression so it's a good idea to get to know what `bool` does to different types of variables.

```{code-cell}
# int --> bool
print('Any non-zero integer is considered as True')
print(bool(1), bool(-2), bool(10000))
print('Zero is False')
print(bool(0), bool(-0), bool(int('0')))

print('\n')

# float --> bool
print('Any non-zero float is considered as True')
print(bool(1.0), bool(-2.0), bool(10000.0))
print('Zero is False')
print(bool(0.0), bool(-0.0), bool(float('0.0')))


# str --> bool
print('Any non-empty string is considered True')
print(bool('as'), bool(''))

print('\n')

# list --> bool
print('Any non-empty list is considered True')
print(bool([1]), bool([1,2]), bool(range(0,10000)))
print('Empty list is considered False')
print(bool([]), bool(list()), bool(list('[]')))

print('\n')

# dict --> bool
print('Any non-empty dict is considered True')
print(bool({1:11}), bool({1:11,-2:22}))
print('Empty dict is considered False')
print(bool({}), bool(dict()))
```

```{code-cell}
bool(2)
```

## Your turn to try this...

Try typing in some Python code in this cell. If you've been simply reading until now, this is your chance to switch to "active" mode: use the rocket-button in the top right of the menu at the top, and choose the `Live Code` option to make all the cells in this notebook interactive, then try entering some Python commands in this code cell below:

```{code-cell}

```


## Coming up

In the next few sections, we'll cover other important parts of Python:

- Blocks of code that contain multiple expressions (these are indicated based on the text indentation of the code instructions)
- Functions
- For loops
- If, elif, else conditional statements
- etc., see full list of **Appendix C: Python coding** planned topics [here](https://docs.google.com/document/d/1fwep23-95U-w1QMPU31nOvUnUXE2X3s_Dbk5JuLlKAY/edit#bookmark=id.zghgol749kju)



## Exercises

- Review Python syntax cheatsheet [https://blog.finxter.com/wp-content/uploads/2020/07/Finxter_WorldsMostDensePythonCheatSheet.pdf](https://blog.finxter.com/wp-content/uploads/2020/07/Finxter_WorldsMostDensePythonCheatSheet.pdf)
  - add single dot next to concepts you've hear about
  - double dot next to python concepts you understand
  - triple dot next to concepts you've used in your code
- Try poking-around and explore expressions involving numbers (`int` and `float`),
  strings (`str`), and booleans (`bool`).
- Go through all quiz questions in reading material as notebooks:
  - 03-Variables: [https://introductorypython.github.io/tutorials/03-Variables.html](https://introductorypython.github.io/tutorials/03-Variables.html)
  - 04-Operarators: [https://introductorypython.github.io/tutorials/04-Operators.html](https://introductorypython.github.io/tutorials/04-Operators.html)
  - 06-Data types: [https://introductorypython.github.io/tutorials/06-DataTypes.html](https://introductorypython.github.io/tutorials/06-DataTypes.html)
- Print out the [SymPy tutorial](https://minireference.com/static/tutorials/sympy_tutorial.pdf)
  and read the beginning, which is an intro to Python from a math perspective.
  Alt version [here](https://minireference.com/static/excerpts/noBSmath_v5_preview.pdf#page=77).

