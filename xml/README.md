## Writing an Avro File in Python

### Overview
This Python script demonstrates how to create and write an Avro file using the `avro` library. It defines a schema, parses it, and initializes a writer for storing data in an Avro binary file.

### Code

```python
import uuid
import avro.schema
import json
from avro.datafile import DataFileReader, DataFileWriter
from avro.io import DatumReader, DatumWriter

## Define the Avro binary file path
l_avro_binary_file = "E:\\code\\python\\avro\\users.avro"

# Define the Avro schema as a JSON string
l_schema = """{
    "namespace": "example.avro",
    "type": "record",
    "name": "User",
    "fields": [
         {"name": "name", "type": "string"},
         {"name": "favorite_number", "type": ["int", "null"]},
         {"name": "favorite_color", "type": ["string", "null"]}
     ]
}"""

# Parse the schema
write_schema = avro.schema.Parse(json.dumps(json.loads(l_schema)))

# Initialize the Avro writer
writer = DataFileWriter(open(l_avro_binary_file, "wb"), DatumWriter(), write_schema)

# Close the writer (No data is written yet)
writer.close()
```

### Explanation
## Importing Required Modules
 -  `uuid:` Generates unique identifiers (not used in this example).
 -  `avro.schema:` Handles Avro schema parsing.
 -  `avro.datafile.DataFileReader` & `DataFileWriter:` Read and write Avro files
 -  `json:` Used to parse and manipulate JSON data.
 -  `avro.io.DatumReader` & `DatumWriter:` Serialize and deserialize Avro data.
  
## Defining the Avro Binary File Path

- The file path E:\\code\\python\\avro\\users.avro specifies where the Avro data will be stored.

## Defining the Avro Schema
- The schema is written in JSON format and describes the structure of the records:
- `name:` A required string field.
- `favorite_number:` An optional integer field (nullable).
- `favorite_color:` An optional string field (nullable).


## Parsing the Schema

- `json.loads(l_schema):` Converts the schema string into a JSON object.
- `json.dumps(...):` Converts the JSON object back into a string.
- `avro.schema.Parse(...):` Parses the schema into an Avro schema object.
  
## Initializing the Avro Writer
- `DataFileWriter(open(l_avro_binary_file, "wb"), DatumWriter(), write_schema):`
- Opens the file in write-binary `(wb)` mode.
- Uses `DatumWriter()` to handle record serialization.
- Uses the parsed schema to define the data structure.
## Closing the Writer
- `writer.close():` Closes the writer to finalize the file.
- Note: No data has been written yet.

## Next Steps
- To write records, use writer.append(data) before closing the writer.
- To read Avro files, use DataFileReader.









## Generating and Writing an XML File Using Python

### Overview
This Python script demonstrates how to generate an XML structure using the `xml.etree.ElementTree` module. It creates an XML document with structured elements and writes it to a file.

### Code

```python
import xml.etree.ElementTree as ET

# Generate the XML File
# Create Root Element
root_element = ET.Element("tinitiate")

# Create a 'training' Sub-element
training_element = ET.SubElement(root_element, "training")

# Add Course Elements under 'training'
course_element1 = ET.SubElement(training_element, "course")
course_element1.text = 'JAVA'

course_element2 = ET.SubElement(training_element, "course")
course_element2.text = 'UNIX'

course_element3 = ET.SubElement(training_element, "course")
course_element3.text = 'PERL'

course_element4 = ET.SubElement(training_element, "course")
course_element4.text = 'PYTHON'

# Create 'code' elements with attributes
code_element1 = ET.SubElement(root_element, "code")
code_element1.set("id", str(1))
code_element1.text = 'Python XML Parsing'

code_element2 = ET.SubElement(root_element, "code")
code_element2.set("id", str(2))
code_element2.text = 'Python File Writing'

# Convert the XML structure to a string
mydata = ET.tostring(root_element, encoding='unicode')

# Print the generated XML
print(mydata)

# Write the Generated XML to a File
myfile = open("E:\\python-master\\media\\test-data-OUT.xml", "w")
myfile.write(mydata)
myfile.close()
```

## Explanation 
## Importing the `xml.etree.ElementTree` Module
- This module provides methods to create and manipulate XML data.

## Creating the Root Element

- `ET.Element("tinitiate")` creates the root `<tinitiate>` element.

## Adding a Sub-element for Training

- `ET.SubElement(root_element, "training")` creates a child element `<training>`.

## Adding Course Elements under <training>

- Each `<course>` element is added as a child of `<training>`.
- `.text` assigns values `(JAVA, UNIX, PERL, PYTHON)`.
## Adding Code Elements with Attributes

- `ET.SubElement(root_element, "code")` creates `<code>` elements.

- `set("id", str(1))` assigns an id attribute.
- `text` contains the description.
## Converting the XML Structure to a String

- `ET.tostring(root_element, encoding='unicode')` converts the XML into a string format.
## Writing XML to a File

