---
title: 'SSH - with GUI?'
date: 2019-02-05
permalink: /posts/2019/02/ssh-with-gui/
tags:
  - ssh
  - x forwarding
  - todayilearnthat
---



Have you ever been in a situation where all you've got is an SSH connection to a remote client, and the access to terminal by itself isn't gonna cut? 

well.. i have.. and that's the basis of this post. Before we head deeper into the issue at hand, I would like to wish everyone who's celebrating a Blessed Chinese New Year! May this year be ever prosperous, joyful, loving and peaceful! 

SSH With GUI? Solutions for both Linux and Windows users
======

So, recently i took up a freelance project where the goal was to extract customer's information from video feed. As the title implies, i had a SSH connection to a Rasp Pi device, i could access and run the extraction programs. However, when asked about troubleshooting - if the client was able to connect to the Rasp Pi and view what was going on, while i knew it was possible, i wasn't sure how to go about it.

The search engine was fired up, and a solution was found for both Linux and Windows users. The solution for both these OS are rather similar, here's some of the groundwork that needs to be established:

1) The first step is to enable X11 forwarding on the targetted machine:
```
ssh <user_id>@<target machine ip>
cd etc/ssh/
sudo vim ssh_config
```
```
ForwardX11 yes
```
```
sudo vim sshd_config
```
```
X11Forwarding yes
X11DisplayOffset 10
```

2) Once you're done updating the ssh_config and sshd_config file, the next step is to restart the ssh daemon. This steps depends on the distribution your device is on. As the current target is a Rasp Pi device, the following code is used:
```
sudo service ssh restart
```

3) Reconnect to your device, and test if you can launch and forward an X11 application. This step differs for both Linux and Windows users. This is because Linux uses X11 for their windowing system, however, Windows does not ship with support for X.

* Linux 
  * Since linux uses X11 windowing system, there's not much configuration except the following to enable X11.
  ```
  ssh -X <user_id>@<target machine ip> 
  # Take note, capital 'X'
  # For more info on how to use ssh, use 'man ssh' to display the manual
  ```

* Windows
  * To enable X forwarding on Windows OS, you would first need to install some supporting programs that enables X server. Some notable X servers are Cygwin/X and Xming. In my case, i installed Xming on my windows machine, load up PuTTY, and "checked" the Enable X11 forwarding button. 

  * ![x11 forwarding PuTTY](https://i.stack.imgur.com/B7r4t.png "PuTTY X11 forwarding")

* Mac
  * Same as linux machines, using feed in `-X` when connecting using SSH 

Credit:
https://superuser.com/questions/119792/how-to-use-x11-forwarding-with-putty?fbclid=IwAR0uFuesE0pAUiFvo3oKdo0v3nMrFbtnkifM6ncIMZwmGvBgYTvFjmpdoQo

