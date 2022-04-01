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

I think the example from the [official docs](https://docs.python.org/3/library/configparser.html#supported-ini-file-structure) is the perfect one:

```
[Simple Values]
key=value
spaces in keys=allowed
spaces in values=allowed as well
spaces around the delimiter = obviously
you can also use : to delimit keys from values

[All Values Are Strings]
values like this: 1000000
or this: 3.14159265359
are they treated as numbers? : no
integers, floats and booleans are held as: strings
can use the API to get converted values directly: true

[Multiline Values]
chorus: I'm a lumberjack, and I'm okay
    I sleep all night and I work all day

[No Values]
key_without_value
empty string value here =

[You can use comments]
# like this
; or this

# By default only in an empty line.
# Inline comments can be harmful because they prevent users
# from using the delimiting characters as parts of values.
# That being said, this can be customized.

    [Sections Can Be Indented]
        can_values_be_as_well = True
        does_that_mean_anything_special = False
        purpose = formatting for readability
        multiline_values = are
            handled just fine as
            long as they are indented
            deeper than the first line
            of a value
        # Did I mention we can indent comments, too?
```

That says it all, right?


<h2><span id="how-to-read-config">How to read config from ConfigParser INI file? 📄</span></h2>


This is the sample INI file we are using:

```
[]
```


First, we need to import the ConfigParser module, create a ConfigParser object, and read from a INI file:

```python
import configparser

configs = configparser.ConfigParser()
configs.read('configurations.ini')
```

Now the configs are initialize as an object. Let's see how we can the values in it:

```python
# Get a whole section
configs['Section Title'] # returns: {'Entry1': 'Value1', 'Entry2': 'Value2', 'Entry3': 'Value3'}

# Get a value from a section
configs['Section Title']['Value Name']
```