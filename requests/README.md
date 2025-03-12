---
Title: Python DELETE Request using Requests Library
MetaKeywords: python, requests, HTTP DELETE, API, REST API
Author: Your Name
ContentName: python-delete-request
---

# Python DELETE Request using the Requests Library

This script demonstrates how to send an HTTP `DELETE` request using Python's `requests` library.

## Pre-requisite

Before running the code, install the `requests` library using:

```bash
pip install requests
```

# Code Example
```python
import requests

url = 'https://fakestoreapi.com/products/8'
response = requests.delete(url)

if response.status_code == 200:
    print('DELETE request successful!')
else:
    print('DELETE request failed with status code:', response.status_code)
```











---
Title: Python GET Request with Query Parameters
MetaKeywords: python, requests, HTTP GET, API, REST API, query parameters
Author: Your Name
ContentName: python-get-request-params
---

# Python GET Request with Query Parameters

This script demonstrates how to send an HTTP `GET` request with query parameters using Python's `requests` library.

## Pre-requisite

Before running the code, install the `requests` library using:

```bash
pip install requests
```
# Explanation
- The params dictionary specifies the query parameters:
- 'limit': 3 → Limits the results to 3 items.
- 'sort': 'desc' → Sorts the results in descending order.
- The requests.get() method sends the GET request with these parameters.
- The response is converted to JSON format and printed.













---
Title: Fetch Private GitHub Repositories using Python
MetaKeywords: python, requests, GitHub API, private repositories, authentication
Author: Your Name
ContentName: python-github-api-private-repos
---

# Fetch Private GitHub Repositories using Python

This script demonstrates how to retrieve a list of private repositories from GitHub using Python's `requests` library.

## Pre-requisite

Before running the code, install the `requests` library using:

```bash
pip install requests
```

# Code Example 
import requests      
import configparser   

# Read the GitHub access token from a configuration file
config = configparser.ConfigParser()

# Specify the path to the configuration file
config.read('E:\\python-master\\code\\config.ini')   

# Read the GitHub access token from the 'DEFAULT' section
github_token = config['DEFAULT']['github_token']  

# Set the API endpoint and authentication headers
api_endpoint = 'https://api.github.com/user/repos'   

# Set the authorization header using the GitHub access token
headers = {'Authorization': f'token {github_token}'}   

# Set the parameters for the API request
parameters = {'type': 'private', 'per_page': 5, 'sort': 'updated'}  

# Make a GET request to the API endpoint to get a list of private repositories
response = requests.get(api_endpoint, headers=headers, params=parameters)  

# Print the name of each private repository
for repo in response.json():   
    print(repo['name'])  

# Explanation
- Reads the GitHub access token from a configuration file (config.ini).
- Sets the API endpoint to fetch user repositories.
- Uses an authorization header with the GitHub token.
- Filters repositories to return only private ones, sorted by the latest updates.
- Prints the names of up to 5 private repositories.














---
Title: Fetch Fake Store API Products using Python
MetaKeywords: python, requests, API, fetch data, Fake Store API
Author: Your Name
ContentName: python-fetch-fakestoreapi-products
---

# Fetch Products from Fake Store API using Python

This script demonstrates how to retrieve product data from the Fake Store API using Python's `requests` library.

## Pre-requisite

Before running the code, install the `requests` library using:

```bash
pip install requests
```

# Code 
```python

import requests

# Send a GET request to the Fake Store API
response = requests.get('https://fakestoreapi.com/products')

# Print the response text (JSON data)
print(response.text)
```

# Explanation
- Uses the requests.get() method to fetch product data from the Fake Store API.
- The API returns product information in JSON format.
- The response.text prints the raw JSON response.















---
Title: Python POST Request to Fake Store API
MetaKeywords: python, requests, API, POST request, Fake Store API
Author: Your Name
ContentName: python-post-fakestoreapi
---

# Sending a POST Request to Fake Store API using Python

This script demonstrates how to send a POST request to the Fake Store API using Python's `requests` library.

## Pre-requisite

Before running the code, install the `requests` library using:

```bash
pip install requests
```

# Code 
import requests
import json

# Define the URL to send the request to
url = "https://fakestoreapi.com/products"

# Define the data to send in the request body
data = {
    "title": "test product",
    "price": 13.5,
    "description": "lorem ipsum set",
    "image": "https://i.pravatar.cc",
    "category": "electronic"
}

# Define any headers to include in the request
headers = {"Content-Type": "application/json"}

# Send the POST request
response = requests.post(url, headers=headers, data=json.dumps(data))
json_response = response.json()

print(json_response)


# Explanation 
- The script sends a POST request to the Fake Store API to create a new product.
- The data dictionary contains product details like title, price, description, image, and category.
- The headers specify that the request body is in JSON format.
- The requests.post() method sends the request with the specified URL, headers, and data.
- The response is converted to JSON format and printed.












---
Title: Python PUT Request to Fake Store API
MetaKeywords: python, requests, API, PUT request, Fake Store API
Author: Your Name
ContentName: python-put-fakestoreapi
---

# Sending a PUT Request to Fake Store API using Python

This script demonstrates how to send a `PUT` request to the Fake Store API to update an existing product.

## Pre-requisite

Before running the code, install the `requests` library using:

```bash
pip install requests
```

# Code Example 
```python
import requests
import json

# Define the API endpoint for updating a product
url = 'https://fakestoreapi.com/products/7'

# Define the updated product data
data = {
    "title": "test product",
    "price": 13.5,
    "description": "lorem ipsum set",
    "image": "https://i.pravatar.cc",
    "category": "electronic"
}

# Define headers specifying JSON content
headers = {"Content-Type": "application/json"}

# Send the PUT request to update the product
response = requests.put(url, headers=headers, data=json.dumps(data))

# Check response status and print the result
if response.status_code == 200:
    print('PUT request successful!')
else:
    print('PUT request failed with status code:', response.status_code)

# Print the response JSON
response_json = response.json()
print(response_json)
```

# Explanation
- The script sends a PUT request to update an existing product (Product ID: 7).
- The data dictionary contains updated product details.
- The headers specify that the request body is in JSON format.
- The requests.put() method sends the request with the specified URL, headers, and data.
- If the request is successful (status_code == 200), it prints a success message.
- The response JSON is printed to verify the updated product details.



