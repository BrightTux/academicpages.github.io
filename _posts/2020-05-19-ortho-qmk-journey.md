---
title: 'Ortholinear Keyboard with QMK'
date: 2020-05-19
permalink: /posts/2020/05/ortho-qmk-journey/
tags:
  - QMK
  - firmware flashing
  - Ortholinear
---


So, recently i was intrigued by ortholinear keyboards and the hype around it. The idea was simple: having keys
laid out in a grid based layout, your fingers would not need to move as much compared to a traditional staggered layout.
This, combined with the power of QMK firmware, the limit is endless.... or so to speak. QMK allows the user to configure
the keyboard however the user sees fit. 

I'll be breaking this short journal into 2 part. The keyboard, switch and ortholinear layout; and QMK(instructions to flash, 
mainly for my own reference)
 
Mechanical keyboards
======

What's the hype around mechanical keyboards? Basically, instead of silicon domes on the typical keyboards, mechanical keyboards
uses mechanical switches to actuate each keystroke. Meaning, there's an actual metal leaf contact point which completes the
electronic circuit when a key is pressed. 

In order to keep it simple, i would just briefly describe the various kinds of mechnical switches available.
1. Clicky switches: Typically known for the high pitch click sound that is produced
2. Tactile switches: Similar to the clicky switch with some profiles to indicate actuation
3. Linear switches: (I have not really tried them yet) but it has little to none tactile feedback except for the spring

So, like i mentioned earlier, ortholiner keyboards uses a grid based layout so that your fingers never really need to leave
the home row (asdfghjkl;) too much, and hopefully the other keys are just a grid away. Along with that, since spacebars are
typically longer, with the reduction of size, your thumb can be put into more use by adding additional keys such as 
'raise' or 'lower' keys... which is more commonly known as Function (Fn) keys available on some keyboards to control things
like volumn up or brightness and etc. (We will touch on this a little more on the QMK Section)

For my first keyboard built, i decided to purchase the XD75 keyboard kit from MassDrop due to the garrage sale.
And since my wife was complaining about the blue switches on my other TenKeyLess(TKL) keyboard, i decided to try 
tactile switches. Hence, i went with Kailh Brown Box Switches. 

I went with the 75 keys layout as i thought this would be a good opportunity to test out the following configurations:
1. [Planck](https://drop.com/buy/planck-mechanical-keyboard) 40% layout
2. [Preonic](https://drop.com/buy/preonic-mechanical-keyboard) 50% layout
3. [Split layout](https://yushakobo.jp/shop/consign_chidori/) 
4. And ultimately ortholinear layout to improve my touch typing skills since i would be typing a lot as a programmer.


Quantum Mechanical Keyboard (QMK)
========

Most keyboards nowadays would have some sort of firmware built into it to allow communication with the host device (PC).
This keyboard is no different. However, the key difference is that this keyboard uses QMK firmware. 

You might be asking what's the big deal with that? To put it simply, QMK firmware allows users to configure their own 
desired layouts using this [tool](https://config.qmk.fm). 

Here's a little back story of my journey: (aka How to do it wrong)
Upon building my keyboard with the default layout, i wanted to try flashing my own setup.
I configured my layout (using xd75), saved the JSON file(Layout file) and compiled the HEX file(Firmware). 
Next, i followed the guide and created the environment to compile my firmware on my PC since the toolbox tool is not
available on linux. 

Used the `qmk compile`, `qmk flash` command.. but device was not detected... got frustrated, and failed.
On the next day, after work.... i gave this another try... 'almost bricked' my keyboard.. and finally suceeded.

Here's a quick run down of task to flash my board.
==========

1. Eventhough the keyboard's URL link says XD75... it's actually a [IDOBO PCB](https://config.qmk.fm/#/idobo/LAYOUT_ortho_5x15).

2. Configure your layout, save the json file.

3. Make sure you have setup the [compilation environment](https://docs.qmk.fm/#/newbs_getting_started?id=setting-up-your-qmk-environment)

4. Copy your JSON file to your own config folder, ie; `/home/tux/qmk_firmware/keyboards/idobo/keymaps/BrightTux`

5. Use `qmk json2c -o keymap.c brighttux.json` to generate the `keymap.c` file

6. Run `qmk compile` (assuming you have set your keyboard to IDOBO and user to your user name)

7. Run `qmk flash` to begin the flashing process. Note: this is when you should press either the hardware 'reset' button or 
the QMK configured soft-reset button. The qmk program will now detect your keyboard and flash the firmware.

8. Test your keymaps, rinse and repeat if you are not satisfied.



Extra note:
=========

1. There's some extra [notes](https://docs.qmk.fm/#/faq_build?id=linux-udev-rules) to be aware of when compiling on a 
linux machine. 

2. If you reached here. Thanks for reading... it's mostly just a journal for me... should i ever face any difficulty again.

3. There is probably some better way... which i do not know of.. but hey.. it works.. at least, for now..





