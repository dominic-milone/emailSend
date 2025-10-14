# -*- coding: utf-8 -*-
"""
Created on Sat Oct 11 13:12:15 2025

@author: thedo
"""

from email.message import EmailMessage
import ssl
import smtplib
import requests

## SENDING MAIL ##

email_sender ="temp email"
email_password = "-password-"
email_receiver = "temp email" 

subject = "Test"
body = """
This is a test to see if it works.

"""


em = EmailMessage()
em['From'] = email_sender
em['To'] = email_receiver
em['Subject'] = subject
em.set_content(body)

context = ssl.create_default_context()

with smtplib.SMTP_SSL('smtp.gmail.com', 465, context=context) as smtp:
    smtp.login(email_sender, email_password)
    smtp.sendmail(email_sender, email_receiver, em.as_string())
    
