---
title: "How to Use the Wolfram Alpha API in Python"
header:
  image: /assets/images/wolfram_alpha_banner.png
  image-alt: "Wolfram|Alpha is perhaps the most advanced knowledge base in the world."
date: 2019-06-27
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

If you're a Computer Scientist, Physicist, Mathematician, or just an analytical person that likes fast, accurate computation with a knowledge base that is unmatched anywhere else in the world, then you've probably worked with WolframAlpha before. Whether for computations, unit conversions, or word definitions, Wolfram seems to have an answer to pretty much every single important question out there, and being able to harness that ability and apply it to our own programs is perhaps one of the most powerful add-ons we can add to an AI or chatbot to enhance responses quickly and easily. In this Quick Tip, we'll be going through how to integrate WolframAlpha into your Python program to instantly beef up your data power.

# API Authentication

## Creating an Account
{% capture notice-2 %}
In the free plan, we get access to 2,000 free queries per month, which so far has been enough for all of my applications (even those with 120,000+ users!). If you're going to be having a small to medium-sized project, the free plan should suffice.
{% endcapture %}
<div class="notice">{{ notice-2 | markdownify }}</div>

First, you'll need to [create a WolframAlpha API account](https://account.wolfram.com/auth/create).

![](/assets/images/wolfram_api_dashboard.png)
<i style="font-size:smaller">The WolframAlpha API Dashboard.</i>

When you verify your email address, you'll be redirected to the dashboard, and you'll be able to proceed to the next step!

## Getting Your API Key
In the dashboard, click the **Get an AppID** button.

<div style="text-align:center"><img src="/assets/images/wolfram_api_createid.png" /></div>
<i style="font-size:smaller">Enter the relevant details for the app.</i>

When you click on **create**, a new API key will be generated for your records. Store this token - it's what you'll need to authenticate with the Wolfram API! Once you write it down, we can move on to the next step - setting up our code to authenticate the key, and writing queries and getting responses!

<div style="text-align:center"><img src="/assets/images/wolfram_api_id.png" /></div>
<i style="font-size:smaller">Keep this API key for your records!</i>

# Installation

First, you'll need to install the `wolframalpha` dependency:
```bash
pip install wolframalpha
```

Next, you'll be able to download or copy the gist I created for interfacing with Wolfram Alpha:
<script src="https://gist.github.com/LeoSaucedo/d1f1d95e9e2f21d265719d511b9bc911.js"></script>

Save this as `wolframapi.py` in the root folder of your Python program. Then, in your main Python file, import the module:
```python
import wolframapi as wolfram
```

# Usage

Once you've imported all the necessary modules, you'll be able to very easily create a new Wolfram Client object and interface with it.

First, instantiate the Wolfram Client as a variable:
```python
client = wolfram.Client("YOUR_CONFIG_KEY_HERE")
```

If no errors are returned, authentication succeeded! Now, you'll be able to easily query responses like so:

```python
print(client.ask("Weather in Tallahassee, FL"));
```

If everything is correct, you should get a detailed, multiline response:
<div style="text-align:center"><img src="/assets/images/wolfram_response_example.png" /></div>
<i style="font-size:smaller">A bit hot, don't you think?</i>

And that's it! You can now customize it to your heart's desire. Feel free to implement any changes to my small API, as well as use this code on your programs of any scale whatsoever!


# Conclusion
With WolframAlpha, you'll be able to create extremely intelligent responses to almost any prompt, from weather, to unit conversions, to Calculus. It's something that I consider essential to all of my AI applications, and sometimes use it for quick conversions so as not to install loads of different modules. I hope you found my Quick Tip interesting, and happy coding!