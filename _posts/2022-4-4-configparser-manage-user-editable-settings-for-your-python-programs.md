---
layout: post
title: ConfigParser - manage user-editable settings for your Python programs
description: User-configurable settings are important for big applications. They make your application more user-friendly and improve the efficiency of your application. But you may be curious, where and how to store those configurations?
date: 2022-4-4 17:40 +08:00
permalink: /post/000005.html
tags: 
read-time: 2
medium-link:
dev-link: https://dev.to/cycool29/configparser-manage-user-editable-settings-for-your-python-programs-3a88
---

___

## Table of Contents

- [What is ConfigParser?](#what-is-configparser)
- [What does a ConfigParser INI file look like?](#what-does-ini-file-look-like)
- [How to read configs?](#how-to-read-config)
- [how to write configs?](#how-to-write-config)


___


User-configurable settings are important for big applications. They make your application more user-friendly and improve the efficiency of your application.

But you may be curious, **where and how to store those configurations?**

Here I am gonna introduce you **[ConfigParser](https://docs.python.org/3/library/configparser)**, one of the standard libraries in Python 3, which is used to save settings for your Python applications.


<h2><span id="what-is-configparser">What exactly is ConfigParser? 🤔</span></h2>

[ConfigParser](https://docs.python.org/3/library/configparser.html) is a Python 3 standard library (You can install it on Python2 by doing `pip install configparser`) that implements a basic configuration language for Python programs. 
The file format used by ConfigParser is `INI` file, which is similar to the format used by older versions of Microsoft Windows. 

The configuration files are organized into sections, and each section can contain name-value pairs for configuration data. The section names are delimited with `[]` characters. The pairs are separated either with `:` or `=`. Comments start either with `#` or with `;`.


<h2><span id="what-does-ini-file-look-like">What does a ConfigParser INI file look like? 🧐</span></h2>

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
        can_values_be_as_well=True
        does_that_mean_anything_special=False
        purpose=formatting for readability
        multiline_values=are
            handled just fine as
            long as they are indented
            deeper than the first line
            of a value
        # Did I mention we can indent comments, too?
```

That says it all, right?


<h2><span id="how-to-read-config">How to read config from ConfigParser INI file? 📄</span></h2>


This is the sample INI file we are using, name it as `configurations.ini`:

```ini
[DEFAULT]
host=localhost
log=True

[MySQL]
PORT=4000
user=john
passwd=IDontwannatellyouhehe123

[Postgresql]
user=peter
PORT=3000
passwd=AnotherPasswd22223
```


First, we need to import the ConfigParser module, create a ConfigParser object, and read from an `INI` file:

```py
import configparser

configs = configparser.ConfigParser()
configs.read('configurations.ini')
```

Now the configs are initialized as an object. Let's see how we can the values in it:

```py
# Get a value from a section
configs['Postgresql']['user'] # returns: 'peter'

# Assign it to variable
user = configs['Postgresql']['user']
print(user) # returns: 'peter'
```

To check what sections do we have in the INI file, do:

```py
# List all sections in the INI file
configs.sections() # returns: ['MySQL', 'Postgresql']

# See specific section is in the INI file
'MySQL' in configs # returns: True
'NotExistingSection' in configs # returns: False
```

To see all value names in a section:

```py
for key in config['MySQL']:
    print(key)
# Returns: 
# port
# user
# passwd
# host
# log
```

You can also generate a dictionary for values in a section:

```py
configs.items('MySQL') # returns: [('host', 'localhost'), ('log', '1'), ('port', '4000'), ('user', 'john'), ('passwd', 'IDontwannatellyouhehe123')]
```

Now you may confuse - why did the `MySQL` section contains `host` and `log` value? Are you having a typo there?

No no no, that is **magic** in ConfigParser, the values are in the `DEFAULT` section (Note that section titles are cAsE-sEnSiTiVe), which is used to provide default values for **all other sections**.

Well, another thing you may notice is, why the `PORT` value is printed in lowercase letters? 

That's because value names are case-insensitive, and all of them are stored in **lowercase letters**.


One last note here: ALL values in ConfigParser are stored as **strings**.
Therefore, you will need to convert them manually if you want them to be some other data types. There are inbuilt functions for this:

```py
configs['MySQL'].get_boolean('log') # returns: True
configs['MySQL'].get_int('port') # returns: 4000
configs['MySQL'].get_float('port') # returns: 4000.0
```

Tips for `get_boolean()` - the method is case-insensitive and recognizes Boolean values from 'yes'/'no', 'on'/'off', 'true'/'false', and '1'/'0'.


<h2><span id="how-to-write-config">OK... Now I know how to read the configs, but how to write configs to the INI file? ✍</span></h2>

It's SUPER easy, just assign them any string you want them to be, and write to the `configurations.ini`!

Here you go 😎:

```py
# Assign the values you want 
configs['MySQL']['user']='sam'

# Or you can use the `set` method
configs.set(section='Postgresql', option='log', value='False')

# Write it to the file
with open('configurations.ini', 'w') as configfile:
    configs.write(configfile)
```

Done! Now your settings are written in `configurations.ini`.


### What if I want a new section or change the name of a section?

You can use `add_section` to create a new section, like this:

```py
configs.add_section('New Section Name')
```

Well, there is no way to directly **rename** a section. But what you can do is **create a new section**, **copy values to the new section** and **delete the old section**.

```py
# Create a new section
configs.add_section('New Section')

# Copy values to the new section
for item in configs.items('MySQL'):
    configs.set('New Section', item[0], item[1])

# Delete the new section
configs.remove_section('MySQL')
```

Thanks for reading! 😎