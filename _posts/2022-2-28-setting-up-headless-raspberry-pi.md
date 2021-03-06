---
layout: post
title: Setting up headless Raspberry Pi
description: However, you will need a monitor, keyboard, mouse… etc. This will be associated with a huge amount of money (that’s not low-cost anymore…). 💰 But, You may use a headless setup for your Pi to cut down all the cost. 😎
author: cycool29
date: 2022-2-28 15:00 +08:00
permalink: /post/000001.html
tags: raspberrypi tutorial beginners linux
read-time: 5
medium-link: https://medium.com/@cycool29/setting-up-headless-raspberry-pi-72979b81e07b
dev-link: https://dev.to/cycool29/setting-up-headless-raspberry-pi-1m9b
---

___

## Table of Contents

- [What is headless setup?](#what-is-headless-setup)
- [Install OS to your SD card](#install-os)
- [Enable VNC in your Raspberry Pi ](#enable-vnc)
- [Connect VNC to your Raspberry Pi ](#connect)


___

You may just want to use your Raspberry Pi as a low-cost Linux computer.

However, you will need a monitor, keyboard, mouse... etc. This will be associated with a huge amount of money (that's not *low-cost* anymore...). 💰

But, You may use a headless setup for your Pi to cut down all the cost. 😎

<h2><span id="what-is-headless-setup">What is headless setup? 🤔</span></h2>    

A headless setup is the Raspberry Pi minus the monitor, keyboard, and mouse. Running a headless setup lets us forego the extra peripherals and directly control the Raspberry Pi wirelessly from any other PC in local network.


In this tutorial, you need to install [Raspberry Pi Imager](https://www.raspberrypi.org/software/), [Angry IP Scanner](https://angryip.org/download/) and [RealVNC Viewer](https://www.realvnc.com/en/connect/download/viewer/).

![RPI Imager](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/r5rzy0qgieffqb7sc2c4.png)
 
![Angry IP Scanner](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ro5zrvkykglulvmgneiy.png)

![RealVNC Viewer](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/dr34s3c98hf5vgyk7c3i.png)
 

<h2><span id="install-os">Install OS to your SD card ⏬</span></h2>    



Your Raspberry Pi needs an operating system to work. If your SD card is not arrived with Raspberry Pi OS or NOOBS pre-installed, you will need to install an operating system into it first. 


Insert your SD card into the SD card slot or SD card reader of your **external PC**.

Open **Raspberry Pi Imager**. You will use this tool to flash OS to your SD Card.  

![Raspberry Pi Imager](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/kwn63hzaygh5ywa271nb.png)
 
    

Click **CHOOSE OS**.  

![Choose OS](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/w0v69lgvc8ww9xonsngw.png)
 
    
    
Choose any OS you want to install on your Raspberry Pi. 

![Choose OS](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ob28fgok557ioz1t5f99.png)
 
![Choose OS](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/6n4pcgw1n8buw7elzqrh.png)
     
Click **CHOOSE STORAGE**.
     
![Choose Storage](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/lj4ob0ovjfdw3urje7qt.png)

Choose the SD card you want to flash to your Raspberry Pi.
     
![Choose Storage](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/fsf1mc0omvekqhu67un5.png)
 
Now, press <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>X</kbd>. This will open an **Advanced options** dialog.

Toggle on **Enable SSH** and **Use password authentication**.

Create a **login password** for your Raspberry Pi and fill it in the **Set password for the 'pi' user** . You must remember it as we will need this password later for SSH login.

If you are going to use WiFi for your Raspberry Pi's connection, toggle on **Configure wifi** and configure your WiFi settings there. 

Lastly, check **Set locale settings**. Choose your Time zone and Keyboard layout there and click **Save**.
     
![Advanced options](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/cmqx40ktmblw8h9en1f1.png)
 
Check all configurations are correct and click **Write**. This will start writing the Raspberry Pi OS to the chosen SD Card. It might take a while so you may have a coffee break. 
     
![Writing image to SD card](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/lcs91ynibna3ww6el0jz.png)
 
 
![Verifying image is writen to SD card](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/goohgqiccbfc2tuu4imt.png)
 
14. Now you have flashed an OS to your SD card. Safely unmount it and plug it into Raspberry Pi's SD card slot.

![Flash done](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/smoiqptrmjmal0n9a1fr.png)
 

<h2><span id="enable-vnc">Enable VNC in your Raspberry Pi ✅</span></h2>  

Connect your Raspberry Pi to power source.

Launch **Angry IP Scanner**.

Click **Start** to discover your Raspberry Pi.

You should see a list of IP addresses after scanning. Find `raspberrypi` or `raspberrypi.local` and note down the IP address.

![Ipscan scan result](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/hoejjx9agohl11acgph6.png)
 
Exit Angry IP Scanner.

If you are on Windows, you will need to enable OpenSSH first. 
   - Open Settings, select Apps > Apps & Features, then select Optional Features.
   - Scan the list to see if the OpenSSH is already installed. If not, at the top of the page, select Add a feature, then: Find OpenSSH Client, then click Install. 

Open a terminal window on your PC replacing `<IP>` with the IP address of the Raspberry Pi you’re trying to connect to.

```bash
ssh pi@<IP>
```

When the connection works you will see a security/authenticity warning. Type **yes** to continue. You will only see this warning the first time you connect.

You will be prompted for the password for the `pi` login, enter the password you set just now in Raspberry Pi Imager.

Now you should see something like this: 

```
pi@raspberrypi ~ $
```

Now you can execute commands on your Pi. But there is no graphical desktop, yet.

Enter `sudo raspi-config`.

Do the following to enable VNC:

   - Navigate to **Interfacing Options**.
   - Scroll down and select **VNC** > **Yes**.

![Raspi-config VNC](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/fjuhdnr6szqgyi7smj97.png)
 

Now you have enabled VNC on your Raspberry Pi. Close the SSH session by entering `exit` or just simply close the terminal window.

<h2><span id="connect">Connect VNC to your Raspberry Pi 🔗</span></h2>    

Launch **RealVNC Viewer**.

Select **File > New connection**.

Enter the IP address of your Raspberry Pi in **VNC Server** field and give it a name in **Name** field.

![VNC property](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/4mm9hzrbjcyqqwx21o4s.png)
 
Leave all other options default and click **OK**. 

Right click at the property you just added and select **Connect**

![VNC connecting](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/6q67j9ka26vevx67utck.png)

If it prompts you this window, simply click **Continue**.

![VNC warning](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/kh5z530ydf26xmnszmxw.png)
 
  
Fill **pi** in the **Username** field and your Raspberry Pi's password in the **Password** field.

![VNC username password](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/nlfjdkof5shz22aoaw1e.png) 

Click **OK**.

Finally, you will be presented with your Raspberry Pi desktop!

![VNC desktop](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/t2gwpfd3rt2o7y5qrlq5.png)
 
Thanks for reading!

BTW, today is the 10th anniversary of Raspberry Pi! 
Wish happy birthday to them in the comment box! 🎂

<blockquote class="twitter-tweet" data-theme="dark"><p lang="en" dir="ltr">We turn 10 today. Happy birthday to us.<br><br>While we wait to see if we out-trend Lady Gaga again, here&#39;s Eben talking about a decade of Raspberry Pi:<a href="https://t.co/QqNlbRlN6l">https://t.co/QqNlbRlN6l</a> <a href="https://t.co/VoDnp3V3WT">pic.twitter.com/VoDnp3V3WT</a></p>&mdash; Raspberry Pi (@Raspberry_Pi) <a href="https://twitter.com/Raspberry_Pi/status/1498221458815864834?ref_src=twsrc%5Etfw">February 28, 2022</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>