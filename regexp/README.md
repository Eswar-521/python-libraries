Title: python iterators and generators
MetaDescription: python regular, expressions, code, tutorials
Author: Venkata Bhattaram / tinitiate.com
ContentName: python-regular-expressions
---

# PYTHON REGULAR EXPRESSIONS BASICS
* Regular Expressions are string patterns to search in other strings
* PYTHON Regular Expressions, functionality is provided by the "re" MODULE
* The "re" Module provides all the functions required to enable PYTHONs
  regular expressions
* Regular expressions is all about matching a "pattern" in a "string"
* **search()** function, returns true or false for the string found / not found
* **findall()** function, returns a TUPLE of all occurrences of the pattern
* **sub()** function, This is used to replace parts of strings, with a pattern
* **split()** function, separates a string by space or any delimiter.

```python
# 1) search Function
import re
```
# Create a test string with repeating letters words
- test_string = "The Test string 123 121212 tinitiate TINITIATE a1b2c3"

# Search for pattern: tinitiate (in SMALL LETTERS)
- match = re.search(r'tinitiate', test_string)
```python
if match:
    print("The word 'tinitiate' is found in the string:", "\n", test_string)
else:
    print("The word 'tinitiate' is NOT found in the string:", "\n", test_string)
```
# Search for more complicated patterns, search for 12*, where *
# is wildcard character, match everything else after the pattern "12"
```python
match = re.search(r'12*', test_string)

if match:
    print("The word '12*' is found in the string:", "\n", test_string)
else:
    print("The word '12*' is NOT found in the string:", "\n", test_string)
```
# 2 findall Function
```python
import re
```
# Prints all the WORDS with a SMALL "t" in the test-string
# The options are:
# word with a "t" in between \w+t\w+,
# OR indicated by the PIPE symbol |
# word with a "t" as the last character \w+t,
# OR indicated by the PIPE symbol |
# word with a "t" as the first character t\w+,

# Create a test string with repeating letters words
```python
test_string = "The Test string 123 121212 tinitiate TINITIATE a1b2c3"

all_t = re.findall(r'\w+t\w+|\w+t|t\w+', test_string)
```
# The re.findall returns a TUPLE and we print all the elements looping
# through the tuple
```python
for lpr in all_t:
    print(lpr)
```

# 3 sub Function
```python
import re

# This is used to replace parts of strings, with a pattern
string = "Tinitiate good python examples"

# Replace "good" with "great"
new_string = re.sub("good", "great", string)
print(string)
print(new_string)
```

# 4 split Function
# The split Function splits a string by spaces
```python
import re

words2list = re.split(r's', 'Tinitiate good python examples')
print(words2list)

# Split a Comma Separated String
csv2list = re.split(r',', '1,AAA,2000')
print(csv2list)
```









Title: python regular expressions patterns
MetaKeywords: python, regular expressions patterns, code, tutorials
Author: Venkata Bhattaram / tinitiate.com
ContentName: python-regular-expressions-patterns
---

# PYTHON REGULAR EXPRESSIONS PATTERNS
* Regular Expressions are string patterns to search in other strings
* PYTHON Regular Expressions, functionality is provided by the "re" MODULE
* This program demonstrates and explains various patterns of the 
  regular expressions   
* Common Regular Expression patterns
  * Match any single character using '.'
  * Match start of line '^'
  * Match END of line '$'
  * Match any single character in brackets. [...]
  * Match any single character NOT in brackets. [^...]
  * Match Beginning of entire string '\\A'
  * Match End of entire string except valid final line terminator CAPS(Z)'\\Z'
  * Match 0 or more occurrences of preceding expression. '*'
  * Match 1 or more of the preceding expression. '+'
  * Match 0 or 1 occurrence of preceding expression. '?'
  * Match exactly n number of occurrences of preceding expression. 'exp{n}'
  * Match n or more occurrences of preceding expression. 'exp{n,}'
  * Match exactly n occurrences and m times, of preceding expression.'exp{n,m}'
  * Match X OR Y. 'X|Y'
  * Match word characters '\\w'
  * Match NON word characters '\\W'
  * Match whitespace. Equivalent to [\t\n\r\f]. '\\s'
  * Match NON whitespace. NOT Equivalent to [\t\n\r\f]. '\\S'
  * Match digits. Equivalent to [0-9]. '\\d'
  * Match NON digits. '\\D'

