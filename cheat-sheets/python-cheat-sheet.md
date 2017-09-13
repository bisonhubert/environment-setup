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
### Conditions
Use `if`, `elif`, and `else` for control flow and `while` for conditional looping.
#### Comparison Operators
Aside from `==` and `!=`, Python uses `in` and `not in` to check whether a value occurs in a list. It also uses `is` and `not is` to compare whether two objects are the same object (this only matters for mutable objects).
```
>>> 1 != 1
False
>>> 1 == 1
True
>>> my_list = [1, 2, 3, 4, 5]
>>> 1 in my_list
True
>>> 5 not in my_list
False
>>> another_list = my_list
>>> my_list is another_list
True
>>> empty_list = []
>>> another_list is not empty_list
True
```
#### Logical Operators
Python uses `and`, `or`, and `not` written literally to make logical comparisons.
```
>>> a == b and b < c
True
>>> not(a == b) and not(b < c)
False
>>> a == c or b != c
True
```
#### Assign Result of Comparison to Variable
```
>>> string1, string2, string3 = '', 'Trondheim', 'Hammer Dance'
>>> non_null = string1 or string2 or string3
>>> non_null
'Trondheim'
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

## Data Structures
### Lists
#### Built-In Methods
A more comprehensive list of methods can be found [here](https://docs.python.org/3/tutorial/datastructures.html#more-on-lists).
```
>>> fruits = ['orange', 'apple', 'pear', 'banana', 'kiwi', 'apple', 'banana']
>>> fruits.count('apple')
2
>>> fruits.count('tangerine')
0
>>> fruits.index('banana')
3
>>> fruits.index('banana', 4)  # Find next banana starting a position 4
6
>>> fruits.reverse()
>>> fruits
['banana', 'apple', 'kiwi', 'banana', 'pear', 'apple', 'orange']
>>> fruits.append('grape')
>>> fruits
['banana', 'apple', 'kiwi', 'banana', 'pear', 'apple', 'orange', 'grape']
>>> fruits.sort()
>>> fruits
['apple', 'apple', 'banana', 'banana', 'grape', 'kiwi', 'orange', 'pear']
>>> fruits.pop()
'pear'
```
#### Using Lists as Queues w/ `collections.deque`
When you insert or remove from the beginning of a list, all other elements are reordered by index, making lists as queues slow. Instead, use `collections.deque` to implement a queue.
```
>>> from collections import deque
>>> queue = deque(["Eric", "John", "Michael"])
>>> queue.append("Terry")           # Terry arrives
>>> queue.append("Graham")          # Graham arrives
>>> queue.popleft()                 # The first to arrive now leaves
'Eric'
>>> queue.popleft()                 # The second to arrive now leaves
'John'
>>> queue                           # Remaining queue in order of arrival
deque(['Michael', 'Terry', 'Graham'])
```
#### Transposing a List w/ `zip()`
```
>>> list(zip(*matrix))
[(1, 5, 9), (2, 6, 10), (3, 7, 11), (4, 8, 12)]
```
#### Deleting From a List w/ `del`
```
>>> a = [-1, 1, 66.25, 333, 333, 1234.5]
>>> del a[0]
>>> a
[1, 66.25, 333, 333, 1234.5]
>>> del a[2:4]
>>> a
[1, 66.25, 1234.5]
>>> del a[:]
>>> a
[]
>>> del a  # removes the variable entirely
```
### Tuples and Sequences
Tuples are immutable, unless nested with a mutable data structure like a list. They are primarily used when the sequence is heterogeneous.
```
>>> t = 12345, 54321, 'hello!'
>>> t[0]
12345
>>> t
(12345, 54321, 'hello!')
>>> # Tuples may be nested:
... u = t, (1, 2, 3, 4, 5)
>>> u
((12345, 54321, 'hello!'), (1, 2, 3, 4, 5))
>>> # Tuples are immutable:
... t[0] = 88888
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'tuple' object does not support item assignment
>>> # but they can contain mutable objects:
... v = ([1, 2, 3], [3, 2, 1])
>>> v
([1, 2, 3], [3, 2, 1])
```
#### Tuples Containing 0 or 1 Items
```
>>> empty = ()
>>> singleton = 'hello',    # <-- note trailing comma
>>> len(empty)
0
>>> len(singleton)
1
>>> singleton
('hello',)
```
#### Tuple Packing and Sequence Unpacking
```
>>> t = 12345, 54321, 'hello!'  # packs the tuple
>>> t
(12345, 54321, 'hello!')
>>> x, y, z = t  # unpacks the tuple/sequence as multiple variables
>>> x
12345
>>> y
54321
>>> z
'hello!'
>>> t
(12345, 54321, 'hello!')
```
### Sets
A set is an unordered collection of data and does not accept duplicate values. They are useful when testing membership and eliminating duplicate entries.
#### Initializing Sets
```
new_set = set()  # creates an empty set
newer_set = {'b', 'i', 's', 'o', 'n'}  # creates a set of letters
not_a_set = {}  # this creates an empty dictionary
```
#### Demonstrating Sets
```
>>> basket = {'apple', 'orange', 'apple', 'pear', 'orange', 'banana'}
>>> print(basket)                      # show that duplicates have been removed
{'orange', 'banana', 'pear', 'apple'}
>>> 'orange' in basket                 # fast membership testing
True
>>> 'crabgrass' in basket
False
>>> # Demonstrate set operations on unique letters from two words
...
>>> a = set('abracadabra')
>>> b = set('alacazam')
>>> a                                  # unique letters in a
{'a', 'r', 'b', 'c', 'd'}
>>> a - b                              # letters in a but not in b
{'r', 'd', 'b'}
>>> a | b                              # letters in a or b or both
{'a', 'c', 'r', 'd', 'b', 'm', 'z', 'l'}
>>> a & b                              # letters in both a and b
{'a', 'c'}
>>> a ^ b                              # letters in a or b but not both
{'r', 'd', 'b', 'm', 'z', 'l'}
```
### Dictionaries
#### Valid Keys
Any immutable data type can be a valid dictionary key. This includes numbers, strings, and tuples *if* they only contain numbers, strings, or nested tuples.
```
>>> tel = {'jack': 4098, 'sape': 4139}
>>> tel['guido'] = 4127
>>> tel
{'sape': 4139, 'guido': 4127, 'jack': 4098}
>>> tel['jack']
4098
>>> del tel['sape']
>>> tel['irv'] = 4127
>>> tel
{'guido': 4127, 'irv': 4127, 'jack': 4098}
>>> list(tel.keys())
['irv', 'guido', 'jack']
>>> sorted(tel.keys())
['guido', 'irv', 'jack']
>>> 'guido' in tel
True
>>> 'jack' not in tel
False
```
#### Constructing Dictionaries w/ `dict()`
```
>>> dict([('sape', 4139), ('guido', 4127), ('jack', 4098)])
{'sape': 4139, 'jack': 4098, 'guido': 4127}
>>> {x: x**2 for x in (2, 4, 6)}
{2: 4, 4: 16, 6: 36}
>>> dict(sape=4139, guido=4127, jack=4098)
{'sape': 4139, 'jack': 4098, 'guido': 4127}
```
### Techniques for Looping through Sequences
#### Access Key/Value Pair of a Dictionary w/ `items()`
```
>>> knights = {'gallahad': 'the pure', 'robin': 'the brave'}
>>> for k, v in knights.items():
...     print(k, v)
...
gallahad the pure
robin the brave
```
#### Access Position Index of Corresponding Value w/ `enumerate()`
```
>>> for i, v in enumerate(['tic', 'tac', 'toe']):
...     print(i, v)
...
0 tic
1 tac
2 toe
```
#### Looping Over Multiple Sequences at the Same Time w/ `zip()`
```
>>> questions = ['name', 'quest', 'favorite color']
>>> answers = ['lancelot', 'the holy grail', 'blue']
>>> for q, a in zip(questions, answers):
...     print('What is your {0}?  It is {1}.'.format(q, a))
...
What is your name?  It is lancelot.
What is your quest?  It is the holy grail.
What is your favorite color?  It is blue.
```
#### Reverse Looping a Sequence w/ `reversed()`
```
>>> for i in reversed(range(1, 10, 2)):
...     print(i)
...
9
7
5
3
1
```
#### Loop Through a Sorted Sequence w/ `sorted()`
```
>>> basket = ['apple', 'orange', 'apple', 'pear', 'orange', 'banana']
>>> for f in sorted(set(basket)):
...     print(f)
...
apple
banana
orange
pear
```
#### Safely Create a New List Rather Than Modifying the List Itself
```
>>> import math
>>> raw_data = [56.2, float('NaN'), 51.7, 55.3, 52.5, float('NaN'), 47.8]
>>> filtered_data = []
>>> for value in raw_data:
...     if not math.isnan(value):
...         filtered_data.append(value)
...
>>> filtered_data
[56.2, 51.7, 55.3, 52.5, 47.8]
```