- Opens the file in write mode and saves the XML content.









## Parsing an XML File Using `xml.dom.minidom` in Python

### Overview
This Python script demonstrates how to parse an XML file using `xml.dom.minidom`. It reads an XML document, extracts elements by tag names, and retrieves both element values and attributes.

### Code

```python
from xml.dom import minidom
```
### Create a DOM object by reading the XML file
### Change the file path to the correct location
```python
xmldoc = minidom.parse('E:/python-master/media/003-python-modules/test-data.xml')
```
### Print the document node and name of the first child tag
```python
print(xmldoc.nodeName)
print(xmldoc.firstChild.tagName)
```

### Extract Tag and its elements By Tag Name

### Extract the TINITIATE element and its children from the XML document
```python
tinitiate_elements = xmldoc.getElementsByTagName("tinitiate")
```

### Loop through a Tag Element and read underlying Elements / Attributes
### Since we know the "tinitiate" element has children, we use a loop
```python
for tinitiate_element in tinitiate_elements:
# Extract the "training" elements
training_elements = tinitiate_element.getElementsByTagName("training")
# Get values from the "training" elements list
for training_element in training_elements:
# Extract the "course" elements within "training"
course_elements = training_element.getElementsByTagName("course")
# Print values of the "course" elements
for course_element in
```

## Explanation 
### Importing the `xml.dom.minidom` Module

- This module provides a lightweight way to parse and navigate XML documents.
### Reading an XML File

- `minidom.parse('E:/python-master/media/003-python-modules/test-data.xml')` loads the XML file.
### Extracting Document and First Child Information

- `nodeName` retrieves the document node name.
- `firstChild` tagName retrieves the first element's tag name.
### Extracting Elements by Tag Name

- `getElementsByTagName("tinitiate")` finds all <tinitiate> elements.
- `getElementsByTagName("training")` finds <training> elements inside <tinitiate>.
- `getElementsByTagName("course")` finds <course> elements inside <training>.
### Retrieving and Printing Course Names

- Loops through each <course> element.
- Extracts and prints nodeValue (the text inside the tag).
### Reading Attributes in the <code> Element

- `getElementsByTagName("code")` extracts <code> elements.
- `attributes["id"]`.value retrieves the id attribute.
- `childNodes[0]`.nodeValue retrieves the text inside <code>.











## Parsing an XML File Using `xml.sax` in Python

## Overview
This Python script demonstrates how to parse an XML file using `xml.sax`. It defines a custom content handler class that processes XML elements, extracts data, and prints attribute values.

## Code

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

# Called when an element starts
def startElement(self, name, attrs):
print("startElement :" + name)
self.CurrentData = name
# Print the "id" attribute if the element is "code"
if name == "code":
print("\tattribute id=" + attrs.getValue("id"))
    
# Called when text content is found within an element
def characters(self, content):
if self.CurrentData == "course":
print(content)
if self.CurrentData == "code":
print(content)
# Called when an element ends
def endElement(self, name):
 print("endElement:"  + name)


# Function to process an XML file using the SAX
def SAXprocessXML(sourceFileName):
# Open the XML file for reading
source = open(sourceFileName)
# Parse the XML file using the SAX parser
xml.sax.parse(source, TIContentHandler())

# Call the function with the XML file path
# Note: Update the path to match your XML file location
SAXprocessXML('E:/python-master/media/003-python-modules/test-data.xml')
```


## Explanation

## Importing xml.sax

- `xml.sax` provides an event-driven XML parsing approach.
## Creating a Custom Content Handler (TIContentHandler)

- Inherits from `xml.sax.ContentHandler.`
- Handles three main SAX events:
- `startElement(self, name, attrs)`: Called at the beginning of an XML element.
- `characters(self, content)`: Called when text content is found.
- `endElement(self, name)`: Called at the end of an XML element.
## Extracting Data

- `startElement():` Prints the element name and extracts attributes.
- `characters():` Prints text content inside course and code elements.
- `endElement()`: Prints the closing tag.
## Processing XML File with SAXprocessXML()

- Opens the XML file.
- Calls `xml.sax.parse()` to parse the file using `TIContentHandler`








# XML Validation Using XSD Schema in Python

# Overview
This Python script demonstrates how to validate an XML file against an XSD schema using the `xmlschema` module. It loads both files, checks their validity, and logs the results.

# Code

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

# Explanation

# Import Required Modules

- `logging:` Provides logging capabilities (not fully used in this example).
xmlschema: Handles XML validation against XSD.
## Load the XSD Schema

- The script attempts to load product.xsd.
- If it fails, an exception is caught and printed.
## Load the XML Data

- The script reads product.xml.
- If the file cannot be read, an exception is raised.
## Validate XML Against XSD

- `The schema.is_valid(xml_data)` function checks if the XML conforms to the XSD.
- If valid, it prints a success message.
- If invalid, it prints an error message and the validation errors.



