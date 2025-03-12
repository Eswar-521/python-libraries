# Using API and JSON Processing in Python

## Overview
- This script fetches weather data from an API.
- It parses the JSON response using `json.loads()`.
- The processed data is stored in a structured format and saved as a JSON file.

---

## Python Code

```python
import json
import requests
```
# Using API
# Using json.loads()

# Fetch data from API
```python
request = requests.get("http://www.7timer.info/bin/api.pl?lon=113.17&lat=23.09&product=astro&output=json")
response = request.text
```
# Parse JSON response
```python
data = json.loads(response)
print(json.dumps(data, indent=2))
```
# Process and extract relevant data
```python
dataseries = []
temp = {}

for item in data['dataseries']:
    temp['timepoint'] = item['timepoint']
    temp['cloudcover'] = item['cloudcover']
    temp['seeing'] = item['seeing']
    temp['transparency'] = item['transparency']
    temp['rh2m'] = item['rh2m']
    temp['lifted_index'] = item['lifted_index']
    
    dataseries.append({
        'Timepoint': temp['timepoint'],
        'Cloudcover': temp['cloudcover'],
        'Seeing': temp['seeing'],
        'Transparency': temp['transparency'],
        'Rh2m': temp['rh2m'],
        'Lifted_index': temp['lifted_index']
    })     
```
# Save extracted data to a JSON file
```python
with open('E:\\python-master\\media\\003-python-modules\\Weather_forecasts.json', 'w') as f:
    json.dump(dataseries, f, indent=2)
```






# Processing JSON Data in Python

## Overview
- This script parses a JSON bill structure.
- It removes the `Product` field from each item in `BillDetails`.
- The updated JSON data is saved to a file.

---

## Python Code

```python
import json
```
# Sample JSON data
```python
bill_json =  """{ "BillNumber":1245
                 ,"BillTotal":3000
                 ,"StoreLocation":"New York"
                 ,"BillDetails":[ { "Product":"Soda"
                                   ,"Quantity":10
                                   ,"UnitPrice":2
                                   ,"LineItemPrice": 20}
                                 ,{ "Product":"Chips"
                                   ,"Quantity":5
                                   ,"UnitPrice":3
                                   ,"LineItemPrice":15 }
                                 ,{ "Product":"Cookies"
                                   ,"Quantity":4
                                   ,"UnitPrice":5
                                   ,"LineItemPrice":20 } ]
                 }"""
```
# Parse JSON string into Python dictionary
```python
data = json.loads(bill_json)
```
# Remove 'Product' key from each item in 'BillDetails'
```python
for item in data["BillDetails"]:
    del item["Product"]
```
# Save updated JSON data to a file
```python
with open('E:\\python-master\\media\\003-python-modules\\Bills_new.json', 'w') as f:
    json.dump(data, f, indent=2)
```









# Processing JSON Data in Python

## Overview
- This script parses a JSON bill structure.
- It removes the `Product` field from each item in `BillDetails`.
- The updated JSON data is printed with proper indentation.

---

## Python Code

```python
import json
```
# Sample JSON data
```python
bill_json =  """{ "BillNumber":1245
                 ,"BillTotal":3000
                 ,"StoreLocation":"New York"
                 ,"BillDetails":[ { "Product":"Soda"
                                   ,"Quantity":10
                                   ,"UnitPrice":2
                                   ,"LineItemPrice": 20}
                                 ,{ "Product":"Chips"
                                   ,"Quantity":5
                                   ,"UnitPrice":3
                                   ,"LineItemPrice":15 }
                                 ,{ "Product":"Cookies"
                                   ,"Quantity":4
                                   ,"UnitPrice":5
                                   ,"LineItemPrice":20 } ]
                 }"""
```
# Parse JSON string into Python dictionary
```python
data = json.loads(bill_json)
```
# Remove 'Product' key from each item in 'BillDetails' and print updated JSON
```python
for item in data["BillDetails"]:
    del item["Product"]
    data_new = json.dumps(data, indent=2)
    print(data_new)
```






# Reading JSON File into a Python Dictionary

## Overview
- This script reads a JSON file and loads it into a Python dictionary.
- It extracts and prints the `StoreLocation` field.
- It iterates over `BillDetails` to print each `Product` name.

---

## Python Code

```python
import json
```
# Reading JSON file to JSON object/dictionary  
# Using load()
```python
with open('E:\\python-master\\media\\003-python-modules\\bills.json') as f:
    data = json.load(f)  # Load JSON data into a dictionary
    print(data)  # Print entire JSON data
```
# Extract and print StoreLocation
```python
StoreLocation = data['StoreLocation']
print(StoreLocation)
```
# Iterate through BillDetails and print each Product
```python
for bill in data['BillDetails']:
    Product = bill['Product']
    print(Product)
```








# Parsing and Extracting Data from JSON in Python

## Overview
- This script parses a JSON string using `json.loads()`.
- It extracts and prints the `BillDetails` list.
- It retrieves the first product from `BillDetails`.
- It iterates over `BillDetails` to print all product names.

---

## Python Code

```python
import json
```
# Some JSON data:
```python
bill_json =  """{ "BillNumber":1245
                 ,"BillTotal":3000
                 ,"StoreLocation":"New York"
                 ,"BillDetails":[ { "Product":"Soda"
                                   ,"Quantity":10
                                   ,"UnitPrice":2
                                   ,"LineItemPrice": 20}
                                 ,{ "Product":"Chips"
                                   ,"Quantity":5
                                   ,"UnitPrice":3
                                   ,"LineItemPrice":15 }
                                 ,{ "Product":"cookies"
                                   ,"Quantity":4
                                   ,"UnitPrice":5
                                   ,"LineItemPrice":20 } ]
                 }"""
```
# Parse JSON using "loads" method
```python
data = json.loads(bill_json)
```
# Get subset of JSON (BillDetails)
```python
print(data["BillDetails"])
```
# JSON Nested value: Get First Product
```python
print(data["BillDetails"][0]["Produ`ct"])
```
# JSON Get All Products
```python
for restaurant in data["BillDetails"]:
    print(restaurant["Product"])
```









# Validating JSON Data with JSON Schema in Python

## Overview
- This script reads JSON data from a file.
- It loads a JSON schema from another file.
- It validates the JSON data against the schema using `jsonschema.validate()`.
- If the data is malformed or does not conform to the schema, appropriate error messages are displayed.

---

## Python Code

```python
import json
import jsonschema
```
# Read the JSON data from file
```python
try:
    with open('E:/python-master/media/003-python-modules/product.json', 'r') as f:
        data = json.load(f)
except ValueError as e:
    print("Malformed JSON data:", e)
    exit()
```
# Read the JSON schema from file
```python
try:
    with open('E:/python-master/media/003-python-modules/schema.json', 'r') as f:
        schema = json.load(f)
except ValueError as e:
    print("Malformed JSON schema:", e)
    exit()
```
# Validate the JSON data against the schema
```python
try:
    jsonschema.validate(data, schema)
    print("JSON data is valid!")
except jsonschema.exceptions.ValidationError as e:
    print("JSON validation error:", e)
```







