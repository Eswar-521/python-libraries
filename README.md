# 🕰️ DateTime Assignment: Finding the Day of February 9th for the Last 10 Years

## 📌 **Objective**
This Python script determines the **day of the week** for **February 9th** over the past **10 years**.

---

## 📝 **Code Breakdown**

### 1️⃣ **Importing the Required Module**
```python
import datetime
```
- The datetime module provides functions to work with dates and times.
  
- ### 2️⃣ Defining the Fixed Date Format
```python
dtm = "0209"
```
- Stores the month (02 for February) and the day (09) as a string.
  
- ### 3️⃣ Getting the Current Year
```python
today = datetime.datetime.today()
year = today.strftime("%Y")
year = int(year)
```
- datetime.datetime.today() retrieves the current date.
- strftime("%Y") extracts the current year as a string.
- int(year) converts the year into an integer for calculations.
  

- ### 4️⃣ Looping Over the Last 10 Years
```python
for c in range(11):  # Loop for 11 iterations (Current Year + Last 10 Years)
```
- The loop runs 11 times (including the current year).
- Each iteration calculates the day of the week for February 9th of a specific year.
  
- ### 5️⃣ Generating the Date String
```python
dt_str = dtm + str(year)  # "0209" + "2024" → "02092024"
print(dt_str)
```
- Concatenates dtm (fixed "0209") with year to form a date string in MMDDYYYY format.

- ### 6️⃣ Converting String to Date and Printing the Day Name
```python
t1 = datetime.datetime.strptime(dt_str, "%m%d%Y")
print(t1.strftime("%A"))
```
- strptime(dt_str, "%m%d%Y") converts the string into a datetime object.
- strftime("%A") extracts the full weekday name (e.g., "Monday").

- ## 7️⃣ Updating the Year for the Next Iteration
```python
year = year - 1
```
- Decreases the year by 1 to move to the previous year.
- #  Expected Output
For example, if the script runs in 2025, it will output:

-mathematica
- Copy
- Edit
- 02092025
- Sunday
- 02092024
- Friday
- 02092023
- Thursday
- ...
- 02092015
- Monday






# ⏰ Timezone Conversion in Python Using `pytz`

## 📌 **Objective**
This Python script demonstrates how to:
- Convert a **given date and time** into different time zones using the `pytz` library.
- Localize a datetime object to specific time zones.

---

## 📝 **Code Breakdown**

### 1️⃣ **Importing Required Modules**
```python
import datetime
import pytz
```
- datetime is used to handle date and time operations.
- pytz is a library for working with timezone conversions.

## 2️⃣ Defining Timezones
```python
tz1 = "Asia/Qyzylorda"
tz2 = "America/Caracas"
tz3 = "W-SU"
```
- tz1: Asia/Qyzylorda (Kazakhstan Time)
- tz2: America/Caracas (Venezuela Time)
- tz3: W-SU (Old Soviet Union timezone, now mostly equivalent to Europe/Moscow)

## 3️⃣ Defining a Date and Time String
```python
str_datetime = '2019-05-15 12:00:00'
l_date_time = datetime.datetime.strptime(str_datetime, '%Y-%m-%d %H:%M:%S')
```
- str_datetime is a string representation of the datetime.
- strptime() converts this string into a datetime object.
## 4️⃣ Assigning Timezones and Localizing the Datetime
🏙️ Localizing to tz1 (Asia/Qyzylorda)
```python
tzd1 = pytz.timezone(tz1)
d1_tz = tzd1.localize(l_date_time)
print(d1_tz)
```
- Creates a timezone object using pytz.timezone(tz1).
- localize() assigns Asia/Qyzylorda's timezone to l_date_time.
- ## 🌎 Localizing to tz2 (America/Caracas)
```python
tzd2 = pytz.timezone(tz2)
d2_tz = tzd2.localize(l_date_time)
print(d2_tz)
```
- Converts l_date_time to America/Caracas timezone.
- ## 🏛️ Localizing to tz3 (W-SU)
```python
tzd3 = pytz.timezone(tz3)
d3_tz = tzd3.localize(l_date_time)
print(d3_tz)
```
- Converts l_date_time to W-SU timezone.
- ## Expected Output
- If you run this script, you will see output similar to:

