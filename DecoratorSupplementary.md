**definition**

_decorator_ 
- A function returning another function, usually applied as a function transformation using the @wrapper syntax. 

## Simple decorator example
Syntatic sugar explanation
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


## Decorator with arguments example

```python
from datetime import datetime

#explain why this works, remove the syntatic sugar!?
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


say_something()
```

## Decorator with arguments and function with arguments
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
def say_something():
    print("Hello world")


say_something()

```
