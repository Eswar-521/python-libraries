## Python Email with Attachments using smtplib
This script demonstrates how to send an email with multiple attachments using Python's `smtplib` and `email` modules.

### Steps:
1. Read Gmail credentials from a configuration file (`config.ini`).
2. Set up the sender and receiver email addresses.
3. Attach multiple files (`.txt`, `.gif`, `.mp3`) to the email.
4. Send the email using SMTP over SSL.

```python
import smtplib
from email.mime.multipart import MIMEMultipart
from email.mime.text import MIMEText
from email.mime.base import MIMEBase
from email import encoders
import configparser
import os
```
# Directory where the files are stored
```python
data_dir = 'E:/python-master/media/003-python-modules/'
```
# Load the configuration from file
```python
config = configparser.ConfigParser()
config.read('config.ini')
```
# Get the Gmail username and password from the configuration
```python
gmail_user = config.get('Gmail', 'username')
gmail_password = config.get('Gmail', 'password')
```

# Create sender and receiver
```python
attachment_sender = 'tinitiate.training@gmail.com'
attachment_receiver = ['tinitiate@gmail.com', 'tinitiate.training@gmail.com']
```

# Create message object
```python
attachment_msg = MIMEMultipart()
attachment_msg['From'] = attachment_sender
attachment_msg['To'] = ", ".join(attachment_receiver)
attachment_msg['Subject'] = 'Python Attachment Test Email'
```

# List of files to attach
```python
files = [data_dir + "myfile.txt", data_dir + "image1.gif", data_dir + "music1.mp3"]
```
# Attach each file
```python
for f in files:
    part = MIMEBase('application', "octet-stream")
    part.set_payload(open(f, "rb").read())
    encoders.encode_base64(part)
    part.add_header('Content-Disposition', 'attachment; filename="{0}"'.format(os.path.basename(f)))
    attachment_msg.attach(part)
```

# Create an SMTP connection
```python
s = smtplib.SMTP_SSL('smtp.gmail.com', 465)
s.login(gmail_user, gmail_password)
s.ehlo()
s.sendmail(attachment_sender, attachment_receiver, attachment_msg.as_string())
s.quit()
```



# Sending Emails with Python (SMTP)

## Import Required Modules
```python
# Import smtplib for sending emails
import smtplib, os

# Import modules for email formatting
from email.mime.multipart import MIMEMultipart
from email.mime.text import MIMEText

# Import modules for attachments
from email.mime.base import MIMEBase
from email import encoders

# Import configparser for reading configurations
import configparser
import os
```

## Load Configuration from config.ini
```python
# Load the configuration from file
config = configparser.ConfigParser()
config.read('config.ini')

# Get the Gmail username and password from the configuration
gmail_user = config.get('Gmail', 'username')
gmail_password = config.get('Gmail', 'password')
```

```python
# Define sender and receiver email addresses
sender = 'tinitiate.training@gmail.com'
receiver = ['tinitiate@gmail.com', 'tinitiate.training@gmail.com']
```
# Create message object
```python
msg = MIMEMultipart('alternative')
msg['From'] = sender
msg['To'] = ", ".join(receiver)
msg['Subject'] = "This is a TINITIATE test EMAIL"
```

# Establish SMTP connection and login
```python
s = smtplib.SMTP_SSL('smtp.gmail.com', 465)
s.ehlo()
s.login(gmail_user, gmail_password)

# Send the email
s.sendmail(sender, receiver, msg.as_string())

# Close SMTP connection after sending
s.quit()
```

## Configuration File (config.ini) Example
```python
[Gmail]
username = your-email@gmail.com
password = your-app-password
```

-**Note:**

- Replace your-email@gmail.com with your actual Gmail address.
- Replace your-app-password with a valid App Password (not your Gmail login password).






## Sending Emails with Attachments in Python

This Python script demonstrates how to send emails with both **plain text** and **HTML content** using the `smtplib` and `email` modules. It retrieves Gmail credentials from a configuration file (`config.ini`) and sends an email to multiple recipients.

### Required Libraries
- `smtplib` - To connect with the SMTP server
- `email.mime` - To format emails with text, HTML, and attachments
- `configparser` - To read email credentials from a configuration file

### **Python Code:**
```python
import smtplib
from email.mime.multipart import MIMEMultipart
from email.mime.text import MIMEText
import configparser
import os
```
# Load configuration from file
```python
config = configparser.ConfigParser()
config.read('config.ini')
```
# Get Gmail credentials
```python
gmail_user = config.get('Gmail', 'username')
gmail_password = config.get('Gmail', 'password')
```

# Define sender and receiver
```python
sender = 'tinitiate.training@gmail.com'
receiver = ['tinitiate@gmail.com', 'tinitiate.training@gmail.com']
```

# Create a MIME message
```python
msg = MIMEMultipart('alternative')
msg['From'] = sender 
msg['To'] = ", ".join(receiver)
msg['Subject'] = "This is a TINITIATE test EMAIL"
```
# Email body (plain text and HTML)
```python
plain_text = "This is plain text"
html_text = """\
<html>
  <body>
    <h1>This is a TEST EMAIL FROM TINITIATE</h1>
    <p>
     Welcome to Python training from TINITIATE.COM
    </p>
  </body>
</html>
"""
```
# Attach plain text and HTML parts
```python
plain_message = MIMEText(plain_text, 'plain')
html_message = MIMEText(html_text, 'html')
msg.attach(plain_message)
msg.attach(html_message)
```

# Establish SMTP connection and send email
```python
s = smtplib.SMTP_SSL('smtp.gmail.com', 465)
s.ehlo()
s.login(gmail_user, gmail_password)
s.sendmail(sender, receiver, msg.as_string())
s.quit()
```

# Steps to Run 

## 1 Create a config.ini file in the same directory:
```python
[Gmail]
username = your-email@gmail.com
password = your-app-password
```

## 2 Run the script:
```python
python send_email.py
```