- Copy
- Edit
- 2019-05-15 12:00:00+06:00
- 2019-05-15 12:00:00-04:30
- 2019-05-15 12:00:00+03:00
- Asia/Qyzylorda is UTC+6.
- America/Caracas is UTC-4:30.
- W-SU (Moscow Time) is UTC+3.
  






# Working with Timezones in Python using `pytz`

## 📌 Import Required Modules
```python
import datetime
import pytz
```
## 🌍 Creating a Date with a Specific Timezone
- Python allows you to work with different timezones using the pytz module. Below, we create  a datetime object and assign it the Eastern Standard Time (EST) timezone.

```python
# Define a string representation of a datetime
str_datetime = '2019-05-15 12:00:00'

# Convert the string to a datetime object
l_date_time = datetime.datetime.strptime(str_datetime, '%Y-%m-%d %H:%M:%S')

# Assign the datetime to the EST TimeZone
EST_TimeZone = pytz.timezone('America/New_York')
est_date = EST_TimeZone.localize(l_date_time)

# Print results
print('EST Date:', est_date)
print('EST Date Timezone:', est_date.tzinfo)
```
## 🔄 Converting a DateTime from One Timezone to Another
Let's take a date in Eastern Standard Time (EST) and convert it to GMT/UTC and Indian Standard Time (IST).

```python
# Define a new datetime string
str_datetime = '2023-04-19 12:00:00'

# Convert the string to a datetime object
l_date_time = datetime.datetime.strptime(str_datetime, '%Y-%m-%d %H:%M:%S')

# Assign the datetime to EST timezone
EST_TimeZone = pytz.timezone('America/New_York')
est_date = EST_TimeZone.localize(l_date_time)

# Print EST Date
print('EST Date:', est_date)
print('EST Date Timezone:', est_date.tzinfo)

# Convert EST Date to GMT / UTC
GMT_TimeZone = pytz.timezone('GMT')
gmt_date = est_date.astimezone(GMT_TimeZone)

# Print GMT Date
print('GMT Date:', gmt_date)
print('GMT Date Timezone:', gmt_date.tzinfo)

# Convert EST Date to Indian Standard Time (IST)
IN_TimeZone = pytz.timezone('Asia/Kolkata')
india_date = est_date.astimezone(IN_TimeZone)

# Print IST Date
print('India Date:', india_date)
print('India Date Timezone:', india_date.tzinfo)
```






# 🕒 Working with Dates and Times in Python

Python provides powerful `datetime` and `timedelta` modules to perform date and time calculations such as:
- Subtracting dates
- Finding differences in days, hours, minutes, and seconds
- Adding time to a date

---

