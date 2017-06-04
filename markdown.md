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
# Language Features

1. Dinamic language
1. No semicolons, identation!
1. We love whitespaces
1. snake_case not camelCase. Please don't write camelCase!!!
1. Functions are first class citizen


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

???
1. Multiline statement with `+ \`
1. Multi assignment same line with semicolon
1. Multiple variable assginment `a,b,c = foo, capa, foo`
1. Multiple variable assignment same `x=y=z=foo` (This is not pointers!!!)
1. Data type conversion `float(5)`
1. Strings format, `%` `+` `*` https://docs.python.org/2/library/stdtypes.html#string-formatting-operations
1. Special characters `\n`, `\t` (tripe quotes)
1. Comments with `#`

---

# Operators



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

# Tuples

Tuple is an ordered sequence of items same as list.The only difference is that tuples are immutable. Tuples once created cannot be modified.

Tuples are used to write-protect data and are usually faster than list as it cannot change dynamically.



---
#Dictionaries

Dictionary is an unordered collection of key-value pairs.

It is generally used when we have a huge amount of data. Dictionaries are optimized for retrieving data. We must know the key to retrieve the value.

an be marshall/unmarshall to JSON

```python
>>> foo = {}
```

???
1. Create a dict from cmd. Show how to access the value
1. Insert/Update key
1. Looping over a dict
1. Find if key exists with `in` and `has_key`
1. Method `keys`/`iterkets`, `values`
1. Show `iteritems` method
1. `del dict[key]`
1. `dict.get(key, default)`

---
# Exercices

1. Given a string return a dict where letters from the string are keys and the value are the count of it in the string.

Example: banana
```
{'b': 1, 'a': 3, 'n': 2}
```

#Set

A set object is an unordered collection of distinct hashable objects. Common uses include membership testing, removing duplicates from a sequence, and computing mathematical operations such as intersection, union, difference, and symmetric difference. (For other containers see the built in dict, list, and tuple classes, and the collections module.)

---

# Python Modules

A module is a file containing Python definitions and statements. The file name is the module name with the suffix .py appended. Within a module, the module’s name (as a string) is available as the value of the global variable __name__. For instance, use your favorite text editor to create a file called fibo.py in the current directory with the following contents:

```python
_MAGIC_VAR="HELLO"

def fib(n):    # write Fibonacci series up to n
    a, b = 0, 1
    while b < n:
        print b,
        a, b = b, a+b

def fib2(n):   # return Fibonacci series up to n
    result = []
    a, b = 0, 1
    while b < n:
        result.append(b)
        a, b = b, a+b
    return result

```

???
1. Show how to import the code `import fib`
1. Show method `dir()` that shows what was imported
1. Show how to import only fib.
1. Add some code to fibo.py to show that it will be executed
1. import * to show that global `_MAGIC_VAR` won't get imported

---
# Modules

How do we execute `fibo` and also make the functions available to other scripts
without executing when `fibo` is imported?

--

```python
if __name__ == "__main__":
    import sys
    fib(int(sys.argv[1]))
```

???
1. First special variable `__name__`
1. Explain that imports can come in any part of the code we want. That's not antipattern


```python
import sys
sys.path

for path in sys.path:
  print(path)
```

---

# Module Search Path

When a module named `fibo` is imported, the interpreter first searches for a built-in module with that name. 

If not found, it then searches for a file named fibo.py in a list of directories given by the variable `sys.path`. sys.path is initialized from these locations:

1. The directory containing the input script (or the current directory).
1. `PYTHONPATH` (a list of directory names, with the same syntax as the shell variable PATH).
1. The installation-dependent default


---
# Python Packages

Packages are a way of structuring Python’s module namespace by using `dotted module names`. 

--

For example, the module name sys.path designates a submodule named `path` in a package named `sys`. 

---

# Python Packages

A package is a directoy containing an `__init__py` file.

The `__init__.py` files are required to make Python treat the directories as containing packages.

```
sound/                          Top-level package
      __init__.py               Initialize the sound package
      formats/                  Subpackage for file format conversions
              __init__.py
              wavread.py
              wavwrite.py
              aiffread.py
              aiffwrite.py
              auread.py
              auwrite.py
              ...
      effects/                  Subpackage for sound effects
              __init__.py
              echo.py
              surround.py
              reverse.py
              ...
      filters/                  Subpackage for filters
              __init__.py
              equalizer.py
              vocoder.py
              karaoke.py
```


---

# I/O

Handling Files

```python
f = open("test.txt", 'r')
f.read()
f.close()
```

???
1. read, than readlines than readline
1. line loop, print with `end=''`
1. try,finally
1. `with` context manager
1. Show the `seek` example to read the content again
Show the old way py26 than the new way

--

Writing
```python
with open("test.txt", mode='w') as writer:
  writer.write("my content\n")
  writer.write("this is nice\n")
```

???
1. Writing file
1. Append a file

---

# Exercise xx

Write a grep script, for real this time! Use your grep engine (Exercise 02) to save some time.

The file name should be exact: **grep.py**

The script should receive two arguments. First, the **search pattern**, Second the **file path**.

