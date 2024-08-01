[Generator-iterator methods](https://docs.python.org/3/reference/expressions.html#generator-iterator-methods:~:text=6.2.9.1.-,Generator%2Diterator%20methods,-%C2%B6)


```python
from math import sqrt

def is_prime(n):
    for i in range(2, int(sqrt(n)) + 1):
        if n % i == 0:
            return False
    return True
```

## Generator
```python
def prime_generator(n):
    # Generator to iterate over n prime numbers
    number = 2
    generated_numbers = 0
    while generated_numbers != n:
        if is_prime(number):
            yield number
            generated_numbers += 1
        number += 1

```

## Iterator 
```python

class PrimeIterator:
    # Iterator that iterates over n primes
    def __init__(self, n):
        self.n = n
        self.generated_numbers = 0
        self.number = 1

    def __iter__(self):
        return self

    def __next__(self):
        self.number += 1
        if self.generated_numbers >= self.n:
            raise StopIteration
        elif is_prime(self.number):
            self.generated_numbers += 1
            return self.number
        return self.__next__()


iter = PrimeIterator(1000000)
for elem in iter:
    print(elem)
```