## 📌 Import Required Modules
```python
import datetime
from datetime import timedelta  
```
## 📅 Subtracting Dates
- Let's define two dates and calculate the difference in various units.
```python
# Define two date strings
D1_str = "2016-06-24"
D2_str = "2016-07-21"

# Convert string to datetime object
D1 = datetime.datetime.strptime(D1_str, "%Y-%m-%d")
D2 = datetime.datetime.strptime(D2_str, "%Y-%m-%d")

# Print original dates
print("D1:", D1)
print("D2:", D2)

# Calculate the absolute difference in days
diff_in_days = abs(D2 - D1).days
print("Difference in Days:", diff_in_days)

# Calculate the difference in hours, minutes, and seconds
date_diff = D2 - D1
diff_in_hours = date_diff.total_seconds() / 3600
diff_in_minutes = date_diff.total_seconds() / 60
diff_in_seconds = date_diff.total_seconds()

# Print time differences
print("Difference in Hours:", diff_in_hours)
print("Difference in Minutes:", diff_in_minutes)
print("Difference in Seconds:", diff_in_seconds)
```
## ➕ Adding to Date-Time
- Let's take a date-time and add days, hours, minutes, and seconds to it.
```python
# Define a date-time string
D3_str = '2016-07-21 12:30:22'
formatADT = "%Y-%m-%d %H:%M:%S"

# Convert string to datetime object
D3 = datetime.datetime.strptime(D3_str, formatADT)
print("D3 DATE-TIME:", D3)

# Add 5 Days using timedelta
newDate = D3 + timedelta(days=5)
print("D3 + 5 Days:", newDate.strftime(formatADT))

# Add 5 Hours using timedelta
newDate = D3 + timedelta(hours=5)
print("D3 + 5 Hours:", newDate.strftime(formatADT))

# Add 5 Minutes using timedelta
newDate = D3 + timedelta(minutes=5)
print("D3 + 5 Minutes:", newDate.strftime(formatADT))

# Add 5 Seconds using timedelta
newDate = D3 + timedelta(seconds=5)
print("D3 + 5 Seconds:", newDate.strftime(formatADT))
```






# 📅 Working with Dates in Python

Python's `datetime` module provides useful methods to work with dates, extract specific parts of a date, and get the current timestamp.

---

## 🕒 1. Get Today's Date
```python
from datetime import date
```
# Get the current date
today = date.today()
print(today) 
- Example Output: 2025-03-12

## 🔍 2. Extract Specific Date Components

```python
# Print day, month, and year
print(today.day)    # Day (e.g., 12)
print(today.month)  # Month (e.g., 3 for March)
print(today.year)   # Year (e.g., 2025)

# Get the weekday (Monday = 0, Sunday = 6)
print(today.weekday())  
```
- `today.day`: Returns the day of the month.
- `today.month`: Returns the month number.
- `today.year`: Returns the year.
- `today.weekday()`: Returns the day of the week as an  integer `(0 = Monday, 6 = Sunday)`.
  
## ⏳ 3. Get the UNIX Epoch Time
```python
import time
```
# Get the current UNIX timestamp
```python
print(time.time())  # Example Output: 1707520502.8757482
```
- time.time(): Returns the number of seconds since the - UNIX epoch (January 1, 1970, 00:00:00 UTC).
- This is useful for timestamps, time calculations, and performance measurement.








# 📅 Python `strftime()`: Convert Date and Time to String

Python's `strftime()` method is used to format date and time into readable string representations.

---

## 📝 **Format Specifiers in `strftime()`**
| Specifier | Description |
|-----------|-------------|
| `%a`  | Abbreviated weekday name (e.g., Mon) |
| `%A`  | Full weekday name (e.g., Monday) |
| `%b`  | Abbreviated month name (e.g., Jan) |
| `%B`  | Full month name (e.g., January) |
| `%c`  | Localized date and time representation |
| `%d`  | Day of the month (01-31) |
| `%f`  | Microseconds (000000-999999) |
| `%H`  | Hour (24-hour format, 00-23) |
| `%I`  | Hour (12-hour format, 01-12) |
| `%j`  | Day of the year (001-366) |
| `%m`  | Month (01-12) |
| `%M`  | Minutes (00-59) |
| `%p`  | AM/PM indicator |
| `%S`  | Seconds (00-61) |
| `%U`  | Week number (Sunday as first day) |
| `%w`  | Weekday as a number (0=Sunday, 6=Saturday) |
| `%W`  | Week number (Monday as first day) |
| `%x`  | Localized date representation |
| `%X`  | Localized time representation |
| `%y`  | Year without century (00-99) |
| `%Y`  | Year with century (e.g., 2025) |
| `%z`

