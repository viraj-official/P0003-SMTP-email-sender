
# Sending Email Using Python — A Step-by-Step Guide

Sending emails programmatically can be a powerful way to automate communication processes. In this article, we will explore how to send emails using Python. We’ll cover setting up an SMTP server, generating app passwords for Gmail, and providing a step-by-step guide to sending emails using the `smtplib` library.

![](https://cdn-images-1.medium.com/max/1000/1*HT2MePLoS0pvF-MLtSoO1A.png)

## Prerequisites:

Before we dive into the code, there are a few prerequisites you need to fulfill:

1.  Create a Gmail account for the sender (e.g., [test@gmail.com](mailto:test@mail.com)).
2.  Generate an App passwords for the sender’s Gmail account. You can follow the instructions provided by Google [here](https://myaccount.google.com/apppasswords).
3.  Create a GitHub repository to host your code. This repository will serve as a version-controlled space to store your email sending code.
4.  Install the necessary libraries. In this case, we’ll be using the `smtplib` library, which is included in Python's standard library.

## Step 1: Importing the Required Libraries

To get started, we need to import the `smtplib` library, as well as other necessary modules from the email library. Add the following lines of code at the beginning of your Python script:
```
import smtplib  
from email.mime.multipart import MIMEMultipart  
from email.mime.text import MIMEText
```

## Step 2: Collecting Email Details

Before running the program, gather the required email details, including:

-   Sender email address (e.g., [test@gmail.com](mailto:test@mail.com))
-   Sender app password (generated from the previous step)
-   Receiver email addresses (separated by commas if there are multiple recipients)
-   Email content (the body of the email)

## Step 3: Creating an SMTP Server

Next, we need to create an SMTP server to establish a connection with the email server. In this case, we’ll be using Gmail’s SMTP server. Add the following code:
```
sender_email = "sender+email@mail.com"  
sender_password = "wabsqstlctgygoad"  
  
server = smtplib.SMTP_SSL('smtp.googlemail.com', 465)  
server.login(sender_email, sender_password)
```
## Step 4: Sending Emails

To send emails, we’ll use a loop to iterate through the receiver email addresses and send emails one by one. Here’s the code:
```
for receiver_email in receiver_emails:  
    msg = MIMEMultipart('alternative')  
    msg['Subject'] = "Test mail"  
    msg['From'] = sender_email  
    msg['To'] = receiver_email  
  
    html = """  
              <h1>Hello world</h1>  
          """  
    msg.attach(MIMEText(html, 'html'))  
    server.sendmail(sender_email, receiver_email, msg.as_string())
```
In the above code, we create a `MIMEMultipart` object and set the subject, sender, and recipient fields. We attach an HTML body to the email using the `MIMEText` object. Finally, we use the `sendmail` method of the SMTP server to send the email.

## Step 5: Stopping the Server

After sending all the emails, don’t forget to stop the server by adding the following code:
```
server.quit()
```
## Step 6: Testing the Code

Now that you have the complete code, it’s time to test it. Replace the placeholder email addresses, such as the sender email, sender app password, and receiver email addresses, with your own email details. You can also modify the email content to suit your needs.

After making the necessary changes, run the code and check your email inbox. You should see the test email with the subject “Test mail” and the “Hello world” message in the HTML format.

![](https://cdn-images-1.medium.com/max/1000/1*vseeplnvRh7omOdLKD8Atw.png)

By following the steps outlined in this article and referring to the example code in the GitHub repository, you’ll be able to send emails programmatically using Python.

## The full code will look something like this:
```
import smtplib  
  
from email.mime.multipart import MIMEMultipart  
from email.mime.text import MIMEText  
  
sender_email = "sender+email@mail.com"  
sender_password = "wabsqstlctgygoad"  
receiver_emails = ["receiver+email1@mail.com","receiver+email2@mail.com"]  
  
server = smtplib.SMTP_SSL('smtp.googlemail.com', 465)  
server.login(sender_email, sender_password)  
  
for receiver_email in receiver_emails:  
    msg = MIMEMultipart('alternative')  
    msg['Subject'] = "Test mail"  
    msg['From'] = sender_email  
    msg['To'] = receiver_email  
    html = """  
        <h1>Hello world</h1>  
    """  
    msg.attach(MIMEText(html, 'html'))  
    server.sendmail(sender_email, receiver_email, msg.as_string())  
  
server.quit()
```
In this article, we covered the process of sending emails using Python. We discussed the prerequisites, importing the required libraries, collecting email details, creating an SMTP server, and sending emails using the `smtplib` library. By following the steps outlined here, you can automate your email communication effectively.

## Reference

GitHub repo : [https://github.com/viraj-official/P0003-SMTP-email-sender](https://github.com/viraj-official/P0003-SMTP-email-sender)

## Contact

For any questions or suggestions, feel free to reach out:

-   Name: Viraj Shakya Samaranayake
-   Email: [virajofficialinfo@gmail.com](http://virajofficialinfo@gmail.com/)
-   GitHub: [github.com/viraj-official](https://github.com/viraj-official)
-   Linkedin: [Linkedin/virajofficial](https://www.linkedin.com/in/virajofficial/)
