class: center, bottom


# Python for DevOps

---
# Desclaimer

1. This is not Algorithm 101 - We're not gonna cover all python data types

---
class: top, right, fit-image
layout: false
background-image: url(http://localhost:8000/images/zen_of_python.png)

---

class: left, middle
background-position: bottom;

# Variables

Python is a dynamic language, we don't have to declare types!

```shell
$ python
Python 2.7.13 (default, Dec 18 2016, 07:03:39)
[GCC 4.2.1 Compatible Apple LLVM 8.0.0 (clang-800.0.42.1)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> myvar = 5
>>> type(myvar)
<type 'int'>
>>> myvar = 'foo'
>>> type(myvar)
<type 'str'>

>>> myvar = 'this is nice'
>>> myvar.split(' ')
['this', 'is', 'nice']
```

1. Data type conversion
1. Strings format, `%` `+` `*`
1. Special characters `\n`, `\t` (tripe quotes)


---
# List

Lists are the workhorse of python:

```python
# Basic list
my_list = ['foo', 5, 5.0, True]

# Index Lookup
my_list[0]

# Inserting
my_list.append('New Element')

# Removing components - By index or the last one
my_list.pop(1)

# Removing by value
my_list.remove(5)

# Slicing
my_list[0:1]
my_list[-4:]

# the in operator
'foo' in my_list
```

---

# Control Flow

We have if/elif/else. We don't have semicolons. Everything is handled by identation, and we use ":" to start a block

```python
if expression:
    statement(s)
elif expression:
    statement(s)
elif expression:
    statement(s)
...
else:
    statement(s)
```

Logic Conditions

```python
if x and y:
  statement

if a or b:
  statement
```

---
# Control Flow

Almost Pure English

```python
if something is None:
  statement

if something is not None:
  statement
```

---
# Freaking For Loop ma friend

Most common way to loop:

```python
for item in ['foo', 'bar', 'biz']:
  print(item)

```
Range function:
```python
for i in range(10):
    print(i)
```

Len function might be helpful
```python
mah_list = ['foo', 'bar', 'biz']
for item in range(len(mah_list)):
  print(item)
```

---

# Functions

```python
def foo(arg1, arg2):
  do_something
```

Return is optional, python will `return None` if you miss `return`
```python
>>> def do_nothing():
...   print("foo")
...
>>> val = do_nothing()
foo
>>> val is None
True
```
---
# Functions

You can have optional arguments:
```python
def foo(name, caps=True):
  greeting = "Hello {}".format(name)
  if caps:
    print(greeting.upper())
  else:
    print(greeting)
...
>>> foo('bernardo')
HELLO BERNARDO
>>> foo('bernardo', caps=False)
Hello bernardo
```

Builtin Functions:
```python
len(), abs(), print()
```
---
# Functions

Returning and documentation:

```python
>>> def stupid_sum(a, b):
...   """ This function sum two arguments and return the result """
...   return a + b
...
>>> stupid_sum.__doc__
' This function sum two arguments and return the result '
>>> stupid_sum(1, 1)
2
```

---
# Exercise 01

Create a function called `check_linux_version`:

1. Receive a parameter with kernel information
2. That returns `el5` if the kernel belongs to a Enterprise Linux 5
3. That returns `el6` if the kernel belongs to a Enterprise Linux 6
4. That returns `el7` if the kernel belongs to a Enterprise Linux 7
5. That returns `unkown_version` if the none of the above


---

# Exercise 02

We will write a function similar to the GNU `grep` program.

The function will:

1. Receive two parameters `pattern` and `content`

*pattern* is the string we're looking for

*content* is a string with the file content


The function should return a list with **all lines** that has the given `pattern`

If the pattern wasn't found return an **empty list**

---

# Exception Handling

_Errors should never pass silently._ ~ Zen of Python

```python
  try:
    x = 5 + 'hey'
  except:
    print("you're stupid!")
```
--

#### Pass

_Unless explicitly silenced._ ~ Zen of Python
```python
  try:
    x = 5 + 'hey'
  except:
    pass
```
--

#### Raising Exceptions

```python
  try:
    x = 5 + 'hey'
  except:
    raise MyCustomCoolException("You're stupid!")
```

---
# Exception Handling

Specific errors / Finally

```python
  try:
    x = 5 + 'hey'
  except ZeroDivisionError:
    print("Shall not see")
  finally:
    print("Aloha")
```

---

# I/O

---


# Tuples

Tuple is an ordered sequence of items same as list.The only difference is that tuples are immutable. Tuples once created cannot be modified.

Tuples are used to write-protect data and are usually faster than list as it cannot change dynamically.



---
#Dictionaries

Dictionary is an unordered collection of key-value pairs.

It is generally used when we have a huge amount of data. Dictionaries are optimized for retrieving data. We must know the key to retrieve the value.

---
# Python Modules

When our program grows bigger, it is a good idea to break it into different modules.

A module is a file containing Python definitions and statements. Python modules have a filename and end with the extension .py.

```python
import sys
sys.path

for path in sys.path:
  print(path)
```
