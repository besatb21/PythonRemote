# Abstraction
In the domain of **object-oriented programming**, 
the usage patterns for interacting with an object can be divided into two basic categories,
which are:
- invocation
- inspection

**Invocation** means **_interacting with an object by invoking its methods_**.
Usually this is combined with polymorphism, so that invoking a given method may run different code depending on the type of an object.

**Inspection** means the ability for external code (outside of the object’s methods) 
**_to examine the type or properties of that object_**, 
and make decisions on how to treat that object based on that information.

Both usage patterns serve the same general end, 
which is **to be able to support the processing** of diverse and potentially novel objects in a **uniform way**,
but at the same time **allowing processing decisions to be customized** for each **different type of object**.
[Rationale behind abstract classes](https://peps.python.org/pep-3119/)
## Abstract classes
Distinction between using interfaces ?
### abc module

abc &rarr; module for defining abstract base classes in python  
### EXAMPLE
```
from abc import ABC, abstractmethod
from math import pi

class Figure(ABC):
    @abstractmethod
    def circuit(self):
        pass

    @abstractmethod
    def area(self):
        pass
```

```
class Rectangle(Figure):
    def __init__(self, a, b):
        self.a = a
        self.b = b

    def circuit(self):
        return 2 * (self.a + self.b)

    def area(self):
        return self.a * self.b


class Circle(Figure):
    def __init__(self, r):
        self.r = r

    def circuit(self):
        return 2 * self.r * pi

    def area(self):
        return pi * self.r ** 2
```