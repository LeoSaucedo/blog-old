---
title: "How to Monitor Your Program's Status with Pushbullet"
header:
  image: /assets/images/pushbullet.jpg
  image-alt: "Pushbullet is an essential app for Android and iOS power users."
date: 2019-06-18
toc: true
toc_label: "Table of Contents"
toc_icon: "list-alt"
categories:
  - Quick Tip
tags:
  - Python
  - Tutorial
  - Coding
---

[Pushbullet](https://www.pushbullet.com/) has always been a service essential to my tech life. It allows you to send and receive SMS messages from any android device within just about any internet-connected device, allows you to sync Android notifications with chrome or Windows, and even lets you easily transfer files to and from your phone and computer. I always knew Pushbullet had an API, but I'd never put two and two together to successfully make a notification system every time my Discord bot, Rikka, gets an error or restarts. In this quick tip, I'll walk you through how I added Pushbullet notifications that notify me of the error, traceback, and timestamp.

# Requirements

- Python 3
- A Pushbullet account
- Basic Knowledge of Python and `pip`

# Setup

## Python Installation

First, install the Python module [Pushbullet.py](https://github.com/rbrcsk/pushbullet.py).

## Obtaining the Pushbullet API Key

Then, you'll need to get your API Key from Pushbullet. This is actually a really simple process.

Navigate to your [Pushbullet Settings](https://www.pushbullet.com/#settings) and click on _Create Access Token_. You'll need to copy the key and save it somewhere.

![](/assets/images/Pushbullet_Access_Key.JPG)
<i style="font-size:smaller">The Pushbullet Access Key Token screen</i>

```bash
pip install pushbullet.py
```

# Quick Examples

## Pushing Text Notes

In order to test your API key and make sure that everything works, you'll first want to run a couple of tests in the python console.

First, import Pushbullet and authenticate using the access key you got in the previous step:

```python
from pushbullet import Pushbullet
pb = Pushbullet(api_key)
```

Now, you can easily push a text note using:

```python
pb.push_note("Quick Tip", "This is the best blog ever!")
```

And, the output should show in your Pushbullet window, like this:

![](/assets/images/push_example.JPG)

## Pushing Files

Pushing files is a bit of a more complex process, but it's still really easy to learn!

First, we'll create a small text file and write something to it:

```bash
touch hi.txt
echo "Hello World!" > hi.txt
```

Next, we'll push it to Pushbullet:

```python
with open("hi.txt", "r") as file:
  # Open the log as a file
  # and push it to yourself.
  file_data = pb.upload_file(file, "hi.txt")
pb.push_file(**file_data)
```

You should receive this in your Pushbullet:

![](/assets/images/pb_file_test.JPG)

If you've gotten up to this point, you're halfway there! Now, let's look at how to fit this into our current programs.

# Pushbullet Error Handling

## API Approach

Since my use case was with my Discord bot, [Rikka](https://cgsphoto.com/rikka-bot/), I was able to use the [Discord.py API](https://github.com/Rapptz/discord.py) to find a function, `on_error`, that would catch all of the errors that occurred during the runtime of the program. When I overrode it, I was able to not only print the error to the console, but also create a text log with all of the errors, and notify myself:

```python
@client.event
async def on_error(self, event_method, *args, **kwargs):
  # Print out a message indicating there was an error.
  print("Error.txt for details...")
  print(file=sys.stderr) # Print out any error details.
  # Create or append to error log if it exits.
  f = open("error.txt", "a+")
  f.write("===== ERROR SUMMARY =====\n")
  # Add timestamp of the error occurring.
  f.write("Timestamp: " + str(datetime.datetime.now().strftime("%d.%b %Y %H:%M:%S")) + "\n")
  # Write the exception that occurred.
  f.write("Exception in {}".format(event_method) + "\n")
  f.write("===== TRACEBACK =====\n")
  # Print out the traceback of the error.
  f.write(traceback.format_exc() + "\n\n")

  # Once the file is created and all of the information
  # is printed, push it to Pushbullet.
  with open("error.txt", "r") as file:
    # Open the error log as a file
    # and push it to yourself.
    file_data = pb.upload_file(f, "error.txt")
  push = pb.push_file(**file_data)
```

## Try-Catch Approach

If you don't have the fortune to be working with a great API that gives you an error-handling API, you can _sort of_ write one yourself by placing everything in a try-catch:

```python
try:
  yourFunctionHere()
except:
  # Print out a message indicating there was an error.
  print("Error.txt for details...", ERROR)
  print(file=sys.stderr) # Print out any error details.
  # Create or append to error log if it exits.
  f = open("error.txt", "a+")
  f.write("===== ERROR SUMMARY =====\n")
  # Add timestamp of the error occurring.
  f.write("Timestamp: " + str(datetime.datetime.now().strftime("%d.%b %Y %H:%M:%S")) + "\n")
  # Write the exception that occurred.
  f.write("Exception in {}".format(event_method) + "\n")
  f.write("===== TRACEBACK =====\n")
  # Print out the traceback of the error.
  f.write(traceback.format_exc() + "\n\n")

  # Once the file is created and all of the information
  # is printed, push it to Pushbullet.
  with open("error.txt", "r") as file:
    # Open the error log as a file
    # and push it to yourself.
    file_data = pb.upload_file(f, "error.txt")
  push = pb.push_file(**file_data)
```

No matter what approach you take, you should get a handy little file in your Pushbullet every time an error is thrown:

![](/assets/images/push_error.JPG)

# Conclusion
And that's it! You've connected your Pushbullet account to your error handling in Python. Whether you're a SysAdmin, or a bot developer like me, you will now be able to be notified whenever an error is caused, and get a nice text message with timestamp and a log to see what could have caused the problem. Since implementing this change, I have become much less paranoid, and now I can live my life knowing my code works in the background. Thanks for reading, and happy coding!