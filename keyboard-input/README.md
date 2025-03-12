# Reading User Input in Python

## Overview
- This script reads user input from the command line.
- It uses the `input()` function to take a single-line input.
- The entered text is then displayed as output.

---

## Python Code

### This is required to read Python file command line arguments
### import sys

### Reading single-line user input using "input"
```python
l_UserInput = input("Enter text and press enter: ")
print("Text entered: " + l_UserInput)
```





# Multi-line User Input in Python

## Overview
- This script allows the user to enter multiple lines of input.
- The input is terminated when the user enters `:END`.
- All entered lines are stored and printed at the end.

---

## Python Code

```python
data = ""
terminate_str = ":END"  # Termination String ':END'

print("Enter multiline user input, Please enter the string ':END'")
print("to terminate reading input")
while True:
    l_UserInput = input()
    if l_UserInput.strip() == terminate_str:
        break
    data = data + "\n" + l_UserInput

print(data)
```






# Reading Command Line Arguments in Python

## Overview
- The `sys.argv` list stores all command-line arguments passed to the script.
- Arguments are **space-separated**.
- The first element in `sys.argv` is always the script's filename.

---

## Python Code

```python
import sys
```
### The sys.argv returns all the arguments passed to the python script
### , DELIMITED (Separator) by SPACE in this list.
```python
commandline_args_list = sys.argv

print(commandline_args_list)
```
### Call the program using:
### $ python script_name.py argument1 argument2
### The FIRST element in the list is the file path and name







# Adding Two Numbers in Python

## Overview
- This script demonstrates three ways to pass numbers to a function:
  1. **Directly in the script** (hardcoded values)
  2. **Using `input()`** to get user input
  3. **Using `sys.argv`** to read command-line arguments

---

## Python Code

```python
import sys

def add2nums(n1, n2):
    print(n1 + n2)
```
# 1. Directly Call with values in the script
```python
add2nums(n1=100, n2=33)
```
# 2. Get values using input(),
# REMEMBER input data is all STRINGS, Convert to the required datatype
```python
in_n1 = int(input("Enter value for n1: "))
in_n2 = int(input("Enter value for n2: "))
add2nums(n1=in_n1, n2=in_n2)
```
# 3. Get values using command-line arguments
# REMEMBER sys.argv LIST data is all STRINGS, Convert to the required datatype
```python
inputs = sys.argv
add2nums(n1=int(inputs[1]), n2=int(inputs[2]))
```










