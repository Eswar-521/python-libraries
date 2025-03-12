---
Title: Python Avro File Handling
MetaKeywords: python, avro, serialization, deserialization, schema, binary file
Author: Your Name
ContentName: python-avro-file-handling
---

# Python Avro File Handling

## Overview

- **Apache Avro** is a data serialization system that provides rich data structures and compact, fast serialization.
- Avro stores data in a binary format along with its schema.
- The **Avro schema** is defined in JSON format.

---

## Prerequisites

Before running the script, install the `avro-python3` package:

```bash
pip install avro-python3
```
## Code Example
```python
import uuid
import avro.schema
import json
from avro.datafile import DataFileReader, DataFileWriter
from avro.io import DatumReader, DatumWriter
```
# Define Avro binary file path
```python
avro_binary_file = "E:\\code\\python\\avro\\users.avro"
```
# Define the Avro schema in JSON format
```python
avro_schema = """{
    "namespace": "example.avro",
    "type": "record",
    "name": "User",
    "fields": [
        {"name": "name", "type": "string"},
        {"name": "favorite_number", "type": ["int", "null"]},
        {"name": "favorite_color", "type": ["string", "null"]}
    ]
}"""
```
# Parse the Avro schema
```python
write_schema = avro.schema.Parse(json.dumps(json.loads(avro_schema)))
```
# Create an Avro data file writer
```python
writer = DataFileWriter(open(avro_binary_file, "wb"), DatumWriter(), write_schema)
writer.close()
```
# Explanation
## 1 Import Required Modules
- uuid: Generates unique identifiers.
- avro.schema: Parses the Avro schema.
- json: Handles JSON encoding and decoding.
- avro.datafile: Reads and writes Avro data files.
- avro.io: Handles Avro data encoding and decoding.

- ## 2 Define the Avro Schema

- The schema defines a User record with three fields:
name (string)
- favorite_number (integer or null)
- favorite_color (string or null)


## 3 Parse the Schema

- Convert the schema JSON into an Avro schema object.
## 4 Write the Avro File
- Create a DataFileWriter to write data into the Avro file.
- The file is created but does not yet contain records.










---
Title: Python XML File Generation
MetaKeywords: python, xml, etree, elementtree, parsing, file writing
Author: Your Name
ContentName: python-xml-file-generation
---

# Python XML File Generation

## Overview

- This script demonstrates how to **generate an XML file** using Python's `xml.etree.ElementTree` module.
- The generated XML contains structured data, including **training courses** and **code descriptions**.

---

## Prerequisites

- Python 3.x installed

No additional libraries are required as `xml.etree.ElementTree` is part of Python’s standard library.

---

## Code Example

```python
import xml.etree.ElementTree as ET

# Generate the XML File

# Create Root Element
root_element = ET.Element("tinitiate")

# Create 'training' sub-element
training_element = ET.SubElement(root_element, "training")

# Add 'course' sub-elements under 'training'
course_element1 = ET.SubElement(training_element, "course")
course_element1.text = 'JAVA'
course_element2 = ET.SubElement(training_element, "course")
course_element2.text = 'UNIX'
course_element3 = ET.SubElement(training_element, "course")
course_element3.text = 'PERL'
course_element4 = ET.SubElement(training_element, "course")
course_element4.text = 'PYTHON'

# Add 'code' sub-elements with attributes
code_element1 = ET.SubElement(root_element, "code")
code_element1.set("id", str(1))
code_element1.text = 'Python XML Parsing'

code_element2 = ET.SubElement(root_element, "code")
code_element2.set("id", str(2))
code_element2.text = 'Python File Writing'

# Convert XML structure to a string
xml_data = ET.tostring(root_element, encoding='unicode')

# Print the generated XML
print(xml_data)

# Write the Generated XML to a file
output_file_path = "E:\\python-master\\media\\test-data-OUT.xml"
with open(output_file_path, "w") as myfile:
    myfile.write(xml_data)
```


