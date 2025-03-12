# OS Module in Python

## Execute OS Commands Using `os.system`

### **Overview**
The `os` module in Python allows interaction with the operating system.  
We can use `os.system()` to execute system commands directly from a Python script.

---

## **Python Code**
```python
import os
```
# String to store the OS command

- OScommand = "echo Tinitiate.com"

# Run the OS command using system function
- os.system(OScommand)



# Explanation
- # 1 Import the OS Module

- import os allows us to access system functionalities.
Define the Command

- # 2 OScommand = "echo Tinitiate.com"
- This command prints "Tinitiate.com" to the terminal.
- # 3 Execute the Command

- os.system(OScommand) runs the command in the shell.













# Python Error Handling - ZeroDivisionError

## **Overview**
This script demonstrates:
1. **Standard Output** using `print()`
2. **ZeroDivisionError** caused by dividing a number by zero.

## **Python Code**
```python
# Output
print("Output Message from os_test.py")

# ZeroDivisionError
a = 1 / 0

```
# Explanation
- # 1 Print Output
- print("Output Message from os_test.py")
- This will print a message to the console.
- # 2 ZeroDivisionError

- a = 1 / 0
- This line will raise a ZeroDivisionError since division by zero is not allowed in Python.






# Python Execute OS Command with SubProcess Module

## **Overview**
This script demonstrates different ways to execute OS commands using the `subprocess` module in Python.

---

## **Using `subprocess.call`**
```python
import subprocess
```
# Simple subprocess.call example
- subprocess.call(['echo', 'Hello Tinitiate'], shell=True)

# Using subprocess.Popen
## Key Differences from call
- Popen does not block execution; the script continues running.
- To make it wait, use .wait().
- Can be used to capture Standard Output (stdout) and Standard Error (stderr).
# Capturing Standard Output
# Capture Standard Output
```python
(standard_output, standard_error) = subprocess.Popen(
    ['echo', 'Hello World!'],
    stdout=subprocess.PIPE,
    stderr=subprocess.PIPE,
    shell=True
).communicate()

# Print output and error
print(standard_output)
print(standard_error)
```


# Capturing Standard Error
```python
# Execute an INVALID command to generate an error
(standard_output, standard_error) = subprocess.Popen(
    ['eco', 'Error'],  # Incorrect command (intentional error)
    stdout=subprocess.PIPE,
    stderr=subprocess.PIPE,
    shell=True
).communicate()

# Print output and error
print(standard_output)
print(standard_error)
```


# Executing a Python Script
```python
# Execute an external Python script
(standard_output, standard_error) = subprocess.Popen(
    ['python', 'D:/training/PythonFeb2024/code/python-libraries/os-commands/os_test.py'],
    stdout=subprocess.PIPE,
    stderr=subprocess.PIPE,
    shell=True
).communicate()

# Print output and error
print(standard_output)
print(standard_error)
```

# Expected Output
```python
Hello Tinitiate
b'Hello World!\r\n'
b''
---------------
b''
b"'eco' is not recognized as an internal or external command,\noperable program or batch file.\r\n"
---------------
Output Message from os_test.py
Traceback (most recent call last):
  File "D:/training/PythonFeb2024/code/python-libraries/os-commands/os_test.py", line 5, in <module>
    a = 1 / 0
ZeroDivisionError: division by zero
```


# Subprocess `wait()`

## **Overview**
- The `wait()` method in the `subprocess.Popen` class **waits** for the process to complete and returns the **exit code**.
- When a process is started using `Popen`, it runs **asynchronously** in the background.
- `wait()` ensures that the process **finishes execution** before the next line of code runs.
- Useful when subsequent code **depends** on the completion of a subprocess.

---

## **Example: Using `wait()`**
```python
import subprocess
```
# Start a subprocess to execute an OS command
```python
process = subprocess.Popen(
    ['echo', 'Hello World!'],
    stdout=subprocess.PIPE,
    stderr=subprocess.PIPE,
    shell=True
)
```
# Capture standard output and error
```python
output, error = process.communicate()
```
# Wait for the process to complete
```python
process.wait()
```
# Print the output and error
```python
print("Output:", output.decode().strip())  # Decoding bytes to string
print("Error:", error.decode().strip())    # Decoding bytes to string
```

# Explanation
- `Popen` starts the command asynchronously.
- `communicate()` captures standard output `(stdout) `and standard error `(stderr)`.
- `wait()` ensures the command has fully executed before moving forward.
- Output is decoded from bytes to string for better readability.





