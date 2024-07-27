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
class Student(Person):
    def __init__(self, name, age, scholarship):
        Person.__init__(self, name, age)
        self.scholarship = scholarship

    def show_finance(self):
        return self.scholarship

    @classmethod
    def create_from_string(cls, inscription):
        name, age, scholarship = inscription.split()
        age, scholarship = int(age), float(scholarship)
        if cls.is_name_correct(name):
            return cls(name, age, scholarship)

    @staticmethod
    def is_name_correct(name):
        if name[0].isupper() and len(name) > 3:
            return True
        return False


stud1 = Student("Margaret", 32, 0)
stud2 = Student.create_from_string("Mark 21 600")
print(stud1)
print(stud2)
print(Student.is_name_correct("alice"))
```


