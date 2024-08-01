
### syntax

**lambda** keyword followed by :

- a comma-separated list of arguments
- a colon
- a single expression that returns the value of the function.


```python 
lambda x : x # this line does not transform the input, it simply returns it as is for the sake of the example
``` 

```python
lowercase = lambda x: x.lower()

# equivalent representation
def lowercase(x):
    return x.lower()
```

```python
square = lambda x: x * x

for el in range(1, 5):
    print(square(el))

```

```python
equals_lambda = lambda x, y: x == y
```
