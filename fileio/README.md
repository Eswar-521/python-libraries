
### YamlDesc: CONTENT-ARTICLE
### Title: Python File IO
### MetaDescription: Python File IO, Reading Files, Writing to files, create directory, remove directory example code, tutorials
### MetaKeywords: Python File IO, Reading Files, Writing to files, create directory, remove directory example code, tutorials
### Author: Venkata Bhattaram / tinitiate.com
### ContentName: file-io

###  PYTHON FILE IO
###  The OS Module of Python handles the **FILE IO (File Input Output)**
###  Common Folder operations include, List Directories, Find Current 
###  Directory Name, Go to a Specific Directory, Create Directory or 
###  Delete Directory.
###  Common File Operations Include Open a File to Read or Write, Read a File 
###  line by line, check if a file exists, Delete a file, Create an empty file.


###  Python FILE IO Directory Operations
###  The Example demonstrates the following:
###  Display Current Directory 
###  Change to a specified Directory
###  List all files and directories in given path
###  List all files directories **Recursively** in given path
###  Create, Remove Directory
###  List in Directory

###  Get Current Directory with getcwd()
### `getcwd()` Displays the Current Directory
```python
import os

print(os.getcwd())
```

### Change To Specified Directory With chdir()
### `chdir()` Changes to specified Directory
```python
import os

my_dir = "f:\\training"

### Change Directory to the specified name in my_dir
os.chdir(my_dir)

# Check if Current Directory is the one specified in variable "my_dir"
print(os.getcwd())
```

### Python List All Files and Directories in a Given Path
### Using `os.walk()` we can list all Files and Folders in a given folder path 
```python
import os
my_dir = "f:\\"
print(os.listdir(my_dir))
```

## Python List All Files and Directories Recursively in a Given Path
## Using `os.walk()` we can list all Files and Folders in a given folder path 
```python
from os import walk

mypath = "f:\\"
all_files = []
all_folders = []

### Loop through all Files and Folders in a Given Path [mypath variable]
for (dirpath, dirnames, filenames) in walk(mypath):
### Capture all files and store in list all_files
    all_files.extend(filenames)
### Capture all files and store in list all_folders
    all_folders.extend(dirnames)

### Print all files and folders lists
print(all_files)
print(all_folders)
```

## Create Directory Using Method os.mkdir
## Create Directory with `os.mkdir`
```python
import os

# New Directory Path
new_dir = "f:\\NewDir"

## Create Directory with mkdir
os.mkdir(new_dir)

### Check if folder exists
print(os.path.exists(new_dir))
```

### Remove Directory using method os.rmdir
### Remove Directory with `os.rmdir`
```python
import os

### New Directory Path
new_dir = "f:\\NewDir"

### Remove Directory
os.rmdir(new_dir)

### Check if folder exists
print(os.path.exists(new_dir))
```

### Python FILE IO File Operations
### The following example demonstrates
### Using the OPEN function we can specify a FILE and the
### FILE-MODE(READ, WRITE, APPEND ..)
### Python Reading and writing to files
### Python Opening files
### Python Reading files line by line
### Python writing to files
### Python writing to files line by line
### Check if File Exists
### Create Empty File

### Read File In Python
### Opening and read file in python
```python
import os
input_file = open("c:\\tinitiate\\data.txt","r")

### Assign the object "input_file" read function
### To a variable
var_text = input_file.read()

### Print the data in one go
print(var_text)

### Close the File stream handler
input_file.close()
```

### Read File Line By Line Using Method readline()
### Read file line by line
```python
import os

### ReOpen the file
input_file1 = open("c:\\tinitiate\\data.txt","r")

### While true enter into an infinite loop (we handle it by a break)
while True:
    curr_line = input_file1.readline()
    if not curr_line:
        break  # Break if there is no line to read
    print(curr_line)  # Print the current line

### Close the File stream handler
input_file1.close()
```

### Read File Line By Line As List Of Strings
```python
import os
readlines_file = open("c:\\tinitiate\\data.txt","r")

### Prints the file contents as a LIST
print(readlines_file.readlines())

readlines_file.close()
```

### Write To File In Python
```python
import os

try:
    os.mkdir("c:\\tinitiate")
except:
    pass

new_file = open("c:\\tinitiate\\data.txt", "w")
new_file.write("Welcome to Tinitiate.COM\n")
new_file.write("Line 2 data\n")
new_file.write("Line 3 data\n")
new_file.close()
```

### APPEND TO EXISTING FILE
```python
append_file = open("c:\\tinitiate\\newdata.txt","a")

list_1 = ['a', 'ZZ']
append_file.writelines(list_1)

tuple_1 = ('A', 'b')
append_file.writelines(tuple_1)

dictionary_1 = {'APPLE':'FRUIT', 'POTATO':'ROOT', 'OKRA':'VEGETABLE'}
append_file.writelines(dictionary_1)

append_file.close()
```

