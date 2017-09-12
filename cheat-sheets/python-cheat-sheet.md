## Data Types
* Numbers `1` or `1.0` **(immutable)**
* String `'Hello world!'` or `"Hello?"` **(immutable)**
* List `[1, 2, 3, 4]` **(mutable)**
* Set `{1, 2, 4, 5}` **(mutable)**
* Tuple `([1, 2], [3, 4], "Tuple")` **(immutable)**
* Dictionary `{'name': 'Bison', 'age': 29}` **(mutable)**

### List vs Set
* Sets are unordered, rendering indexing and slicing useless
* Adding `add()` and updating `update()` a set is how new values are added
* In all cases with Sets, duplicates are avoided

### List vs Tuple
Lists and Tuples are similar but have different use cases. Mutability is one condition that separates the two. Their syntax is also different, with lists being wrapped in brackets and tuples being wrapped in parentheses.
* Tuples are generally used for heterogeneous data types, while lists are used for homogenous data types.
* Iterating through a tuple is faster than a list
* Both tuples and lists can be concatenated
* Nested mutable elements in a tuple can be changed
```
>>> my_tuple = (4, 2, 3, [5, 9])
>>> my_tuple[0]
4
>>> my_tuple[0] = 1  # attempt to mutate an immutable tuple element
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'tuple' object does not support item assignment
>>> my_tuple[-1]
[5, 9]
>>> my_tuple[-1][0] = 0  # attempt to mutate a mutible tuple element
>>> my_tuple[-1]
[0, 9]
```

## Variables
* Must start with a letter `cats` or underscore `_dogs`
* Remainder of characters can be letter, number, or underscore
* Space separated by underscore
* Variables are case sensitive: `nachos` vs `Nachos` vs `NACHOS` are all different variables

### Multi-Value Assignment
```
>>> a, b = 0, 1
>>> a
0
>>> b
1
```

## Lists
### Appending w/ `append()`
```
>>> cubes.append(216)  # add the cube of 6
>>> cubes.append(7 ** 3)  # and the cube of 7
>>> cubes
[1, 8, 27, 64, 125, 216, 343]
```

### Slicing w/ `[:]`
```
>>> letters = ['a', 'b', 'c', 'd', 'e', 'f', 'g']
>>> letters
['a', 'b', 'c', 'd', 'e', 'f', 'g']
>>> # replace some values
>>> letters[2:5] = ['C', 'D', 'E']
>>> letters
['a', 'b', 'C', 'D', 'E', 'f', 'g']
>>> # now remove them
>>> letters[2:5] = []
>>> letters
['a', 'b', 'f', 'g']
>>> # clear the list by replacing all the elements with an empty list
>>> letters[:] = []
>>> letters
[]
```

### Length w/ `len()`
```
>>> letters = ['a', 'b', 'c', 'd']
>>> len(letters)
4
```

## Indentation with New Scope Declaration
```
>>> # Fibonacci series:
... # the sum of two elements defines the next
>>> def fibonacci(n):
>>>   a, b = 0, 1
>>>   while a < n:
...     print(a, end=' ')
...     a, b = b, a+b
...
>>> fibonacci(0, 1)
1
1
2
3
5
8
```

## Conditional Flow w/ `if`
```
>>> x = int(input("Please enter an integer: "))
Please enter an integer: 42
>>> if x < 0:
...     x = 0
...     print('Negative changed to zero')
... elif x == 0:
...     print('Zero')
... elif x == 1:
...     print('Single')
... else:
...     print('More')
```

## Iteration
### Iterate Through Strings and Lists w/ `for`
```
>>> # Measure some strings:
... words = ['cat', 'window', 'defenestrate']
>>> for w in words:
...     print(w, len(w))
...
cat 3
window 6
defenestrate 12
```

### Iterate Over a Sequence w/ `range(n)`
```
>>> for i in range(5):
...     print(i)
...
0
1
2
3
4
```

### Iterate Over Indices of a Sequence w/ `len()` and `range(n)`
```
>>> for n in range(len(l)): # similar to Ruby's `#each_with_index`
...     print(n, l[n])
...
0 1
1 2
2 3
3 4
4 5
```

### Iterate w/ `else` Clause
```
>>> for n in range(2, 10):
...     for x in range(2, n):
...         if n % x == 0:
...             print(n, 'equals', x, '*', n//x)
...             break
...     else:
...         # loop fell through without finding a factor
...         print(n, 'is a prime number')
...
2 is a prime number
3 is a prime number
4 equals 2 * 2
5 is a prime number
6 equals 2 * 3
7 is a prime number
8 equals 2 * 4
9 equals 3 * 3
```

### Jump to Next Iteration of Loop w/ `continue`
```
>>> for num in range(2, 10):
...     if num % 2 == 0:
...         print("Found an even number", num)
...         continue  # similar to Ruby's `next`
...     print("Found a number", num)
Found an even number 2
Found a number 3
Found an even number 4
Found a number 5
Found an even number 6
Found a number 7
Found an even number 8
Found a number 9
```