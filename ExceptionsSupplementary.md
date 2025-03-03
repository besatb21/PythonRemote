# Exceptions
## What are exceptions?
Until now error messages haven’t been more than mentioned, but if you have tried out the examples you have probably seen some. 
There are (at least) two distinguishable kinds of errors: syntax errors and exceptions.

## Built-in exceptions
As the name implies, **_built-in exceptions_** are exceptions that are defined in the language, 
meaning not user defined custom exceptions.
The base exception class is **Exception**. All others inherit from it.
In truth, the uppermost class is BaseException but programmers are discouraged inheriting from said class.
Some common built-in exceptions are :
- **AssertionError**
  - This one occurs if the condition given after the keyword _assert_ is false 
- **AttributeError**
  - will occur when we try to reference an attribute or method of an object that does not exist
- **FileNotFoundError**
  - signals an I/O error and occurs when you try to access a file that does not exist
- **IndexError**
  - occurs when trying to access a list item using index that does not exist
```python
lst = range(0, 5)
# 0, 1, 2, 3, 4, 5
# and their complements  meaning  negative numbers
print(lst)
# print(lst[6]) <--error
# print(lst[-6]) <--error
```
- **ImportError**
  - occurs when there is an error with the module import
```python
# from re import doesNotExistInRe
```
- **ModuleNotFound**
  - occurs when we try to import a module that is not installed
```
from interface import implements, Interface
# interface not installed 
```
- **KeyError**
  - occurs when trying to access a dictionary using a key that does not exist
```python
# (key, value) <-- this pair in common when talking about dictionaries

myDict = {'personName': 'Besa', 'personGender': 'female'}

print(myDict['personName']) # valid
print(myDict['personName1']) # should trigger KeyError
```
- **NameError**
  - will show up when we try to use a variable that has not been initialized
```python
x: int # no assigned value meaning un-init.

# x  # -- since there is no type involved explicitly it means that the error will come up earlier
print(x)

# two cases, different error placement

```
- **ValueError**
  - will occur when we pass an argument of the 
```python
a = "Alice has a cat" #string
b = int(a) # integer representation of a literal
print(a, b) 

```
## Handling exceptions
As with every error that is encountered during a program's execution, it should be decided what to 
do next once the error is encountered. In the case of exceptions, we can create handlers to contain the part of code
we wish to execute once the exception has been triggered/raised.

## try, except

First, the try clause is executed.

- **no exception occurs**
  - the except clause is skipped and execution of the try statement is finished
- **an exception occurs**
  - during execution of the try clause, the rest of the clause is skipped
  - if its type **matches the exception** named after the except keyword, the **except clause** is executed, and then execution continues after the try/except block.
- **an exception occurs which does not match** the exception named in the except clause,
it is passed on to outer try statements
  - **if no handler** is found, it is an **_unhandled exception_** and **execution stops** with an error message.

```python
#example
a = 3
b = [1, 0, 2]
for elem in b:
    try:
        result = a / elem
    except ZeroDivisionError:
        continue
    print(f"Result is: {result}")
```

### finally
The **finally** clause is executed regardless of whether the exception occurred or not.

```python
#example
try:
    file = open("temp.txt")
    file.write("Alice has a cat")
except IOError:
    print("An error occurred while processing the file.!")
finally:
    file.close() # an error will occur in the case that the file variable remains uninitialized.
```

In this case, we open the file and write a sentence to it. Thanks to the use of finally, we can be sure that the file has been closed, regardless of whether there was an error.

### Raising exceptions
The raise statement allows the programmer **to force** a specified **exception to occur**.
```python
raise ValueError # syntax 
 ```
It only takes one argument, namely the exception instance or exception class that the programmer intends to.