### Delete A File In Python
```python
import os
os.remove("c:\\tinitiate\\newdata.txt" )
```

### Rename a file or folder in PYTHON
```python
import os
os.rename("c:\\tinitiate\\data.txt", "c:\\tinitiate\\info.txt" )
```




### YamlDesc: CONTENT-ARTICLE
### Title: Python File Handling - Writing Multiplication Table to a File
### MetaDescription: Python File Handling, Writing Multiplication Table to a File, Example Code, Tutorials
### MetaKeywords: Python File Handling, Writing to Files, Multiplication Table Example
### Author: Your Name
### ContentName: file-handling-multiplication-table

### Python File Handling - Writing Multiplication Table to a File
### This Python program demonstrates how to write a multiplication table 
### to a text file using Python's built-in file handling capabilities.
### The file will be created in the specified directory, and each line 
### will contain the multiplication result.

### Code Example:
### The following code writes the multiplication table of 5 to a text file.
### ```python
import os

### Define the file path
l_file_path = "D:\\training/PythonFeb2024/"
NUM = 5

### Define the file name
l_file_name = l_file_path + str(NUM) + "_table.txt"

### Create and open the file in write mode
new_file = open(l_file_name, "w")

### Loop to write the multiplication table
for c in range(1, 11):
    str_to_print = str(NUM) + " X " + str(c) + " = " + str(NUM * c) + "\n"
    new_file.write(str_to_print)  # Writing to file

### Close the file
new_file.close()

### Explanation:
### `open(l_file_name, "w")` - Opens the file in write mode.
### `for c in range(1, 11):` - Loops from 1 to 10 to generate the multiplication table.
### `new_file.write(str_to_print + "\n")` - Writes each line to the file.
### `new_file.close()` - Closes the file after writing.

### Output:
### A file named **5_table.txt** will be created in the `D:\training/PythonFeb2024/` directory.
### The file content will look like:
### >```
5 X 1 = 5
5 X 2 = 10
5 X 3 = 15
5 X 4 = 20
5 X 5 = 25
5 X 6 = 30
5 X 7 = 35
5 X 8 = 40
5 X 9 = 45
5 X 10 = 50
### >```

### Notes:
### You can change the value of `NUM` to generate the table for any number.
### Ensure the directory `D:\training/PythonFeb2024/` exists before running the script, or modify the path accordingly.









### PYTHON FILE IO
### The OS Module of Python handles the **FILE IO (File Input Output)**

### Common Folder operations include:
- List Directories
- Find Current Directory Name
- Go to a Specific Directory
- Create Directory or Delete Directory

### Common File Operations Include:
- Open a File to Read or Write
- Read a File line by line
- Check if a file exists
- Delete a file
- Create an empty file

---

### Python FILE IO Directory Operations
### This Example demonstrates the following:
- Display Current Directory 
- Change to a specified Directory
- List all files and directories in a given path
- List all files and directories **Recursively** in a given path
- Create and Remove a Directory
- List Contents in a Directory

---

```python
import os
```
### Get Current Directory with getcwd()
### getcwd() Displays the Current Directory
```python
print(os.getcwd())
```
### Change To Specified Directory With chdir()
### `chdir()` Changes to the specified Directory
```python
my_dir = "D:\\training/PythonFeb2024/"
```
### Change Directory to the specified name in my_dir
```python
os.chdir(my_dir)
```
### Check if Current Directory is the one specified in variable "my_dir"
```python
print(os.getcwd())
```
### Create Directory Using Method os.mkdir

### New Directory Path
```python
new_dir = "E:\\Training"
```
### Check if folder exists
```python
print(os.path.exists(new_dir))
```
### Create Directory with mkdir
```python
try:
    os.mkdir(new_dir)
except Exception as e:
    print(type(e).__name__, e)
```

### Check if folder exists
```python
print(os.path.exists(new_dir))
```
### Remove Directory with rmdir
```python
os.rmdir(new_dir)
```
### Check if folder exists
```python
print(os.path.exists(new_dir))
```
### List Contents in a Directory
```python
print(os.listdir(my_dir))
```
### Rename a file or folder in PYTHON
### The `rename` method can be used to rename both a folder or a file
### Example: 
- rename `c:\tinitiate\data.txt` to `c:\tinitiate\info.txt`
### os.rename(my_dir+"\\newdata.txt" , my_dir+"\\olddata.txt" )

### Delete a file
```python
os.remove(my_dir+"\\olddata.txt" )
```

