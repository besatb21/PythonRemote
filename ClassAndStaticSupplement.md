# Methods
## Class methods
A class method receives the class as **implicit first argument**,
just like an instance method receives the instance.

To **declare a class method**, use this idiom:
```python
class C:
  @classmethod
  def f(cls, arg1, arg2, ...):
      ...
```
- possible usage 
  - create alternate class constructor

## Static methods

Transforms a method into a static method.
Unlike a class method, a static method does not receive
an implicit first argument.
To declare a static method:

```
class C:
    @staticmethod
    def f(arg1, arg2, argN): ...
```

A static method can be called outside the class definition:

```python 
C.f()
# called on the class
```
```python 
C().f()
# called on the instance
```


or  **inside the class definition**:
```python
f()
```

Static methods in Python are similar to those in Java or C++.


### Example

```python
class Student():
    def __init__(self, scholarship):
        self.scholarship = scholarship

    def show_finance(self):
        return self.scholarship

    @classmethod
    def create_from_string(cls, inscription):
        if cls.is_scholarship_correct(inscription):
            return cls(inscription)

    @staticmethod
    def is_scholarship_correct(scholarship):
        return int(scholarship) > 0


stud1 = Student(3200)
stud2 = Student.create_from_string("-8")
print(stud1) 
print(stud2) # None
print(Student.is_scholarship_correct("0"))  # invoking static method outside the class definition
```


