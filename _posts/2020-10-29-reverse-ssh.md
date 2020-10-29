---
title: 'Reverse SSH'
date: 2020-10-29
permalink: /posts/2020/10/reverse-ssh/
tags:
  - reverse ssh
  - systemctl
  - syncthing
  - tools
  - security
  - fail2ban
---

Corona virus is back again. And, yes... back to working remotely.
During the previos WFH(work from home) session, i didn't have much problem as i
was building a `pyqt` application coupled with some `mongodb` functions. I
didn't really need the remote access to the office PC.

But this time, it was slightly different. I **NEEDED** access to the office PC
as it's connected to a kiosk where some of the hardwares are hooked up. There
was no other way, I needed to figure out the best way to access my office PC.

In one of my previous post, i shared a way to 'reverse ssh' via tmate.
Well, that method still kindda works... but, tmate didn't allow X forwarding
which was what i was hopping for. Finally, i took some time to really understand
how reverse ssh works, and set it up to work.

Here's a diagram to illustrate the process.

```
+-----------------------------------------------------------------------------+
|                                                                             |
|            home                                      office                 |
|        +----------+                               +----------+              |
|        |          |                               |          |              |
|        | user:    |                               | user:    |              |
|        |   james  |                               |   adam   |              |
|        |          |                               |          |              |
|        |          |                               |          |              |
|        +----------+                               +----------+              |
|    IP: brighttux.com                                                        |
|                                                                             |
|                                                                             |
|                             ssh -X -R 2210:localhost:22 james@brighttux.com |
|                      <-------------------------------+                      |
|                                                                             |
|                                                                             |
|   ssh -X adam@localhost -p 2210                                             |
|                     +-------------------------------->                      |
|                                                                             |
|                                                                             |
+-----------------------------------------------------------------------------+
```

Yeap... that's it. It's that simple. I didn't know why it took me so long to
understand it.
Here's the image transcript:

Assuming there's 2 machines. One at home, and another at the office.
First, you would obviously need to setup ssh-server on both machines, and
possibly setup port forwarding for your home machine if it's not done yet.

To get started with the process. We would need to perform a reverse ssh from the
office machine. In the diagram, we would perform
`ssh -R 2210:localhost:22 james@brighttux.com` assuming there's a user `james`
at `brighttux.com` (which is probably going to be an IP address).

What this does, is to setup a tunnel from port 22 of the office machine to port
2210 of the remote(home) machine. Then, from the home machine, we can connect to
this particular port using `ssh adam@localhost -p 2210`. Which means, we are
connecting to the tunneled port which we connected from the remote machine.

--------

But... i don't have a static IP at home, unlike the diagram above! What can i
do? Well, here's what i did, there's probably so many other possible solutions
that you can come up with.

1. Remember the post about tmate? Yeap, i'm still using that method. Here's what
   i did differently. I had to fix some problem which happened quite frequently
   at my workplace recently. Power outage. Yeap..

   I had to first enable boot on lan/power if ever there's any power outage. So
   that, obviously, i can reconnect to the remote machine. I won't go into the
   details of that, since those are settings at the BIOS.

   Then, i had to create a deamon to automatically start tmate on the remote
   machine. And yes, so that the tmate connection is still available when i need
   it.

   Since i'm using systemctl on my office pc. Here's the service file which i
   enabled at `/etc/systemd/system/tmate.service`.

   ```
   [Unit]
   Description=Autoboot tmate -F service
   After=network.target
   StartLimitIntervalSec=0

   [Service]
   Restart=always
   RestartSec=1
   User=clarence
   ExecStart=/home/clarence/bin/tmate -F

   [Install]
   WantedBy=multi-user.target
   ```

2. Step one completed. We are now sure that if ever there's a power outage, the
   remote machine will automatically reboot and the tmate service will run. Now,
   how do we automate the process of the office machine connecting to mine?

   I would have to send my external IP to the office machine securely, and i was
   recently introduced to a tool called `syncthing`. I won't go into the details
   of it, since it's a little too complicated to explain here. But basically,
   it's like your cloud storage function, but it's only stored on your machine
   and no where else.

   I wrote a simple `cron` job to `curl ifconfig.me` every morning and wrote it
   to a file on my machine which is then synced to the office machine using
   `syncthing`. `crontab -e` then add in `30 7 * * * /home/clarence/bin/get_ip`.

3. Similarly, on the remote machine, i setup a cron job to read the synced up IP
   file and perform a reverse SSH connection to my home machine at a slighly
   later time. `0 8 * * * /home/clarence/bin/autossh` with the following codes.

   ```
   #!/bin/bash
   # get external IP
   extIP=$(cat /home/clarence/sync_dir/external_ip)

   # create reverse ssh connection back to home machine
   ssh -R 2210:localhost:22 brighttux@$extIP
   ```

4. We're done. Unless something bad happens, we should have our connections
   always ready to go in the morning. Do know that if the port has been used,
   you can't re-use it for other purposes. So technically, the daily cron job on
   the remote pc is redundant, since it doesn't connect to the same port.