## ## ⏳ **Convert Date to String Using `strftime()`**
```python
import datetime

# Get the current date and time
today = datetime.datetime.today()

# Format YYYYMMDD
format1 = "%Y%m%d"
s = today.strftime(format1)
print(s)  # Example Output: 20250312

# Format DD-MON-YYYY
format2 = "%d-%b-%Y"
s = today.strftime(format2)
print(s)  # Example Output: 12-Mar-2025

# Format DD-MON-YYYY HH24:MI:SS
format3 = "%d-%b-%Y %H:%M:%S"
s = today.strftime(format3)
print(s)  # Example Output: 12-Mar-2025 14:30:45









## 📅 Python `strftime()`: Convert DATE and TIME to String

Python’s `strftime()` function allows formatting date and time into string representations.

---

### 📝 Format Specifiers in `strftime()`
| Specifier | Description |
|-----------|-------------|
| `%a`  | Abbreviated weekday name (e.g., Mon) |
| `%A`  | Full weekday name (e.g., Monday) |
| `%b`  | Abbreviated month name (e.g., Jan) |
| `%B`  | Full month name (e.g., January) |
| `%c`  | Localized date and time representation |
| `%d`  | Day of the month (01-31) |
| `%f`  | Microseconds (000000-999999) |
| `%H`  | Hour (24-hour format, 00-23) |
| `%I`  | Hour (12-hour format, 01-12) |
| `%j`  | Day of the year (001-366) |
| `%m`  | Month (01-12) |
| `%M`  | Minutes (00-59) |
| `%p`  | AM/PM indicator |
| `%S`  | Seconds (00-61) |
| `%U`  | Week number (Sunday as first day) |
| `%w`  | Weekday as a number (0=Sunday, 6=Saturday) |
| `%W`  | Week number (Monday as first day) |
| `%x`  | Localized date representation |
| `%X`  | Localized time representation |
| `%y`  | Year without century (00-99) |
| `%Y`  | Year with century (e.g., 2025) |
| `%z`  | UTC offset |
| `%Z`  | Time zone name |
| `%%`  | A literal `%` character |

---

### ⏳ Convert Date to String Using `strftime()`

```python
import datetime

# Get the current date and time
today = datetime.datetime.today()

# Format YYYYMMDD
format1 = "%Y%m%d"
s = today.strftime(format1)
print(s)  # Example Output: 20250312

# Format DD-MON-YYYY
format2 = "%d-%b-%Y"
s = today.strftime(format2)
print(s)  # Example Output: 12-Mar-2025

# Format DD-MON-YYYY HH24:MI:SS
format3 = "%d-%b-%Y %H:%M:%S"
s = today.strftime(format3)
print(s)  # Example Output: 12-Mar-2025 14:30:45

# Print Full Weekday Name
s = today.strftime("%A")
print(s)  # Example Output: Tuesday
```






## ⏳ Python `time` Module: Date Comparisons and Checking

- Python's `datetime` module allows us to compare dates easily. Below is a demonstration of how to compare two dates.

---

### 📌 Date Comparison Example

```python
import datetime

# Define two dates as strings
D1_str = "2016-06-24"
D2_str = "2016-07-24"

# Convert string dates to datetime objects
D1 = datetime.datetime.strptime(D1_str, "%Y-%m-%d")
D2 = datetime.datetime.strptime(D2_str, "%Y-%m-%d")

# Print the converted dates
print("D1:", D1)
print("D2:", D2)

# Compare the dates
if D1 > D2:
    print(D1, "is Greater than", D2)
else:
    print(D1, "is Less than", D2)
```







## 📆 Python `datetime`: Add & Subtract Dates/Times using `timedelta`

Python's `timedelta` allows us to **add** or **subtract** dates and times easily. Below is a demonstration:

---

### ⏳ Subtracting Dates

```python
import datetime
from datetime import timedelta  

# Define two dates as strings
D1_str = "2016-06-24"
D2_str = "2016-07-21"

