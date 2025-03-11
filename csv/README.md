# Reading a CSV File in Python

## Code

```python
import csv

with open('D:/training/PythonFeb2024/code/python-libraries/csv/data.csv', 'r') as csv_file:
    csv_reader = csv.DictReader(csv_file)

    for line in csv_reader:
        # Output of the reader is a dictionary
        print(line)       
        
        # Getting specific column from the list, in this case, 'LastName'.
        print(line['LastName'])
```


# Explanation:
**Import CSV Module** 
```Python 
import csv 
```
- This import Python's built-in CSV module for handling CSV files.
  
## Open the csv Module
```python
with open('D:/training/PythonFeb2024/code/python-libraries/csv/data.csv', 'r') as csv_file:
```
- Open the CSV File in read mode('r').
- Uses a `With` statement to ensure the file is properly closed after use.
  
## Read the CSV File as a Dictionary
```python 
csv_reader = csv.DictReader(csv_file)
```
- DictReader reads each row as a dictionary where column headers are keys.
  
## Loop Through CSV Rows
```python
for line in csv_reader:
```
- Iterates through each row in the CSV.
  
## Print Each Row as a Dictionary
```python
print(line)
```
- Display the row as a dictionary.
  
## Print a Specific column Value (LastName)
```python
print(line['LastName'])
```
- Extracts and prints the LastName column from each row.


<!-- csv_dict_writer -->


#  Writing a CSV File Using `csv.DictWriter` 

### **Python Code**
```python
import csv

with open('E:\\python-master\\media\\003-python-modules\\data.csv', 'r') as csv_file:    
    csv_reader = csv.DictReader(csv_file)    

    with open('E:\\python-master\\media\\003-python-modules\\data_new.csv', 'w') as new_file:        
        fieldnames = ['FirstName', 'LastName', 'Email', 'Amount', 'MaxAmount', 'Status', 'Country', 'Start']

        # Create a CSV DictWriter object with a tab delimiter
        csv_writer = csv.DictWriter(new_file, fieldnames=fieldnames, delimiter='\t') 

        # Write the header row to the new CSV file
        csv_writer.writeheader()

        for line in csv_reader:  
            # Write each row from the original file to the new file
            csv_writer.writerow(line)
```

# Explanation

**Import the CSV Module** 
```python
import csv
```
- This is required the work with CSV files.
  
**Open the Original CSV File for Reading**
```python
with open('E:\\python-master\\media\\003-python-modules\\data.csv', 'r') as csv_file:
```
- Opens the original CSV file in read mode ('r').

**Read the File Using `DicReader`**
```python
csv_reader = csv.DictReader(csv_file)
```
- Reads each row as a dictionary where column headers are keys.

**Open a New CSV File for Writing**
```python
with open('E:\\python-master\\media\\003-python-modules\\data_new.csv', 'w') as new_file:
```
- Creates a new CSV file in write mode ('w').
  
**Define the Column Headers**
```python
fieldnames = ['FirstName', 'LastName', 'Email', 'Amount', 'MaxAmount', 'Status', 'Country', 'Start']
```
- Uses DictWriter to write dictionaries to CSV.
- delimiter='\t' makes it a tab-separated file.
  
**Write the Header Row**
```python
csv_writer.writeheader()
```
- Writes column names as the first row.
  
**Write Each Row from the Original CSV**
```python
for line in csv_reader:
    csv_writer.writerow(line)
```
- Iterates through each row and writes it to the new file.
  

<!-- csv_reader -->


# Reading a CSV File in Python Using `csv.reader`

## **Python Code**
```python
import csv

# Open the CSV file in read mode
with open('D:/training/PythonFeb2024/code/python-libraries/csv/data.csv', 'r') as csv_file:
    # Create a CSV reader object
    csv_reader = csv.reader(csv_file)    
    print(csv_reader)    
    
    # Ignore Headers or first line of the data
    # next(csv_reader)
    
    for line in csv_reader:    
        # Output of the reader is a list
        print(line)  

        # Getting specific column from the list, in this case, the 'Email' column (index 2).
        print(line[2])
```

# Explanation
**Import the CSV Module**
```python
import csv
```
- import Python's built-in `csv` module to work with CSV files.
  
**Open the CSV  File**
```python
with open('D:/training/PythonFeb2024/code/python-libraries/csv/data.csv', 'r') as csv_file:
```
- Opens the CSV file in **read mode** ('r')
- Uses the with statement to ensure the file is automatically closed after execution.
  
**Create a CSV Reader Object**
```python
csv_reader = csv.reader(csv_file)
```
- Reads the CSV file and treats each row as a list of values.
  
**Print the CSV Reader Object**
```python
print(csv_reader)
```
- Displays the object reference (not the actual data).

**Skipping the Header Row (Optional)**
```python
 next(csv_reader)
```
- The next(csv_reader) statement (currently commented out) skips the first row (header) of the CSV file.

**Loop Through CSV Rows**
```python
for line in csv_reader:
```
- Iterates over each row in the CSV file.
  
**Print Each Row as a List**
```python
print(line)
```
- Displays each row as a list of values.
  
**Print a Specific Column (Email)**
```python
print(line[2])
```
- Extracts the third column (index 2) from each row, assuming it represents the Email field.


<!-- csv_writer.py-->

# Python CSV File Read 
```python
import csv
with open('D:/training/PythonFeb2024/code/python-libraries/csv/data.csv', 'r') as csv_file:
    csv_reader = csv.reader(csv_file)    
    
    # with open('data_new.csv', 'w',newline='') as new_file:
    with open('D:/training/PythonFeb2024/code/python-libraries/csv/output-data.csv', 'w') as new_file:

        # csv writer method
        csv_writer = csv.writer(new_file,delimiter='\t') 
    
        for line in csv_reader:    

            # csv method to write items in a sequence           
            csv_writer.writerow(line)
```

# Explanation 
**Importing Required Library**
```python
import csv
```
- The csv module is imported to handle reading and writing CSV files.
  
**Opening the CSV File for Reading**
```python
with open('D:/training/PythonFeb2024/code/python-libraries/csv/data.csv', 'r') as csv_file:
```
- The open() function is used to open the file data.csv located at the specified path.
- The file is opened in read mode ('r').
- The with statement ensures the file is properly closed after reading.
- The file object is assigned to csv_file.
  
**Creating a CSV Reader Object**
```python
    csv_reader = csv.reader(csv_file)    
```
- The `csv.reader()` function is used to read the CSV file.
- The `csv_reader` object iterates over the rows of the file.
  
**Opening the Output File for Writing**
```python
    with open('D:/training/PythonFeb2024/code/python-libraries/csv/output-data.csv', 'w') as new_file:
```
- The `open()` function is used to create/open a new file `output-data.csv`.
- The file is opened in write mode `('w')`.
- The `with` statement ensures that the file is closed properly after writing.
- The file object is assigned to `new_file`.
  
**Creating a CSV Writer Object**
```python
csv_writer = csv.writer(new_file, delimiter='\t') 
```
- The csv.writer() function is used to create a CSV writer object.
- The delimiter='\t' specifies that values in the output CSV should be separated by a tab     (\t) instead of a comma.
  
**Iterating Over Each Line in the CSV File**
```python
        for line in csv_reader:    
```
- A for loop iterates over each row (line) in the csv_reader object.

**Writing Each Line to the New File**
```python
    csv_writer.writerow(line)
```
- The `writerow()` method writes each row from the input file (csv_reader) to the output file `(csv_writer)`.
- The row is written as a sequence of values, separated by a tab (`\t`).
  
