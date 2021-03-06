---
layout: post
title: Pi-Apps - The most powerful app store for Raspberry Pi
description: While ago, I got my first Raspberry Pi. Like most of the Linux users (specifically, Raspberry Pi users) transferring from Windows, I am getting crazy with these questions.
author: cycool29
date: 2022-02-25 12:45:00 +08:00
permalink: /post/000003.html
tags: raspberrypi beginners appstore raspbian
read-time: 5
medium-link: https://medium.com/@cycool29/pi-apps-the-most-powerful-app-store-for-raspberry-pi-e3e651623247
dev-link: https://dev.to/cycool29/pi-apps-the-most-powerful-app-store-for-raspberry-pi-105l
---

______

## Table of Contents


- [What is Pi-Apps?](#what-is-pi-apps)
- [How to install Pi-Apps?](#how-to-install)
- [How to launch Pi-Apps?](#how-to-launch)
- [How to update Pi-Apps?](#how-to-update)
- [Basic usage](#basic-usage)

______


While ago, I got my first Raspberry Pi. Like most of the Linux users (specifically, Raspberry Pi users) transferring from Windows, I am getting crazy with these questions:

> How to install emoji font on my pi?

> Why Discord is not supporting ARM architecture?

> The built-in screenshot tool really sucks... 

> Where can I install ZOOM?????

I found a bunch of tutorials online, but most of them are **outdated**, and even **broke my system**.

And... I found Pi-Apps! 🤩

[![Botspot/pi-apps - GitHub](https://gh-card.dev/repos/Botspot/pi-apps.svg)](https://github.com/Botspot/pi-apps)

Now I am able to install emoji fonts, a usable Discord client, a powerful screenshot tool, and even ZOOM Meeting client!

<br>
<h2><span id="what-is-pi-apps">What is Pi-Apps? 🤔</span></h2>

Pi-Apps is a well-maintained collection of app installation-scripts that you can run with one click. 

In short, it is an **app store**.

![Main window](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/9pabl9zu2vxpnetg85ow.png)
 

Unlike the tutorials or blog posts on the web, Pi-Apps has a beautiful GUI, constantly maintained scripts, bug reporting system, and [a cheerful community](https://discord.gg/RXSTvaUvuu)! 

Pi-Apps now serves over **1,000,000** people and hosts [nearly 200 apps](https://github.com/Botspot/pi-apps/wiki/Apps-List).

<br>
<h2><span id="how-to-install">Looks cool... How can I install it on my Pi? ⏬</span></h2>

Here is the one-liner command 😎 :

```bash
wget -qO- https://raw.githubusercontent.com/Botspot/pi-apps/master/install | bash
```

### Supported systems:

- [Raspberry Pi OS](https://www.raspberrypi.com/software/operating-systems/) (32-bit/64-bit) (Buster/Bullseye)
   - Fully supported.    
<br>

- [Twister OS](https://twisteros.com/download.html)
   - Fully supported, preinstalled.    
<br>

- Kali Linux, Ubuntu, Ubuntu Mate, any other Debian-based ARM OS
   - Pi-Apps should mostly work but you may encounter errors for some apps.    
<br>

- Android, ChromeOS, non-ARM, non-Debian operating systems
   - Not supported. Your mileage may vary.    

**To install Pi-Apps manually** if you prefer to see what happens under the hood
 
```
git clone https://github.com/Botspot/pi-apps ~/pi-apps
~/pi-apps/install
```
**To uninstall Pi-Apps**
This will not uninstall any apps that you installed through Pi-Apps.

```
~/pi-apps/uninstall
```
<br>
<h2><span id="how-to-launch">Now I have it installed... How to launch it? 🤟</span></h2>

- From the start menu on Raspberry Pi OS:
   - Accessories -> Pi Apps
- Use the terminal-command: `pi-apps`
- Run Pi-Apps from its directory: `~/pi-apps/gui`

<br>
<h2><span id="how-to-update">How To Update Pi-Apps? ⏫</span></h2>

- Pi-apps will automatically check for updates on boot and display a notification to update.
- To manually run the updater, use this command: `~/pi-apps/updater gui`
- It also supports a cli interface: `~/pi-apps/updater cli`

<br>
<h2><span id="basic-usage">Basic usage 🔧</span></h2>

Pi-Apps is very easy to use!  
- This is the **main window**.  
![main window](https://github.com/Botspot/pi-apps/raw/master/icons/screenshots/main%20window.png?raw=true)  
  - ![icon](https://github.com/Botspot/pi-apps/raw/master/icons/screenshots/buttons/search.png?raw=true) Search for apps.
  - ![icon](https://github.com/Botspot/pi-apps/raw/master/icons/screenshots/buttons/info.png?raw=true) Open the selected category. (you can also double-click on the category)

<br>

- Opening a category will reveal a **list of apps**:  
![app list](https://github.com/Botspot/pi-apps/raw/master/icons/screenshots/app%20list.png?raw=true)  
  - ![icon](https://github.com/Botspot/pi-apps/raw/master/icons/screenshots/buttons/back.png?raw=true) Go back to the main list of categories.
  - ![icon](https://github.com/Botspot/pi-apps/raw/master/icons/screenshots/buttons/install.png?raw=true) Install the selected app.
  - ![icon](https://github.com/Botspot/pi-apps/raw/master/icons/screenshots/buttons/uninstall.png?raw=true) Uninstall the selected app.
  - ![icon](https://github.com/Botspot/pi-apps/raw/master/icons/screenshots/buttons/info.png?raw=true) See more details about the app. (see **details window** below)

<br>

- This is the **details window**:  
![details](https://github.com/Botspot/pi-apps/raw/master/icons/screenshots/details%20window.png?raw=true)  
  - ![icon](https://github.com/Botspot/pi-apps/raw/master/icons/screenshots/buttons/back2.png?raw=true) Go back to the list of apps.
  - ![icon](https://github.com/Botspot/pi-apps/raw/master/icons/screenshots/buttons/scripts.png?raw=true) View the shell-scripts responsible for installing or uninstalling the selected app.
  - ![icon](https://github.com/Botspot/pi-apps/raw/master/icons/screenshots/buttons/edit.png?raw=true) Modify the app's description, icons, or scripts. (This button is hidden unless you enable it in Settings)
  - ![icon](https://github.com/Botspot/pi-apps/raw/master/icons/screenshots/buttons/install.png?raw=true) Install the selected app.
  - ![icon](https://github.com/Botspot/pi-apps/raw/master/icons/screenshots/buttons/uninstall.png?raw=true) Uninstall the selected app.
  - ![icon](https://github.com/Botspot/pi-apps/raw/master/icons/screenshots/buttons/credits.png?raw=true) See who played a part in adding the app.
  - ![icon](https://github.com/Botspot/pi-apps/raw/master/icons/screenshots/buttons/errors.png?raw=true) If the selected app failed to install, this button will allow you to see its error log.

<br>


- Pi-Apps Settings can be configured by launching Menu -> Preferences -> Pi-Apps Settings.  
![settings](https://github.com/Botspot/pi-apps/raw/master/icons/screenshots/settings.png?raw=true)  
In addition to changeable settings, this window also gives access to these tools:
  - ![icon](https://github.com/Botspot/pi-apps/raw/master/icons/screenshots/buttons/categories.png?raw=true) Does that one app seem to be in the wrong category? With this button, you can change it.
  - ![icon](https://github.com/Botspot/pi-apps/raw/master/icons/screenshots/buttons/new%20app.png?raw=true) Create a new app with a wizard-style set of dialogs. We recommend reading [the tutorial](https://github.com/Botspot/pi-apps/wiki/Creating-an-app).
  - ![icon](https://github.com/Botspot/pi-apps/raw/master/icons/screenshots/buttons/log%20files.png?raw=true) View the past weeks-worth of installation logs. This is useful if you ever encounter an app that won't install and want to see the terminal output after you closed the terminal.
  - ![icon](https://github.com/Botspot/pi-apps/raw/master/icons/screenshots/buttons/import%20app.png?raw=true) This allows you to easily import a 3rd-party app from elsewhere. It helps Pi-Apps developers test upcoming apps for reliability on a variety of systems.

<br>

To learn more about Pi-Apps, read [the documentation](https://github.com/Botspot/pi-apps/blob/master/DOCUMENTATION.md) and the [wiki](https://github.com/Botspot/pi-apps/wiki).