# Convert string dates to datetime objects
D1 = datetime.datetime.strptime(D1_str, "%Y-%m-%d")
D2 = datetime.datetime.strptime(D2_str, "%Y-%m-%d")

print("D1:", D1)
print("D2:", D2)

# Difference in days
diff_in_days = abs(D2 - D1).days
print("Difference in Days:", diff_in_days)

# Difference between Dates
date_diff = D2 - D1

# Convert difference to hours, minutes, and seconds
diff_in_hours = date_diff.total_seconds() / 3600
diff_in_minutes = date_diff.total_seconds() / 60
diff_in_seconds = date_diff.total_seconds()

print("Difference in Hours:", diff_in_hours)
print("Difference in Minutes:", diff_in_minutes)
print("Difference in Seconds:", diff_in_seconds)
```

## ⏩ Adding to Date & Time
```python
# Define a datetime string
D3_str = '2016-07-21 12:30:22'
formatADT = "%Y-%m-%d %H:%M:%S"

# Convert string to datetime object
D3 = datetime.datetime.strptime(D3_str, formatADT)
print("D3 DATE-TIME:", D3)

# Subtract 5 days
newDate = D3 + timedelta(days=-5)
print("D3 - 5 Days:", newDate.strftime(formatADT))

# Add 5 days
newDate = D3 + timedelta(days=5)
print("D3 + 5 Days:", newDate.strftime(formatADT))

# Add 5 hours
newDate = D3 + timedelta(hours=5)
print("D3 + 5 Hours:", newDate.strftime(formatADT))

# Add 5 minutes
newDate = D3 + timedelta(minutes=5)
print("D3 + 5 Minutes:", newDate.strftime(formatADT))

# Add 5 seconds
newDate = D3 + timedelta(seconds=5)
print("D3 + 5 Seconds:", newDate.strftime(formatADT))
```






## 🔄 Python Generators: `yield` Function

Generators allow us to **iterate over data lazily**, improving memory efficiency. Below are different generator demonstrations.

---

### 📌 Basic Generator Example

```python
# Function converted to a generator using yield
def GeneratorDemo():
    yield 22
    yield 33
    yield 44

# Call the function as an iterator
myIter = GeneratorDemo()

# Print values one by one using __next__()
print(myIter.__next__())  # Output: 22
print(myIter.__next__())  # Output: 33
print(myIter.__next__())  # Output: 44
```


## 🔁 Using yield Inside a Loop
```python
# Generator function using a loop
def GeneratorDemo1():
    for c1 in [1, 2, 3, 4, 5]:
        yield c1

# Call the function as an iterator
myIter = GeneratorDemo1()

# Print values one by one
print(myIter.__next__())  # Output: 1
print(myIter.__next__())  # Output: 2
print(myIter.__next__())  # Output: 3
print(myIter.__next__())  # Output: 4
print(myIter.__next__())  # Output: 5
```

## 🔢 Dynamic Generator: Even & Odd Numbers
```python
# Create a dynamic generator
def EvenOddNum(MAX):
    num = 0
    while num < MAX:
        num += 1
        if num % 2 != 0:
            yield str(num) + " is Odd Number"
        else:
            yield str(num) + " is Even Number"

# Call the function as an iterator
myIter = EvenOddNum(5)

# Print generated values
print(myIter.__next__())  # Output: 1 is Odd Number
print(myIter.__next__())  # Output: 2 is Even Number
print(myIter.__next__())  # Output: 3 is Odd Number
print(myIter.__next__())  # Output: 4 is Even Number
print(myIter.__next__())  # Output: 5 is Odd Number