I have yet to try X forwarding, but i suppose there shouldn't be any problem
since we're using the actual ssh protocol.

On a side note, i've been getting a whole lot of random attacks from external
parties after i enabled ssh server and port forwarding on my home pc.

```
$ systemctl status sshd
● sshd.service - OpenSSH Daemon
     Loaded: loaded (/usr/lib/systemd/system/sshd.service; enabled; vendor preset: disabled)
     Active: active (running) since Wed 2020-10-28 17:25:38 +08; 1 day 1h ago
   Main PID: 1341261 (sshd)
      Tasks: 1 (limit: 9385)
     Memory: 7.9M
     CGroup: /system.slice/sshd.service
             └─1341261 sshd: /usr/bin/sshd -D [listener] 0 of 10-100 startups

Oct 29 19:01:21 brightstudio sshd[1424846]: Invalid user guest from 141.98.81.200 port 38499
Oct 29 19:01:21 brightstudio sshd[1424846]: Connection closed by invalid user guest 141.98.81>
Oct 29 19:01:24 brightstudio sshd[1424848]: Invalid user support from 141.98.81.192 port 39438
Oct 29 19:01:24 brightstudio sshd[1424848]: Connection closed by invalid user support 141.98.>
Oct 29 19:15:28 brightstudio sshd[1425887]: error: kex_exchange_identification: Connection cl>
Oct 29 19:15:28 brightstudio sshd[1425887]: Connection closed by 142.93.143.46 port 41320
Oct 29 19:20:27 brightstudio sshd[1426198]: Invalid user admin from 114.29.237.145 port 35072
Oct 29 19:20:33 brightstudio sshd[1426198]: Connection closed by invalid user admin 114.29.23>
Oct 29 19:20:40 brightstudio sshd[1426200]: Invalid user admin from 114.29.237.145 port 35164
Oct 29 19:20:42 brightstudio sshd[1426200]: Connection closed by invalid user admin 114.29.2
```

```
# fail2ban-client status sshd
|- Filter
|  |- Currently failed:	1
|  |- Total failed:	1240
|  `- Journal matches:	_SYSTEMD_UNIT=sshd.service + _COMM=sshd
`- Actions
   |- Currently banned:	4
   |- Total banned:	8
   `- Banned IP list:	115.76.170.42 161.97.64.180 85.209.0.103 190.149.175.189

```

1240 attemps so far, after i rebooted my network twice (to change my external IP)
.. welp, i'm not sure what else i can do, since i've already implemented ssh key
access only, `fail2ban` and `ufw` to block most attemps.

That's for another day i guess. Thanks for reading. Stay safe.

Caption: Person wearing face mask.
```

                               `.-::///////::-.`
                          `.:/+oooooooooooooooooo+/-.
                       `-/++++++ooooooooooooooooooooo+-
                     `:++++++++++++++oooooooooooooosssso-
                   `:+++++++++++++++++++++oooooooooosssso/
                  -++++++++++++++++++++++++oooooooooooosso+`
                 :+++++++++++++++++++++++++++ooooooooooosso/
                -+++++++++++++++++++++++++++++ooooooooooosso:
                ++++++++++++++++++++++++++++++ooooooooooossso.
               `+++++++++++++++++++++++++++oooooooooooooosssy+
               `+oo++++++++++++++++++++++ossyyyyyyysoooossyyy+
               `+oo+++++++++++++++++++++o+++oooosssssoooyhhhy:
                /ooo++++++++++++++++++++++oosyyhhhysooooyhhhs`
                -oo++++/:+++++++++++++++osyysshhhhyso+/::--oo`
                 +o++++++/::+++++++++++oooooooo++//-.....--:/:
                 .++o+ooo++/--/+++++//::::--.---------::://+/:
                  :++ooso+++++:--..```...---::::////////////++`
                   /++syoo+++++++.--.--::///+++////////////+++-
                   `++osso+++++++/:::::////+++++////////+++ooo+-
                    .++++o++++++++::::::://///////++++++///oo+++`
                     .+++ooo++++++:::--::::///++++++//////+oo++.
                      .+++oo++++++///:///////////////////+ooo++:
                       .++/:+++++o/::///////////////////++ooo+++
                        :+++:/+++o/////////////////////++oooo+o+
                        `+++++//+/::/++//////+++++///++++oooooo-
                         /+++++:-:///:::::::///////////++ooooo:
                         :+++++o+--////////////////////+oooo+-
                         -++++++oo/-://///////////+++++oooo/`
                         :+++++++ooo:-:////::///++++oooo+:`
                         /+++++++++ooo:-:///++++ooooo+/-`
                         +++++++++++oooo/:::/++++++/.`
                        `++++++++++++ooooooo++oooos:
                        -+++++++++++++oooooooosssss:
                        /++++++++++++++ooooooosssss:
                       -++++++++++++++++ooooooossss:

```