### Explanation :
- os.getcwd() → Prints the current working directory.
- os.chdir(path) → Changes the working directory to path.
- os.mkdir(path) → Creates a new directory at path.
- os.rmdir(path) → Removes the directory at path (only if empty).
- os.listdir(path) → Lists files and directories at path.
- os.rename(old, new) → Renames a file or folder.
- os.remove(path) → Deletes the file at path.








### Read File in Python

### **Overview**
The `open()` function in Python is used to open files in different modes such as Read, Write, and Append. The function returns a file object, which can be used to read or write the file.

---

### **Steps:**
1. Open the file in **read mode** (`"r"`).
2. Use the `read()` function to read the file contents.
3. Print the contents.
4. Close the file using `close()` to free up system resources.

---

```python
import os
```
### Define file path
```python
l_file_path = "D:\\training/PythonFeb2024/data.txt"
```
### Open the file in READ mode
```python
input_file = open(l_file_path, "r")
```
### Read file contents into a variable
```python
var_text = input_file.read()
```
### Print the file content
```python
print(var_text)
```
### Close the File
```python
input_file.close()
```



### Read File Line By Line as a List of Strings

### **Overview**
Reading a file **line by line** helps in efficiently handling large files. The `readlines()` method reads all lines of a file and returns them as a **list of strings**, where each line ends with a newline character (`\n`).

---

### **Steps:**
1. Open the file in **read mode** (`"r"`).
2. Use the `readlines()` function to read the file contents **line by line** into a list.
3. Print the list of lines.
4. Close the file to free up system resources.

---

```python
import os
```
### Define file path
```python
l_file_path = "D:\\training/PythonFeb2024/data.txt"
```

### Open the file in READ mode
  ```python
readlines_file = open(l_file_path, "r")
```
### Read the file line by line into a list
  ```python
file_lines = readlines_file.readlines()
```
### Print the file content as a list
```python
print(file_lines)
```
### Close the file
```python
readlines_file.close()
```

### **Explanation:**
- open(l_file_path, "r") → Opens the file in read mode.
- readlines_file.readlines() → Reads the file line by line into a list.
- print(file_lines) → Prints the list of strings.
- readlines_file.close() → Closes the file to prevent memory leaks.













### Read File Line By Line Using `readline()` Method

### **Overview**
Reading a file **line by line** using the `readline()` method allows efficient handling of large files without loading the entire content into memory at once.

---

### **Steps:**
1. Open the file in **read mode** (`"r"`).
2. Use a `while` loop to read one line at a time.
3. Stop reading when there are **no more lines** (i.e., when `readline()` returns an empty string).
4. Print each line as it is read.
5. Close the file.

---

```python
import os
```
### Define the file path
```python
l_file_path = "D:\\training/PythonFeb2024/data.txt"
```
### Open the file in READ mode
```python
input_file1 = open(l_file_path, "r")
```
### Read file line by line using a while loop
```python
while True:
    curr_line = input_file1.readline()  # Read the current line
    if not curr_line:
        break                           # Break if no more lines
    print(curr_line)                    # Print the current line
```
### Close the file
```python
input_file1.close()
```


### **Explanation:**
- open(l_file_path, "r") → Opens the file in read mode.
- readline() → Reads one line at a time from the file.
- if not curr_line: break → Breaks the loop when no more lines exist.
- print(curr_line) → Prints each line as it is read.
- close() → Closes the file to free up resources.










### **Write to File in Python**

### **Overview**
The `open()` function in Python is used to **read**, **write**, and **append** data to files.

### **Usage:**
```python
FILE_OBJECT = open("File_Path/File_Name", FILE_MODE)
```

### File Modes :
- "r" → Read Mode (Default) - Opens an existing file for reading.
- "w" → Write Mode - Overwrites the file if it exists; creates a new file if it doesn't.
- "a" → Append Mode - Appends data to the file without overwriting.
- "r+" → Read & Write Mode - Allows both reading and writing.

### Step 1 : Writing to a File 
```python
import os

### Define file path
l_file_path = "D:\\training/PythonFeb2024/output.txt"

### Open file in WRITE mode (overwrites existing file or creates a new one)
new_file = open(l_file_path, "w")

## Write data to the file
new_file.write("Welcome to Tinitiate.COM\n")
new_file.write("Line 2 data")
new_file.write("Line 3 data\n")

### Close the file
new_file.close()
```

### Explanation 
- The file is opened in "w" mode, which overwrites existing content.
- write() adds text to the file.
- \n ensures a new line is inserted.


### Step 2: Appending to a File
- Appending allows adding content without overwriting existing data.