# This will raise a StopIteration error as MAX is 5
print(myIter.__next__())  # ❌ ERROR: No more values to yield
```





## Python DateTime TimeZone
* Working with TimeStamps and TimeZones
* The convenient way to work with TimeZones is to use the module `import pytz`
* Here we demonstrate the creation of a date at a timezone and conversion of a date to 
  various timezones using `astimezone`
* Here is a full list of TimeZone values that can be used:  
  [List of tz database time zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)

```python
import datetime
import pytz
```
# CREATE DATE AT A TIMEZONE
```python
str_datetime = '2019-05-15 12:00:00'
_date_time = datetime.datetime.strptime(str_datetime, '%Y-%m-%d %H:%M:%S')
```
# Assign current Date to EST TimeZone
```python
EST_TimeZone = pytz.timezone('America/New_York')
est_date = EST_TimeZone.localize(l_date_time)

print('est_date', est_date)
print('est_date timezone', est_date.tzinfo)
```

# CONVERT A DATETIME AT A TIMEZONE TO ANOTHER TIMEZONE
```python
str_datetime = '2019-12-15 12:00:00'
_date_time = datetime.datetime.strptime(str_datetime, '%Y-%m-%d %H:%M:%S')
print(l_date_time)
```

# Assign current Date to EST TimeZone
```python
EST_TimeZone = pytz.timezone('America/New_York')
est_date = EST_TimeZone.localize(l_date_time)

print('est_date', est_date)
print('est_date timezone', est_date.tzinfo)
```

# Convert EST Date to GMT / UTC using "astimezone"
```python
GMT_TimeZone = pytz.timezone('GMT')
gmt_date = est_date.astimezone(GMT_TimeZone)

print('gmt_date', gmt_date)
print('gmt_date timezone', gmt_date.tzinfo)
```
# Convert EST Date to INDIA TIMEZONE
```python
IN_TimeZone = pytz.timezone('Asia/Kolkata')
india_date = est_date.astimezone(IN_TimeZone)

print('india_date', india_date)
print('india_date timezone', india_date.tzinfo)
```







## Python datetime strptime(): Convert String to DATE and TIME
* Use `strptime()` to convert string to date
* `%a`  Locale’s abbreviated weekday name.
* `%A`  Locale’s full weekday name.
* `%b`  Locale’s abbreviated month name.
* `%B`  Locale’s full month name.
* `%c`  Locale’s appropriate date and time representation.
* `%d`  Day of the month as a decimal number [01,31].
* `%f`  Microsecond as a decimal number [0,999999], zero-padded on the left.
* `%H`  Hour (24-hour clock) as a decimal number [00,23].
* `%I`  Hour (12-hour clock) as a decimal number [01,12].
* `%j`  Day of the year as a decimal number [001,366].
* `%m`  Month as a decimal number [01,12].
* `%M`  Minute as a decimal number [00,59].
* `%p`  Locale’s equivalent of either AM or PM.
* `%S`  Second as a decimal number [00,59].
* `%U`  Week number of the year (Sunday as the first day of the week).
* `%w`  Weekday as a decimal number [0 (Sunday), 6].
* `%W`  Week number of the year (Monday as the first day of the week).
* `%x`  Locale’s appropriate date representation.
* `%X`  Locale’s appropriate time representation.
* `%y`  Year without century as a decimal number [00,99].
* `%Y`  Year with century as a decimal number.
* `%z`  UTC offset in the form +HHMM or -HHMM.
* `%Z`  Time zone name (empty string if the object is naive).
* `%%`  A literal '%' character.

```python
import datetime
```

# Convert String to Date
```python
l_date_time_string = "2016-06-24"
l_datetime = datetime.datetime.strptime(l_date_time_string, "%Y-%m-%d")
print(l_datetime)
```

# Convert String to Date Time in format: DD-MON-YYYY HH24:MI:SS
```python
l_date_string1 = "2016-06-24 16:00:00"
format4 = "%Y-%m-%d %H:%M:%S"
t1 = datetime.datetime.strptime(l_date_string1, format4)
print("t1", t1)
```
# Get Today's Date Time in format4
```python
today = datetime.datetime.today()
s = today.strftime(format4)
```
# Convert string s back to date time in format4
t2 = datetime.datetime.strptime(s, format4).date()
print("t2", t2)