The script should exit with **returncode 1** and return a message if: 

  1. Both arguments were not provided. Print message: **Two arguments are required, pattern and file path.**
  1. The file doesn't exists. Print message: **File *filename* doesn't exists**

The script should return:
  1. The same way as GNU grep, return **each match in a new line**.
  1. Nothing if no lines matches

Remember the pythonic way is **ask for forgiveness not permission!**

BONUS: Replace GNU grep with your new script using a shell alias: `alias grep="/path/to/grep.py"`

---

# Regular Expression

Regular expressions are handled by module `import re`

Most methods follows the same structure:

1. Pattern
2. String
3. Flags

--

### FINDALL

Return a list with all matches

```python
import re
re.findall(r'\d+', "Bernardo has 25 years old and he's a "
"DevOps Engineer at AvenueCode")
```

???

Findall
`\d` = any digit
+ = One or more occurance

---

# Regular Expression

Compiling a regular expression

```python
regex = re.compile('http\://|https://')
regex.match("https://avenuecode.com")
```

???
Demonstrate re.match() = Return match object or None

--
Searching for a pattern

```python
print(re.match(r'avenuecode', "https://avenuecode.com"))
print(re.search(r'avenuecode', "https://avenuecode.com"))

```
???
.group() to return the matched string

--

Find all occurences

```python
test = """
https://avenuecode.com
https://avenuecode.com.br
https://acdc.avenuecode.com
https://jenkins.avenuecode.com"""
print(re.search(r'avenuecode', "https://avenuecode.com"))
print(re.findAll(r'avenuecode', "https://avenuecode.com"))
```

---
# Regular Expression

Replacing stuff!

```python
re.sub(r'avenuecode', 'ac4success', "https://avenuecode.com")
```

-- 
Grouping

```python
regex = re.match(r'(http|https)\://(\w*).(\w.*)', "https://jenkins.avenuecode.com", flags=re.MULTILINE)
regex.group(1))
```

---

# Interacting with Underlying OS

```python
import os
```

Interacting with the File System


Getting file information
???
os.getcwd()
os.listdir()
os.stat(file) // 
os.makedirs('foo/bar')
os.listdir() // or give path

# Modification time example
mod_time = os.stat('.gitignore').st_mtime
print(datetime.datetime.fromtimestamp(mod_time))

---

# OS

Environment Variables
```python
os.environ

os.getenv('PATH')
```
--

Creating a file at home. How can we do that?


???
Example: LOGNAME to collect username

print(os.path.join(os.getenv('HOME'), 'foo.txt'))
print(os.path.expanduser("~/foo.txt"))

Get file
os.path.exists()

Remove it
os.remove()

File path manipulation
os.path.basename -- filename
os.path.dirname -- directory
os.path.split -- split file/path
os.path.splitext(f) -- split file and extension

os.uname()

os.system -- calls os, but let's work on subprocess
---

# SHUTIL

```python
import shutil
```

???
1. Create a file
1. shutil.copy to /tmp
1. shutil.move to user home
1. Create a bunch of temp files
1. Use shutil.copytree
1. Remove it using shutil.rmtree
1. Create a backup using shutil.make_archive

```python
shutil.make_archive('backup', format='zip', root_dir='/Users/bvale/projects/python-devops/exercise01')
```

---

# Exercises

1. Write a script that compress files older than 7 days from a given folder

```shell
./script /tmp/backup
```

2. Write a second script that removes all files from a folder that has an specific extension:

```shell
./script2 /tmp/files bkp
```

---

# Subprocess :)

The subprocess module allows you to spawn new processes, connect to their input/output/error pipes, and obtain their return codes. This module intends to replace several older modules and functions:

```
os.system
os.spawn*
os.popen*
popen2.*
commands.*
```

PEP 324 – PEP proposing the subprocess module

--

Let's give it a try :)

```python
subprocess.call(cmd)
```

???
`subprocess.call(cmd)` wait for cmd exec and return resultcode

1. Explain result code
1. Explain list of commands
1. Explain shell=True with exit and ls and the threats with `;` plus rm -rf --no-preserve-root
1. Explain stdout with a file

---
# Subprocess :)

What if we don't wanna write a logic to identify errors ?

--


```
subprocess.check_output(cmd)
```

???
1. Show the exceptions and the output

---
#Subprocess

Complex cases. Popen!

https://docs.python.org/2/library/subprocess.html#popen-constructor

???
Explain why popen is usefull, e.g: cwd, env, rc, stdout, stderr

Open process and explain the lifecycle `child = subprocess.Popen(["jconsole"])`
1. child.poll()
1. child.kill()

1. Open a shell with child = subprocess.Popen("/bin/bash", stdin=subprocess.PIPE, stdout=subprocess.PIPE)
and use communicate to send data

---
# Exercice Time

Write a script to deploy a static website.

1. Install nginx or apache
1. Push your html to nginx home/apache home
1. Reload the web server if you need

To test it use Vagrant or Docker

For docker, run a centos:7 with this command:

```
docker run -it --rm -v $(pwd)/deploy.py:/tmp/deploy.py -p 81:80 centos:7

python /tmp/deploy.py
```

---

# Classes

---


# Sys

```python
import sys
```