```python
### Define file path for appending
l_file_append_path = "D:\\training/PythonFeb2024/output1.txt"

### Open file in APPEND mode
append_file = open(l_file_append_path, "a")

### Writing a LIST to file
list_1 = ['a', 'ZZ']
append_file.writelines(list_1)  # Writelines writes a list of strings

### Writing a TUPLE to file
tuple_1 = ('A', 'b')
append_file.writelines(tuple_1)

### Writing a DICTIONARY (only keys are written)
dictionary_1 = {'APPLE': 'FRUIT', 'POTATO': 'ROOT', 'OKRA': 'VEGETABLE'}
append_file.writelines(dictionary_1)  # Only keys will be written

### Close the file
append_file.close()
```
### Key Takeaways

- write() → Writes a string to the file.
- writelines() → Writes multiple strings from a list, tuple, or dictionary.
- File opened in "w" mode is overwritten, whereas "a" mode appends data.
- Closing the file (close()) is essential to ensure all data is properly saved.

### Example Output (output.txt after writing)

```python
Welcome to Tinitiate.COM
Line 2 dataLine 3 data
```
### Example Output (output1.txt after appending)
```python
aZZAbAPPLEPOTATOOKRA
```






### **Python: List All Files and Directories Recursively**

## **Overview**
In Python, we can use the `os.walk()` function to **list all files and directories** in a given folder path **recursively**.

---

### **Code Implementation**
```python
from os import walk

### Define the directory path
mypath = "E:\\Training\\PythonSep2023"

### Initialize empty lists to store file and folder names
all_files = []
all_folders = []

### Loop through all files and folders in the given path
for (dirpath, dirnames, filenames) in walk(mypath):
    
    # Capture all files and store in list all_files
    all_files.extend(filenames)
    
    # Capture all directories and store in list all_folders
    all_folders.extend(dirnames)

### Print all files and folders lists
print("Files:", all_files)
print("Folders:", all_folders)
```

### Explanation
- os.walk(mypath) recursively iterates through the directory structure.
- dirpath → Current directory path being traversed.
- dirnames → List of directories in the current directory.
- filenames → List of files in the current directory.
- all_files.extend(filenames) → Collects all files in the list.
- all_folders.extend(dirnames) → Collects all directories in the list.






### **File Handling in Python using `with open()` Statement**

### **Reading from a File**
```python
with open('E:\\python-master\\media\\003-python-modules\\data.csv', 'r') as f:
    contents = f.read()
    print(contents)
```
Opens `data.csv` in **read (`'r'`) mode** and prints the contents.

---

### **Appending to a File**
```python
with open('E:\\python-master\\media\\003-python-modules\\data.txt', 'a') as f:
    f.write('Welcome to Tinitiate.\n')
```
Opens `data.txt` in **append (`'a'`) mode** and adds a new line at the end.

---

### **Writing to a File**
```python
with open('E:\\python-master\\media\\003-python-modules\\data.txt', 'w') as f:
    f.write('Hello, Tinitiate!')
```
Opens `data.txt` in **write (`'w'`) mode**, **overwriting** existing content.

---

### **Creating a New File**
```python
with open('E:\\python-master\\media\\003-python-modules\\data_new.txt', 'x') as f:
    f.write('Welcome to Tinitiate!\n')
```
Opens `data_new.txt` in **exclusive creation (`'x'`) mode**. 
Fails if the file already exists.

### **Reading & Writing Using `r+` Mode**
```python
with open('file.txt', 'r+') as f:
# Read the file
data = f.read()

# Write to the file
f.write('Hello, World!')
```
Opens `file.txt` in **read & write (`'r+'`) mode**. 
Reads the content first, then writes at the end of the file.

---

### **Summary of File Modes in Python**
| Mode | Description |
|------|------------|
| `'r'` | Read mode (default) |
| `'w'` | Write mode (overwrites file) |
| `'a'` | Append mode (adds new content at the end) |
| `'x'` | Exclusive creation (fails if file exists) |
| `'r+'` | Read and write mode |





### Process Very Large Files with Python
### Here we demonstrate working with very large files 
```python
import string
import random
from random import choice
import os 
```
### STEP 1.
### Create a very large file
### Path where large file will be created
```python
l_filename = "E:/code/PYTHON_TRAINING/CODING_PythonLabs/code/001-python-core-language/code/large_data.csv"

with open(l_filename, "w") as flh:
    for c in range(55555):
        row = (''.join(random.choice(string.ascii_uppercase) for i in range(100)) + ",")*50
        flh.write(row[:-1] + "\n")
        # print(row[:-1] + "\n")
```
### Read Very Large Files with Python
### Here we demonstrate reading a very large file, line by line

### Print File Size in MB
```python
size_in_MB = os.stat(l_filename).st_size / (1024 * 1024)
print("File Size is", size_in_MB, "MB")
```
### Count the number of lines
```python
l_ctr = 0
with open(l_filename) as infile:
for line in infile:
l_ctr += 1

print(l_ctr)
```
### Remove the File
```python
os.remove(l_filename)
```
