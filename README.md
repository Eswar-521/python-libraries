# PostgreSQL Database Connection and Data Retrieval using `psycopg2`

## Overview
This script connects to a **PostgreSQL** database using the `psycopg2` library, fetches data from a table called `ti_test`, and prints the results.

---

## 📌 **Code Breakdown**

### 1️⃣ **Importing Required Library**
```python
import psycopg2
```
- `psycopg2` is the PostgreSQL adapter for Python, allowing interaction with PostgreSQL databases.
  
- ### 2️⃣  Establishing a Connection
```python
conn = psycopg2.connect(database="postgres",
                        user="tinitiate",
                        password="Tinitiate!23456",
                        host="127.0.0.1",  # localhost
                        port="5432")
```
- `database="postgres"` → Specifies the database name.
- `user="tinitiate"` → The username for authentication.
- `password="Tinitiate!23456"` → The password for authentication.
- `host="127.0.0.1"` → Localhost IP, meaning the database runs on the local machine.
- `port="5432"` → Default PostgreSQL port.
- This establishes a connection to the PostgreSQL database.
  
- ### 3️⃣ Creating a Cursor Object
```python
cursor = conn.cursor()
```
- A `cursor` allows execution of SQL queries and retrieval of data.
  
- ### 4️⃣ Executing a SQL Query to Fetch Data
```python
cursor.execute("select col1, col2, col3, col4 from ti_test;")
rowdata = cursor.fetchone()
print(rowdata)
```
- Executes a SELECT query to retrieve the first row from the ti_test table.
- fetchone() fetches a single row.
- print(rowdata) prints the retrieved row.

- ### 5️⃣ Fetching and Printing All Rows
```python
cursor.execute("select col1, col2, col3, col4 from ti_test;")
for l_col1, l_col2, l_col3, l_col4 in cursor.fetchall():
    print("l_col1: ", l_col1)
    print("l_col2: ", l_col2)
    print("l_col3: ", l_col3)
    print("l_col4: ", l_col4)
```
- Executes the SELECT query again.
- fetchall() retrieves all rows from the query result.
- The for loop iterates over each row and prints its values.
  
- ### 6️⃣ Closing the Cursor and Connection
```python
cursor.close()
conn.close()
```
- cursor.close() → Closes the cursor.
- conn.close() → Closes the database connection to free up resources.


