---
layout: post
title: ConfigParser - manage user-editable settings for your application in Python
description: 
date: 2022-3-31 10:00 +08:00
permalink: /post/000005.html
tags: 
read-time: 2
---


User-configurable settings are important for big applications. They make your application more user-friendly, and improve the efficient of your application.

But you may curious, **where and how to store those configurations?**

Here I am gonna introduce you **[ConfigParser](https://docs.python.org/3/library/configparser)**, one of standard libraries in Python3, which is used to save settings for your Python applications.


<h2><span id="what-is-configparser">What exactly is ConfigParser? 🤔</span></h2>

[ConfigParser](https://docs.python.org/3/library/configparser.html) is a Python3 standard library (You can install it on Python2 by doing `pip install configparser`) which implements a basic configuration language for Python programs. 
The file format used by ConfigParser is `INI` file, which is similar to the format used by older versions of Microsoft Windows. 

The configuration files are organized into sections, and each section can contain name-value pairs for configuration data. The section names are delimited with `[]` characters. The pairs are separated either with `:` or `=`. Comments start either with `#` or with `;`.


<h2><span id="how-does-ini-file-looks-like">How does a ConfigParser INI file looks like? 🧐</span></h2>

Here is an example of ConfigParser INI file for Harry potter Series Movies (Yes, I am really a fan of Harry Potter, LOL):

```ini
[Harry Potter and the Sorcerer's Stone]
release_date = November 22, 2001
director = Chris Columbus
duration_minutes = 212
budget_millions = 125



```