```python
# First STEP to use Regular Expressions in python import the "re" module
import re

# Matches any single character using '.'
TargetString = "ABCDEFG"
RegExPattern = "B(.)D"
ReplaceString = "BXD"
retValue = re.sub(RegExPattern, ReplaceString, TargetString)
print(retValue)  # OUTPUT: ABXDEFG

# Matches START of line '^'
TargetString = " is a line."
RegExPattern = "^"
ReplaceString = "Here"
retValue = re.sub(RegExPattern, ReplaceString, TargetString)
print(retValue)  # OUTPUT: Here is a line.

# Matches END of line '$'
TargetString = "This is a "
RegExPattern = "$"
ReplaceString = "line"
retValue = re.sub(RegExPattern, ReplaceString, TargetString)
print(retValue)  # OUTPUT: This is a line

# Matches any single character in brackets. [...]
TargetString = "SAT SIT SET"
RegExPattern = "S[AI]T"
ReplaceString = "SXT"
retValue = re.sub(RegExPattern, ReplaceString, TargetString)
print(retValue)  # OUTPUT: SXT SXT SET

# Matches any single character NOT in brackets. [^...]
TargetString = "SAT SIT SET"
RegExPattern = "S[^AI]T"
ReplaceString = "SXT"
retValue = re.sub(RegExPattern, ReplaceString, TargetString)
print(retValue)  # OUTPUT: SAT SIT SXT

# Matches Beginning of entire string '\\A'
TargetString = "there was PASCAL"
RegExPattern = "\\A"
ReplaceString = "Once upon a time "
retValue = re.sub(RegExPattern, ReplaceString, TargetString)
print(retValue)  # OUTPUT: Once upon a time there was PASCAL

# Matches End of entire string '\\Z'
TargetString = "there was \n"
RegExPattern = "\\Z"
ReplaceString = "PASCAL."
retValue = re.sub(RegExPattern, ReplaceString, TargetString)
print(retValue)  # OUTPUT: there was \nPASCAL.

# Matches 0 or more occurrences of preceding expression. '*'
TargetString = "JA is Cool, JAJA is Cool"
RegExPattern = "J*"
ReplaceString = "JAVA"
retValue = re.sub(RegExPattern, ReplaceString, TargetString)
print(retValue)

# Matches 1 or more of the preceding expression. '+'
TargetString = "JA is Cool, JAJA is Cool"
RegExPattern = "J+"
ReplaceString = "JAVA"
retValue = re.sub(RegExPattern, ReplaceString, TargetString)
print(retValue)

# Matches X OR Y. 'X|Y'
TargetString = "ERLANG is great"
RegExPattern = "(ERLANG|SCALA)"
ReplaceString = "JAVA"
retValue = re.sub(RegExPattern, ReplaceString, TargetString)
print(retValue)  # OUTPUT: JAVA is great

# Matches word characters '\\w'
TargetString = "Java is great"
RegExPattern = "(\\w)"
ReplaceString = "JAVA"
retValue = re.sub(RegExPattern, ReplaceString, TargetString)
print(retValue)

# Matches whitespace '\\s'
TargetString = "Java is        great"
RegExPattern = "(\\s)"
ReplaceString = "JAVA"
retValue = re.sub(RegExPattern, ReplaceString, TargetString)
print(retValue)

# Matches digits '\\d'
TargetString = "Java is Number 1 !!"
RegExPattern = "(\\d)"
ReplaceString = "one"
retValue = re.sub(RegExPattern, ReplaceString, TargetString)
print(retValue)  # OUTPUT: Java is Number one !!

# Matches NON digits '\\D'
TargetString = "1a2b3"
RegExPattern = "(\\D)"
ReplaceString = "JAVA"
retValue = re.sub(RegExPattern, ReplaceString, TargetString)
print(retValue)  # OUTPUT: 1JAVA2JAVA3
```













Title: python regular expressions multiple patterns
MetaKeywords: python, regular expressions multiple patterns, code, tutorials
Author: Venkata Bhattaram / tinitiate.com
ContentName: python-regular-expressions-multiple
---

# PYTHON REGULAR EXPRESSIONS MULTIPLE PATTERNS IN WORDS OF STRING
* Here we demonstrate use cases for multiple pattern matching in words of 
  a given string.
* Matching String Pattern "Starts with"
* Matching String Pattern "Ends with"
* Matching String Pattern "Has pattern inbetween"
* Matching String with multiple Patterns (Using an Pattern1 OR Pattern2)

```python
import re

my_string = 'Hour01 Min22 VOIDDDDD Sec29 BLAH min3erere Hour32 OTHERS Min33 Hour32'

# String Pattern Match Exact word
Hour32 = re.findall(r'Hour32', my_string)
for word in Hour32:
    print(word)

# Word Pattern Starts with
starting_h = re.findall(r'\bH+\w+.\b', my_string)
for word in starting_h:
    print(word)

# Word Pattern Ends with
ending_2 = re.findall(r'\b\w+2\b', my_string)
for word in ending_2:
    print(word)

# Word Pattern has pattern
has_3 = re.findall(r'\w*3\w*', my_string)
for c in has_3:
    print(c)

# Word with multiple Patterns (Using an Pattern1 OR Pattern2)
has_ou_OI = re.findall(r'\w*OI\w*|\w*ur\w*', my_string)
for c in has_ou_OI:
    print(c)
```

