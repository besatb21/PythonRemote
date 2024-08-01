[Regex online editor](https://regex101.com/)

- let's think of when we use range(0,5) = short way of writing [0,1,2,3,4]  the same thing is valid for **range of
  characters**
    - instead of writing [ABCDEFGHIJKLM....Z]  we can write [A-Z]


- parentheses ()

- (az)+ <-- I want these two letters to appear side by side for at least one time
  and at most "infinity"

- (a-z){1, 3}
- caret ^ when used inside [square brackets] it means negation
- some other use of caret
  -> signify the **start of a line/string**

```python
import re

print(re.search(r"[A-Z]la", "ala Ola Ela"))
print(re.match(r"[A-Z]la", "ala Ola Ela"))

print(re.fullmatch(r"[A-Z]la", "Ela sdsd"))
print(re.findall(r".la", "Ola ala Ela #la 1la"))

iter = re.finditer(r".la", "Ola ala Ela")
for elem in iter:
    print(elem)

print(next(iter))
print(next(iter))

print(re.split(r",|\.", "apple,pear,grapes,carrot.cabbage,veggies.fruit,yard"))

print(re.sub(r"cat", "dog", "Alice has a cat"))
text = "Thomas (33 l.) and Eva (24 l.) agreed to go shopping together tomorrow"
pattern = r"([A-Z]{1}[a-z]+) \((\d+) l\.\)"
print(re.findall(pattern, text))
```