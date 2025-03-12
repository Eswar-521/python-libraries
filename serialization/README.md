---
Title: Python Pickle Serialization and De-Serialization
MetaKeywords: python, pickle, serialization, deserialization, object, file handling
Author: Your Name
ContentName: python-pickle-serialization
---

# Python Pickle Serialization and De-Serialization

## Overview

- **Serialization** is the process of converting an object state into a binary file, which can be stored or transmitted.
- Serialization is also known as **deflating** or **marshalling**.
- In Python, we use the **`pickle`** module for object serialization.
- **Deserialization** is the process of loading the serialized object back into memory.
- Deserialization is also known as **inflating** or **unmarshalling**.

---

## Install the Required Module

Python’s `pickle` module is built-in, so no installation is needed.

---

## Code Example

```python
import pickle
```
# Serialization of an Object
# Define a class
```python
class PickleTest:
    # Class Variables
    a = 0
    b = 0

    # Constructor
    def __init__(self, i_a, i_b):
        self.a = i_a
        self.b = i_b
```
# Create an Object
```python
Obj1 = PickleTest(1, 2)
```
# Define file path for serialization
```python
serialization_path = "D:\\training\\PythonFeb2024\\code\\python-libraries\\serialization\\object.pickle"
```
# Serialize the object and save it to a file
```python
with open(serialization_path, 'wb') as f:
    pickle.dump(Obj1, f)
```
## Alternative way without 'with' statement
## f = open(serialization_path, 'wb')
## pickle.dump(Obj1, f)
## f.close()

## De-Serialization of an Object

# Load the object back from the pickle file
```python
with open(serialization_path, 'rb') as f:
    ObjFile = pickle.load(f)
```
# Print the deserialized object
```python
print(ObjFile)
print(ObjFile.a)
print(ObjFile.b)
```











---
Title: Python Object Serialization using Pickle
MetaKeywords: python, pickle, serialization, deserialization, dictionary
Author: Your Name
ContentName: python-pickle-serialization
---

# Serialization of Objects: Dictionary using Python Pickle

This script demonstrates how to serialize and deserialize a dictionary using Python's `pickle` module.

## What is Serialization?
Serialization is the process of converting a Python object into a byte stream, which can be saved to a file or transferred over a network.

## Pre-requisite
No additional installations are required, as `pickle` is a built-in Python module.

## Code Example

```python
# Serialization of objects: Dictionary
import pickle

# Create a dictionary
Dict1 = {'APPLE': 'FRUIT', 'POTATO': 'ROOT', 'OKRA': 'VEGETABLE'}

# Define file path for serialization
l_serialization_loc = "E:/Training/Python
```

# Explanation
- The pickle module is imported to handle serialization.
- A sample dictionary Dict1 is created.
- The dictionary is serialized and saved to a file (object1.pickle).
- The serialized file is then deserialized back into a Python dictionary.
- The dictionary is printed to confirm successful deserialization.
