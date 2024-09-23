```python
# Libary Imports
import string
import random
import smtplib
from email.mime.multipart import MIMEMultipart
from email.mime.text import MIMEText
from getpass import getpass



# OTP Generation

OTP = "".join([random.choice(string.digits) for i in range(6)])


# Creating Email Content

sub = "OTP Verification"
body = """
THIS OTP is sent as a part of small python project
Don't worry
Enter this OTP as verification system purposeam
""" + OTP
msg = MIMEMultipart()
msg["Subject"] = sub
msg.attach(MIMEText(body,"plain"))
message = msg.as_string()

# Sender Email And Password Check

smtp_server = "smtp.gmail.com"
port = 587
sender_email = "amitkumarpaul720@gmail.com"
password ="ufoo fqfj cggu qfom"
server = smtplib.SMTP(smtp_server,port)
server.starttls()

# login Check Of Sender

server.login(sender_email,password)
receiver_email = input("Enter your Email : ")

# Sending Email With Otp

server.sendmail(sender_email, receiver_email, message)
print("Otp Sent to your Email please Check your email")

# Otp Validation

def authenticate():
    i = input("\n\nEnter your Otp: ")
    if i == OTP:
        print("OTP verified Succesfully")
    else:
        for k in range(3):
            print("Invalid OTP\nYou have {} attempts left ".format(3 - k))
            i = input("Enter your OTP again:")
            if i == OTP:
                print("OTP verified Succesfully")
                break
        if k == 2 and i!=OTP:
            print("Reached Maximum Attempts")

authenticate()
# Content For Another Email

subb = "OTP Verified " + u'\u263A'
bod = """
OTP Verified Succesfully
Thank  You \u263A
"""
m = MIMEMultipart()
m["Subject"] = subb
m.attach (MIMEText(bod,"plain"))
mes = m.as_string()

server.sendmail(sender_email,receiver_email,mes)

```


```python

```
