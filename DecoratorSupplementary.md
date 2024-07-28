**definition**

_decorator_ 
- A function returning another function, usually applied as a function transformation using the @wrapper syntax. 

[Current Syntax](https://peps.python.org/pep-0318/#current-syntax)

## Simple decorator example

Syntactic sugar explanation

**Every decorator is a nested function.**
```python
from datetime import datetime


def disable_at_night(func):
    def wrapper():
        if 7 <= datetime.now().hour < 22:
            func()
    return wrapper


@disable_at_night
def say_something():
    print("Hello world")

say_something()
```


### Decorator with arguments example

```python
from datetime import datetime

def run_only_between(from_=7, to_=22):
    def dec(func):
        def wrapper():
            if from_ <= datetime.now().hour < to_:
                func()
        return wrapper
    return dec


@run_only_between(10, 15)
def say_something():
    print("Hello world")
    
# equivalent representation
# (run_only_between(from, to))(say_something)
    
say_something()
```

### Decorator with arguments and function with arguments
```python
from datetime import datetime


def run_only_between(from_=7, to_=22):
    def dec(func):
        def wrapper(*args, **kwargs):
            if from_ <= datetime.now().hour < to_:
                func(*args, **kwargs)
        return wrapper
    return dec


@run_only_between(10, 15)
def say_something(message):
    print(message)

say_something("Hello world")

```
