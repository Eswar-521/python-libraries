## PYTHON GENERATORS:
* Generators are used to create iterators, producing a sequence of values into an iterator.
* Python Generators return an iterator. This is done using the keyword `yield`.
* `yield` is similar to `return`, except that `yield` appends to a list of values for an iterator, 
  and this iterator can be used with `__next__()`.

```python
# GENERATORS
# Function converted to a generator using yield
def GeneratorDemo():
    yield 22
    yield 33
    yield 44
```
# Call the function as an iterator
```python
myIter = GeneratorDemo()
```
# Print the state of the function as an iterator
```python
print(myIter.__next__())
print(myIter.__next__())
print(myIter.__next__())
```

# Using the generator in a loop
```python
myIter = GeneratorDemo()
for c in myIter:
    print(c)
```

# Using yield in a loop inside the function
```python
def GeneratorDemo1():
    for c1 in [1,2,3,4,5]:
        yield c1
```
# Call the function as an iterator
```python
myIter = GeneratorDemo1()
```
# Print the state of the function as an iterator
```python
print(myIter.__next__())
print(myIter.__next__())
print(myIter.__next__())
print(myIter.__next__())

print("-----")
myIter = GeneratorDemo1()
print("Manual __next__() call of Iterator")
print(myIter.__next__())
print(myIter.__next__())
print("Loop Call of Iterator")
for c in myIter:
    print(c)
print("-----")
```
# Create a Dynamic Generator
```python
def EvenOddNum(MAX):
    num = 0
    while num < MAX:
        num += 1
        if num % 2 != 0:
            yield str(num) + " is Odd Number"
        else:
            yield str(num) + " is Even Number"
```
# Call the function as an iterator
```python
myIter = EvenOddNum(5)
```
# Print the state of the function as an iterator
```python
print(myIter.__next__())
print(myIter.__next__())
print(myIter.__next__())
print(myIter.__next__())
print(myIter.__next__())
```
# This will cause an error as MAX is 5 and this is the 6th __next__()
- print(myIter.__next__())















## Iterator with a CLASS

* The CLASS provides `__iter__()` and `__next__()` functions, which create 
  the iterator and get the next value of the iterator.
* This example demonstrates a class with `__iter__()` and `__next__()` functions 
  where a `MAX` value is specified to limit the iterations.
* Until `MAX` is reached, the numbers increment, determining EVEN or ODD 
  starting from `1`.

```python
# Iterator with a CLASS

class EvenOddNumbers:
    
    def __init__(self, max):
        # Instance Variables
        self.max = max
        self.number = 0

    # Override the iterator to return the class instance
    def __iter__(self):
        return self

    # Return the custom __next__ value specified within this function
    def __next__(self):
        # Increment the number once every time __next__() is called
        self.number += 1  

        # Exit when the iterations reach the MAX defined in the constructor
        if self.number > self.max:
            print("Max Number of Iterations reached:", self.max)
        else:
            # Check if the current number is EVEN or ODD and print it
            if self.number % 2 != 0:
                print(str(self.number), "is Odd Number")
            else:
                print(str(self.number), "is Even Number")
```

# Create an object and call the Class with the MAX value to limit iterations
```python
obj = EvenOddNumbers(5)
```
# Call the __next__() method more than the MAX iterations specified (5)
```python
obj.__next__()
obj.__next__()
obj.__next__()
obj.__next__()
obj.__next__()
obj.__next__()
obj.__next__()
obj.__next__()
```









# PYTHON ITERATORS

## Overview

- **Iterators** are looping constructs that can be applied to data containers such as strings, lists, dictionaries, and even **classes** by creating a class iterator.
- The **biggest advantage** of iterators is that there is no boundary; the loop can be closed at any part of the program (or function).
- Iteration is done using the `__next__()` function, which is called once for each iteration.
- Once the values are exhausted, calling `__next__()` will throw an error.

---

## Iterator with `__next__()` Function

```python 
# PYTHON ITERATORS

# Create a List of Data
data_set1 = [1, 2, 3, 4, 5]
```
# Loop or Iterate over this data list using a Loop
# as List is an iterable object
```python
for value1 in data_set1:
    print(value1)
```
# Loop or Iterate over this data list using an Iterator
# Create an iterator using the iter() function

```python
itr = iter(data_set1)
```
# Call the print function to display the next value

```python
print(itr.__next__())
print(itr.__next__())
print(itr.__next__())
print(itr.__next__())
print(itr.__next__())
```
## This will cause an error as there are no more elements left
# print(itr.__next__())

## The biggest advantage is that there is no predefined "end loop".
## Unlike a `for` loop with indentation, we can add more code in between
## the `.__next__()` calls, providing greater flexibility.