# Explanation 
  # 1 Create Root Element (<tinitiate>)

- This is the main container for the XML document.
# 2 Add a <training> Section

- Contains multiple <course> elements representing different training topics.
# 3 Add a <code> Section

- Contains multiple <code> elements with an id attribute and a text description.
# 4 Convert XML to String

- The ET.tostring() function converts the XML structure into a string for output.
# 5 Write XML to a File

- The generated XML is saved as test-data-OUT.xml at the specified location.













---
Title: Python XML Parsing using minidom
MetaKeywords: python, xml, minidom, parsing, DOM, xml parsing
Author: Your Name
ContentName: python-xml-parsing-minidom
---

# Python XML Parsing using `minidom`

## Overview

- This script demonstrates how to **parse an XML file** using Python's `xml.dom.minidom` module.
- It extracts **tags, elements, attributes**, and **reads the content** within the XML file.

---

## Prerequisites

- Python 3.x installed
- An XML file to parse (e.g., `test-data.xml`)

---

## Code Example

```python
from xml.dom import minidom

# Create a DOM object by reading the XML file
# Note: Change the path based on the XML file location
xmldoc = minidom.parse('E:/python-master/media/003-python-modules/test-data.xml')

# Print the document node and name of the first child tag
print(xmldoc.nodeName)
print(xmldoc.firstChild.tagName)

# Extract Tag and its Elements by Tag Name

# Extract the "tinitiate" element and its children
tinitiate_elements = xmldoc.getElementsByTagName("tinitiate")

# Loop through a Tag Element and Read Underlying Elements / Attributes

# Iterate through the "tinitiate" elements
for tinitiate_element in tinitiate_elements:

    # Extract "training" elements
    training_elements = tinitiate_element.getElementsByTagName("training")

    # Get values from the "training" elements
    for training_element in training_elements:

        # Extract "course" elements
        course_elements = training_element.getElementsByTagName("course")

        # Print the values of the "course" elements
        for course_element in course_elements:
            # Each course element has one child node at the lowest level, so use index ZERO
            print(course_element.childNodes[0].nodeValue)

    # Reading Attributes in the "code" Elements
    

    # Extract "code" elements
    code_elements = xmldoc.getElementsByTagName("code")

    # Print the total count of "code" elements
    print("Total Count of 'CODE' elements in XML: ", len(code_elements))

    # Loop through the "code" elements
    for code_element in code_elements:

        # Print the attributes of each "code" element
        print(code_element.attributes["id"].value)
        
        # Print the node value of each "code" element
        print(code_element.childNodes[0].nodeValue)
```

# Explanation

## 1 Load XML File into DOM

- The minidom.parse() function loads the XML file into a DOM object.
## 2 Extract Root Element Information

- xmldoc.nodeName and xmldoc.firstChild.tagName print the root node details.
## 3 Extract Specific Tags and Their Children

- The script extracts elements using getElementsByTagName().
- It loops through training and course elements, printing course names.
## 4 Read Attributes from Elements

- It fetches all <code> elements and prints their id attribute values.


















---
Title: Python XML Parsing using SAX
MetaKeywords: python, xml, SAX, parsing, xml.sax, event-driven XML parsing
Author: Your Name
ContentName: python-xml-parsing-sax
---

# Python XML Parsing using `xml.sax`

## Overview

- This script demonstrates how to **parse an XML file** using Python's `xml.sax` (Simple API for XML).
- `xml.sax` is an **event-driven** parser that reads XML data **sequentially** without loading the entire document into memory.

---

## Prerequisites

- Python 3.x installed
- An XML file to parse (e.g., `test-data.xml`)

---

## Code Example

