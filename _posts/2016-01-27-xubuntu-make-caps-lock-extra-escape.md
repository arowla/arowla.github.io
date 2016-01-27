---
layout: post
title: "Xubuntu Keyboard Mod Essentials: CapsLock -> Extra ESC; Windows Key -> XFCE Menu"
categories:
- articles
tags:
- sysadmin
- ubuntu
- xubuntu
- xmodmap
---

_I recently installed Xubuntu on my old Thinkpad T410s, in the hopes that it would be a lighter and faster distribution for my aging, beloved, but soon to be replaced workhorse.
I am not particularly enjoying the experience after several years of Linux Mint, but that is for another post._

Mapping CapsLock to Escape is an essential step for vim users. This is covered by an easy keyboard tweaks submenu in Mint, but not so in Xubuntu. It took some searching, trial and error to find
a working command. In Session and Startup, add an item:

    xmodmap -e "clear Lock" -e "keysym Caps_Lock = Escape"

Another handy trick is setting up a shortcut on the Windows key to open the XFCE applications menu. There are several app menu and search options in XFCE. The one provided here
will bring up the same menu as when you click the XFCE mouse logo in the corner of the panel. Go to `Keyboard` -> `Application Shortcuts`, click the `Add` button, and enter:
    
    xfce4-popup-whiskermenu

Click `OK` and then hit the Windows key to define it as the shortcut key. That's it!
