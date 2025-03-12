# Python Logging Example

## Overview
This script demonstrates how to set up and use Python's built-in logging module. It:
- Creates a logging object.
- Configures a console stream handler.
- Defines a log format.
- Logs messages at different levels.
- Adjusts the log level and observes the output.

---

## Python Code

```python
import sys, logging
```
# Create a LOGGING Object
```python
tiConsLog = logging.getLogger('tinitiate-console')
```
# Create a StreamHandler for the LOGGING Object
```python
ConsHandler = logging.StreamHandler(sys.__stdout__)
```
# Set Log Formatting
```python
formatter = logging.Formatter('[%(asctime)s] %(name)-12s: %(levelname)-8s %(message)s')
ConsHandler.setFormatter(formatter)
```
# Add the Console Handler to the LOGGING Object
```python
tiConsLog.addHandler(ConsHandler)
```
# Set Log Level
```python
tiConsLog.setLevel(logging.DEBUG)
```
# Log messages at different levels
```python
tiConsLog.debug('This is a debug message')
tiConsLog.info('This is an info message')
tiConsLog.warning('This is a warning message')
tiConsLog.error('This is an error message')
tiConsLog.critical('This is a critical message')
```
# Change Log level and retry logging all levels
```python
tiConsLog.setLevel(logging.ERROR)

tiConsLog.debug('This is a debug message')
tiConsLog.info('This is an info message')
tiConsLog.warning('This is a warning message')
tiConsLog.error('This is an error message')
tiConsLog.critical('This is a critical message')
```








# Python File Logging Example

## Overview
This script demonstrates:
- Creating a logging object for file logging.
- Configuring a log file with a unique timestamp-based filename.
- Implementing logging in both functional and object-oriented approaches.

---

## Python Code

```python
import sys, logging
import time
```
# Create a LOGGING Object
```python
tiFileLog = logging.getLogger('tinitiate-file')
```
# Generate a log filename with a timestamp
```python
l_log_file_name = "app_log" + str(time.time()) + ".log"
```
# Create a Log File Handler
```python
LogFile = logging.FileHandler('D:/training/PythonFeb2024/' + l_log_file_name)
```
# Set Log Formatting
```python
formatter = logging.Formatter('[%(asctime)s] %(name)-12s: %(levelname)-8s %(message)s')
LogFile.setFormatter(formatter)
```
# Add the handler to the logging object
```python
tiFileLog.addHandler(LogFile)
```
# Set Log Level
```python
tiFileLog.setLevel(logging.DEBUG)
```
# Run Log messages
```python
tiFileLog.debug('This is a debug message')
tiFileLog.info('This is an info message')
tiFileLog.warning('This is a warning message')
```
# Only the following messages are logged to the file
```python
tiFileLog.error('This is an error message')
tiFileLog.critical('This is a critical message')
```
# Function-Based Logging
```python
def add2nums(n1, n2, log_obj):
    try:
        log_obj.debug(f'Functional Inputs: n1 = {n1} || n2 = {n2}')
        print(n1 + n2)
    except Exception as e:
        log_obj.error(f'Functional Inputs: n1 = {n1} || n2 = {n2}')
        log_obj.error(f'{type(e).__name__} {e}')

tiFileLog.debug('Starting Adder')
add2nums(12, 22, tiFileLog)  # Pass logger object as parameter
add2nums('a', 22, tiFileLog)  # Will trigger an error
```
# Object-Oriented Logging
```python
class MathOperations:
    def __init__(self, p_log_obj):
        # Instance Variable
        self.log_obj = p_log_obj
        self.log_obj.setLevel(logging.ERROR)

    def add2nums(self, n1, n2):
        try:
            self.log_obj.debug(f'OOP Inputs: n1 = {n1} || n2 = {n2}')
            print(n1 + n2)
        except Exception as e:
            self.log_obj.error(f'OOP Inputs: n1 = {n1} || n2 = {n2}')
            self.log_obj.error(f'{type(e).__name__} {e}')

a1 = MathOperations(tiFileLog)  # Pass logger object to the constructor
a1.add2nums(22, 11)
a1.add2nums(22, 'bbb')  # Will trigger an error
```