```python
import xml.sax

# Define a class that inherits from xml.sax.ContentHandler
class TIContentHandler(xml.sax.ContentHandler):
    # Constructor method
    def __init__(self):
        # Call the constructor of the base class
        xml.sax.ContentHandler.__init__(self)
        # Initialize a variable to keep track of the current element being parsed
        self.CurrentData = ""
        
    # This method is called every time a new element is encountered in the XML file
    def startElement(self, name, attrs):
        # Print the name of the element
        print("startElement :" + name)
        # Update the value of the current data variable
        self.CurrentData = name
        # If the current element is "code", print its "id" attribute value
        if name == "code":
            print("\tattribute id=" + attrs.getValue("id"))
    
    # This method is called every time character data is encountered inside an element
    def characters(self, content):
        # If the current element is "course", print its value
        if self.CurrentData == "course":
            print(content)
        # If the current element is "code", print its value
        if self.CurrentData == "code":
            print(content)

    # This method is called every time the end of an element is encountered
    def endElement(self, name):
        # Print the name of the element
        print("endElement:"  + name)


# This function processes an XML file using the SAX parser and the TIContentHandler class
def SAXprocessXML(sourceFileName):
  # Open the XML file for reading
  source = open(sourceFileName)
  # Parse the XML file using the SAX parser and the TIContentHandler class
  xml.sax.parse(source, TIContentHandler())

# Call the SAXprocessXML function with the path to the XML file as an argument
# Note: Change the folder to where the file is located
SAXprocessXML('E:/python-master/media/003-python-modules/test-data.xml')
```



# Explanation
1. Creating a Custom SAX Handler
- The class TIContentHandler inherits from xml.sax.ContentHandler.
Implements three key methods:
- `startElement(self, name, attrs):`
- Called when a new XML element is encountered.
- Prints the element name and attributes (if available).
- `characters(self, content):`
- Called when character data is encountered inside an element.
- Prints the content of <course> and <code> elements.
- `endElement(self, name):`
- Called when an element ends.
- Prints the closing element name.
2. Parsing XML using SAX
- The SAXprocessXML(sourceFileName) function:
- Opens the XML file.
- Passes it to xml.sax.parse() along with TIContentHandler.
- Sample XML File (test-data.xml)














---
Title: Python XML Validation using XSD
MetaKeywords: python, xml, xsd, xmlschema, validation, logging
Author: Your Name
ContentName: python-xml-validation-xsd
---

# Python XML Validation using XSD

## Overview

- This script demonstrates how to **validate an XML file** against an **XSD schema** using Python's `xmlschema` module.
- Validation ensures that the XML data conforms to the defined structure and rules in the **XSD file**.

---

## Prerequisites

- Python 3.x installed
- Install the `xmlschema` module:
```python
  pip install xmlschema
```
# Code Example 
```python
import logging
import xmlschema

# Load the XSD schema file
xsd_file = 'E:/python-master/media/003-python-modules/product.xsd'
try:
    schema = xmlschema.XMLSchema(xsd_file)
except Exception as e:
    print(f"Failed to load XSD schema file: {e}")
    raise

# Load the XML data file
xml_file = 'E:/python-master/media/003-python-modules/product.xml'
try:
    with open(xml_file, 'r') as f:
        xml_data = f.read()
except Exception as e:
    print(f"Failed to load XML data file: {e}")
    raise

# Validate the XML data against the XSD schema
is_valid = schema.is_valid(xml_data)

# Log the validation result
if is_valid:
    print("The XML data is valid according to the XSD schema.")
else:
    print("The XML data is not valid according to the XSD schema.")
    print(schema.validate(xml_data))
```

## Explanation 
- # 1 Loading the XSD Schema
- The script attempts to load the XSD file (product.xsd) using xmlschema.XMLSchema(xsd_file).
If the file is missing or invalid, an error message is displayed.
- # 2. Loading the XML File
- Reads the XML file (product.xml).
- If the file is missing or unreadable, an error message is displayed.
# 3. Validating the XML Against the XSD
- The is_valid(xml_data) method checks whether the XML conforms to the schema.
- If validation fails, schema.validate(xml_data) returns error messages.


