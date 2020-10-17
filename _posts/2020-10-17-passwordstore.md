---
title: 'Password Management Tool'
date: 2020-10-17
permalink: /posts/2020/10/passwordstore/
tags:
  - passwordstore
  - password management
  - tools
  - gpg
---


Internet Security breaches has been a common topic over the past decades, it's
no longer a foreign topic to many. Maybe you have gotten your account hacked
before, or maybe one of your passwords has been compromised. Hopefully, you
practiced a rather secure method of *NOT* reusing your password for all your
other applications.

Personally, i think i practiced a rather safe method of using different
passwords for different sites that i visit. However, with more and more
applications and websites popping out, sometimes it gets difficult trying to
remember and keep track of all the passwords you used.

Furthermore, if you can easily remember all those passwords, then perhaps your
passwords are not as secured as you thought it is.

```
              What's my password again?
        ヘ(>_<ヘ)
```

Sure, you can save your passwords using the build in password managers in your
web browsers, but that also means that you're trusting the browsers to protect
your details entirely. Alternatively, you can use other password management
tools such as LastPass, Dashlane and various other managers which are
often promoted by YouTube content creators. But that, would somewhat still
require you to trust the service provider.

Recently, i came across a password management tool which is 'terminal based' and
as a fan of terminal based tools, i couldn't resist the looking more into it.
So, let me introduce this tool to you: [pass](https://www.passwordstore.org/).
For one, i like the idea of open source tools which allows you to inspect and
change the program however you see fit.

----------

The Basics:
===========
As mentioned, `pass` is a password management tool, which follows the
[Unix Philosophy](http://en.wikipedia.org/wiki/Unix_philosophy), which aims to
be simple, short, clear, modular, extensible and easily maintainable. The
passwords are stored in a Tree like directory with each password encrypted using
`gpg`.

Caption: Tree-like structure example
```
Password Store
├── 192.168.1.1
├── accounts.reddit.com
├── facebook.com
├── github.com
├── google.com
├── linkedin.com
├── netflix.com
├── overleaf.com
└── youtube.com
```

So, what is GPG? Well, to be honest, that bothered me for a while as i wasn't
too familiar with it. All i knew was that `gpg` is a encryption method which is
widely used, and that was pretty much the extend of what i knew about it. I took
the dive, and learned more about it. I wouldn't say that i have fully grasp the
idea of the tool, but enough to use `pass` as my daily password manager.

GPG is basically, an implementation of PGP (Pretty Good Privacy). Have i
confused you yet? Haha. I'm just going to briefly explain what i understand, but
i reckon, you should probably do your own research. So here goes.

Imagine you have a set of keys. One is used to lock the door, and the other, to
open it. You can share the key which is used to lock the door, because sure, why
not? Everyone can lock the door... but they can't open it without the other key.

The key used to lock the door, is called a Public Key. While the key used to
open the door is called a Private Key. Here's a simple illustration of the door.
In this scenario, both keys are required to encrypt and decrypt the information
available behind this door. As such, your private key, like the name indicates,
should be kept privately, and only made available to those whom you trust, as
how you would do with your house keys. While the public key can be shared if you
want to allow other people to lock/encrypt information which can only be opened
with your set of private key.

```
 Door
+----------------------------+
|                            |
|                            |
|                            |
|  Public          Private   |
| +--------+      +--------+ |
| |        |      |        | |
| |        |      |        | |
| |        |      |        | |
| +--+--+--+      +--+--+--+ |
|    |  |            |  |    |
|    |  |            |  |    |
|    |  |            |  |    |
|    +--+            +--+    |
|                            |
|    Lock            Open    |
|                            |
|                            |
|                            |
+----------------------------+
```

So with that, you should keep your private keys securely, and perhaps even make
backups or print them out so that one day, if your key goes missing, you would
still have some backup somewhere that allows you to reopen the gateway to all
the information behind the door.

How to use it:
==============
So, if that got you interested, read on. If it was a little too complicated,
then perhaps, this might not be the right tool for you. Since, if you somehow
forgot where you placed your secret key, you might be locked away permanently
from your other passwords. I hope this would scare you a little, and be slightly
paranoid over how you keep your keys :)

Okay, regardless of what distribution of Linux you're running, the installation
process is rather similar. Just use the right package manager for the job.
Installation can be done using: `yay -S pass` if you're using Arch based system
like myself, or just simple `sudo apt install pass` on a Debian/Ubuntu based
machine.
With the tool installed, unfortunately, you are still not able to use the tool
as you have not generated your own private and public keys. So here's how you
can do it.

Generating Public and Private keys using gpg:
```
gpg --full-generate-key

gpg (GnuPG) 2.2.23; Copyright (C) 2020 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Please select what kind of key you want:
    (1) RSA and RSA (default)
    (2) DSA and Elganal
    (3) DSA (sign only)
    (4) RSA (sign only)
   (14) Existing key from card
Your selection?

RSA keys may be between 1024 and 4096 bits long.
What keysize do you want? (3072)

Please specify how long the key should be valid.
      0 = key does not expire
   <n>  = key expires in n days
   <n>w = key expires in n weeks
   <n>m = key expires in n months
   <n>y = key expires in n years

Key is valid for? (0)
Key does not expire at all
Is this correct? (y/N) y

GnuPG needs to construct a user ID to indentify your key.

Real name: <insert real name here>
Email address: <insert email address here>
Comment: <insert comment if any>

You selected this USER-ID:
    "real name (comment) <email address>"

Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit?
O
```

This command will then ask you to fill up some details such as your real name,
and email address. These information are not sent anywhere, but stored within
the public and private keys as a means of identifying the owner of the keys.
I normally go with the default values which are recommended, but typically set
an expiry date for the keys just to be extra secured. But that's totally up to
you.

Once you have entered all the information, the program will ask you to enter a
passphrase which can be thought of as another password to open the private key.
In other words, this passphrase is like the 'master password' to unlock all your
other passwords in the future. So give it a strong password which you can
remember.

When you're done with that, the program will ask you to move your mouse/type
random things/open or close other applications to generate a lot of random bytes
which is used to generate the keys. You might wanna take note of this portion of
code which is generated here as it contains your private key ID. But fear not,
there's a way to list it out again in case you missed it.

Sample message:
```
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
gpg: /root/.gnupg/trustdb.gpg: trustdb created
gpg: key DBACA805DFF5C88B marked as ultimately trusted
gpg: directory '/root/.gnupg/openpgp-revocs.d' created
gpg: revocation certificate stored as '/root/.gnupg/openpgp-revocs.d/876D27F7A16015CED0D4E38EDBACA805DFF5C88B.rev'
public and secret key created and signed.

```

Congratulations, you have now finished the first step of generating your keys.
Now you can finally use pass to store your keys! Based on the message above,
your private key ID is *DBACA805DFF5C88B*, you will be uing it to initialize
pass. Don't worry, this is not my real private key ID, since this was
generated in a virtual machine.
Here's a summary from `tldr` regarding `pass`:
```
  pass

  Tool for storing and reading passwords or other sensitive data.
  All data is GPG-encrypted, and managed with a git repository.
  More information: https://www.passwordstore.org.

  - Initialize (or re-encrypt) the storage using one or more GPG IDs:
    pass init gpg_id_1 gpg_id_2

  - Save a new password and additional information
    (press Ctrl + D on a new line to complete):
    pass insert --multiline path/to/data

  - Edit an entry:
    pass edit path/to/data

  - Copy a password (first line of the data file) to the clipboard:
    pass -c path/to/data

  - List the whole store tree:
    pass

  - Generate a new random password with a given length,
    and copy it to the clipboard:
    pass generate -c path/to/data num

  - Initialize a new Git repository (any changes done by pass will be
    committed automatically):
    pass git init
```
Unfortunately, this `tldr` guide isn't really useful if you're not familiar with
the tool. To initialize your password store, use the following commands:

```bash
$ pass init DBACA805DFF5C88B
mkdir: created directory '/root/.password-store/'
Password store initialized for DBACA805DFF5C88B
```

With that, your password store is initialized. If you would like to use `git` as
a version control system for your password store, you can use `pass git init`.
Provided that you have setup git properly before, you shouldn't face any
difficulty in that step. Otherwise, git will ask you to enter your name and
email address to identify yourself. Also, just to note, since i was running the
command in a docker container as root, my password store was created in the root
directory. However, in a normal circumstance, it would be created in
`/home/username/.password-store`.

Following the `tldr` documentation, you can insert your passwords using:
`pass insert <site name.com>`. For example, if i used `pass insert google.com`,
the program will ask me to 'Enter the password for google.com:' and then retype
it again.

You can then list it out using `pass`:
```
[root@c599a76eb78a /]# pass
Password Store
└── google.com
```

Now, how do you retrieve it? Simple, just type `pass google.com`. This will then
trigger the program to ask you for your `passphrase` which you used to encrypt
the secret key. Your password will be displayed on the terminal, which isn't
really useful. Alternatively, you can use `pass -c google.com` which will copy
the password to your clipboard.

Also, if you have updated your password, you can edit it using
`pass edit google.com`. Again, `pass` may or may not ask your for your
passphrase to edit the password, depending whether or not timeout has occured.

If you would like the program to generated a password for you, simply use
`pass generate facebook.com 15` or however long you want. The output would look
something like the below:
```
[root@c599a76eb78a .password-store]# pass generate facebook.com 15
The generated password for facebook.com is:
o.A6^z;_#!BiH#0
```

HOWEVER
=======
This isn't really useful isn't it? Since you would normally want to store your
username and password together. Here's where `pass` makes it extensible. The
program, by default will store the password on the first line of the file. You
can easily add new lines to describe items such as username, secret question and
secret answers and etc.

```
Yw|ZSNH!}z"6{ym9pI
URL: *.amazon.com/*
Username: AmazonianChicken@example.com
Secret Question 1: What is your childhood best friend's most bizarre superhero fantasy? Oh god, Amazon, it's too awful to say...
Phone Support PIN #: 84719
```

Furthermore, there are many different extensions which has been developed to
work in conjunction with pass, which includes web browsers. I would definitely
recommend you to check it out from their main website.


What if `pass` suddenly goes away?
==================================
No worries, since your passwords are encrypted using gpg, you can easily decrypt
it using gpg. Essentially, your passwords are stored as encrypted plain texts.

```
[root@c599a76eb78a .password-store]# gpg -d google.com.gpg
gpg: encrypted with 3072-bit RSA key, ID 3718BA9CC5CCB5B4, created 2020-10-17
      "clarence (asd) <clarence@hotmail.com>"
1234
```

And if you used `git` as your VCS, you can push your changes to the git servers,
and synchronize it among your various machines.
But, remember, you would need to export your secret key over using the following
command `gpg --export-secret-keys > temporary-file`. Copy it over to the new
machine, and import it, and setting the trust level to `ultimate`. I'll leave
that for you to research on your own ;)

I hope that this simple introduction has given you some insights to this
wonderful tool. Have fun exploring!

That's it for today, see you next time!
