
## Using SMTPlib
In this example we will be using smtplib

```python
import smtplib
smtp = smtplib.SMTP('smtp.office365.com', 587)
```

Note that this example uses Office 365 as the SMTP server, but you can replace it with your own corporate SMTP server address. You can also use port 465 if your server supports SSL encryption.

Next, you need to authenticate with your username and password using the login method:

```python
smtp.login('user@company.co', 'password')
```

Then, you can compose your email message using the email module. The email module helps you create well-formed email messages with headers, attachments, HTML content, etc.

For example:

```python
from email.message import EmailMessage
msg = EmailMessage()
msg['Subject'] = 'Python email test'
msg['From'] = 'user@company.co'
msg['To'] = 'ron@company.co'
msg.set_content('This is an email sent from Python.')
```

Finally, you can send your message using the send_message method:

```python
smtp.send_message(msg)
smtp.quit()
```

This will send your email message and close the connection with the SMTP server.

## Using EWS

Another option for sending emails using a corporate exchange server is to use the EWS API. EWS stands for Exchange Web Services and is a web service that allows you to access various features of Microsoft Exchange Server such as calendars, contacts, tasks, etc.

To use EWS from Python, you need to install a third-party library called exchangelib. You can install it using pip:

```bash
pip install exchangelib
```

Then, you need to import it and create an Account object with your credentials and server details. For example:

```python
from exchangelib import Account, Credentials, Configuration
creds = Credentials('user@company.co', 'password')
config = Configuration(server='outlook.office365.com', credentials=creds)
account = Account('user@company.co', config=config)
```

Note that this example uses Office 365 as the EWS server, but you can replace it with your own corporate EWS server address.

Next, you can create an EmailMessage object with your message details:

```python
from exchangelib import EmailMessage
msg = EmailMessage(
account=account,
subject='Python email test',
body='This is an email sent from Python.',
to_recipients=['ron@company.co']
)
```

Finally, you can send your message using the send method:

```python
msg.send()
```

This will send your email message using EWS.

## Implementation example
```python
import smtplib, ssl

smtp_server = "smtp.office365.com"
port = 587  # For starttls
sender_email = "youremail@domain.com"
receiver_email = "recipient@domain.com"
password = "<your password here>"
message = """\
Subject: Hi there

This message is sent from Python."""

context = ssl.create_default_context()
with smtplib.SMTP(smtp_server, port) as server:
    server.ehlo()  # Can be omitted
    server.starttls(context=context)
    server.ehlo()  # Can be omitted
    server.login(sender_email, password)
    server.sendmail(sender_email, receiver_email, message)
```