# PYTHON REGULAR EXPRESSIONS MULTIPLE PATTERNS IN STRING
* Here we demonstrate use cases for multiple pattern matching in a given string.
* Matching String Pattern "Starts with"
* Matching String Pattern "Ends with"
* Matching String Pattern "Has pattern inbetween"
* Matching String with multiple Patterns (Using an Pattern1 OR Pattern2)

```python
import re

# String Pattern Match with Exact word
my_string = 'Hour01 Min22 VOIDDDDD Sec29 BLAH min3erere Hour32 OTHERS Min33 Hour32'
Hour32 = re.findall(r'Hour32', my_string)
for word in Hour32:
    print(word)

# String Pattern Match with Exact word using search
test_string = 'Hour01 Min22 VOIDDDDD Sec29 BLAH min3erere Hour32 OTHERS Min33 Hour32'
Hour32 = re.search('Hour32', test_string)
if Hour32:
    print(test_string)

# String Pattern Starts with
starting_h = re.search('H*$', test_string)
if starting_h:
    print(test_string)

# String Pattern Ends with
ending_2 = re.search('2$', test_string)
if ending_2:
    print(test_string)

# String with multiple Patterns (Using an Pattern1 OR Pattern2)
has_OIur = re.search('OI|ur', test_string)
if has_OIur:
    print(test_string)
```













---
Title: Python Iterators and Generators  
MetaDescription: Python regular expressions, code, tutorials  
Author: Venkata Bhattaram / tinitiate.com  
ContentName: python-regular-expressions  
---

# **PYTHON REGULAR EXPRESSIONS BASICS**
- Regular Expressions are **string patterns** used for searching in other strings.
- Python's **Regular Expressions** functionality is provided by the **`re`** module.
- The **`re`** module provides functions required for working with Regular Expressions.
- Regular expressions help in matching a **"pattern"** in a **"string"**.

## **Commonly Used Functions in `re` Module**
1. **`search()`** – Returns `True` or `False` based on whether the pattern is found.
2. **`findall()`** – Returns a **tuple** of all occurrences of the pattern.
3. **`sub()`** – Used to **replace** parts of strings that match a pattern.
4. **`split()`** – Splits a string based on **space** or any delimiter.

---

## **1) `search()` Function**
```python
import re
```
# Create a test string

- test_string = "The Test string 123 121212 tinitiate TINITIATE a1b2c3"

# Search for pattern: 'tinitiate' (lowercase only)
- match = re.search(r'tinitiate', test_string)
```python
if match:
    print("The word 'tinitiate' is found in the string:", "\n", test_string)
else:
    print("The word 'tinitiate' is NOT found in the string:", "\n", test_string)
```
# Search for pattern: '12*' where '*' is a wildcard character

- match = re.search(r'12*', test_string)
```python
if match:
    print("The pattern '12*' is found in the string:", "\n", test_string)
else:
    print("The pattern '12*' is NOT found in the string:", "\n", test_string)
```

# 2 findall() Function
```python
import re

# Test string
test_string = "The Test string 123 121212 tinitiate TINITIATE a1b2c3"

# Find all words with 't' in different positions
all_t = re.findall(r'\w+t\w+|\w+t|t\w+', test_string)

# Print all matches
for word in all_t:
    print(word)
```

# 3 sub() Function
```python
import re

# Sample string
string = "Tinitiate good python examples"

# Replace 'good' with 'great'
new_string = re.sub("good", "great", string)

print(string)      # Original string
print(new_string)  # Modified string
```

# 4 split() Function
```python
import re

# Split string by 's'
words2list = re.split(r's', 'Tinitiate good python examples')
print(words2list)

# Split CSV formatted string
csv2list = re.split(r',', '1,AAA,2000')
print(csv2list)
```






---
Title: Python Regular Expressions - Match Exact Word
MetaKeywords: python, regular expressions, exact word match, pattern matching
Author: Your Name
ContentName: python-regex-exact-word
---

# Python Regular Expressions - Match Exact Word in a String

This script demonstrates how to use Python regular expressions to find words containing the number "3" in a given string.

## Code Example

```python
import re

my_string = 'Hour01 Min22 VOIDDDDD Sec29 BLAH min3erere Hour32 OTHERS Min33 Hour32'

# Word Pattern has pattern
# From "my_string" find all words that have "3" in them
has_3 = re.findall(r'\w*3\w*', my_string)

for c in has_3:
    print(c)
```

