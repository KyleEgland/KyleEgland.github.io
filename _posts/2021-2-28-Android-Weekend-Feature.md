---
layout: post
title: Android Weekend Feature
categories: [blog, purpleteam]
tags: [android, nethunter]
---

Having fun with an unsupported device in hopes of extending its life just a little bit more.

![Moddified Weekend Vibes](/images/posts/2021-2-28/0_modified-weekend-vibes.jpg)

## The story so far

I've spent some time hacking away at my Pixel C table as the device is no longer supported by Google (serious "boo-hoo"s over here) and I love everything about this little hardware setup - reasonable processor, RAM, screen size, etc. and I rather like the accessories (folio and keyboard) that I purchased with it. Rather than let it rot or simply pay to continue to play (don't like all the e-waste...), I've decided to use it as a learning experience. Oh, also, it's my device and I want to use my tablet the way I want to use it. After all, the laptop I did this on is a former Windows 7 machine now running Ubuntu - why can't we do that with handsets and tablets?

Around the time of last year's [Def Con](https://defcon.org/html/defcon-safemode/dc-safemode-index.html) I started my first attempt to put [Kali Linux](https://www.kali.org/kali-nethunter/) on the Pixel C. Despite how much I love and live Android, my initial attempts were very naive and therefore resulted in a janky "how-to" and an underwhelming result (had Kali apps on my tablet at Android version 7.1...woo...). I wasn't satisfied with this and so the tablet sat, unused, for quite some time (twas disapointing). The motivation hit me this weekend to "fix-it-up" and so I've installed [AOSP Android 11](https://www.getdroidtips.com/android-11-google-pixel-c/), added [F-Droid](https://f-droid.org/) (instead of GApps), and installed [Kali Nethunter store](https://store.nethunter.com/) (...also instead of GApps). The efforts are not quite finished (need some productivity apps and/or access to OneDrive) but I'm calling this MVP - you got-tuh know when tuh fold um!

Lastly, the original work from my initial efforts has been (relatively) preserved below (see "Kali Nethunter - Pixel C") as that laid the foundation for much of what I was able to achieve.

## Prep work

My tablet has already been modified as I've installed Nethunter on it and I will therefore be focusing on the Android 11 components. Please check out the information at links provided here for further information regarding

- Enabling developer mode on the Pixel C
- [Download ADB and Fastboot](https://www.getdroidtips.com/download-adb/)
  - Execute the below command to install ADB Fastboot binaries on Ubuntu:

{% highlight bash %}
$ sudo apt install android-tools-adb
$ sudo apt install android-tools-fastboot
{% endhighlight %}

- [How to Unlock bootloader via Fastboot Method on Android](https://www.getdroidtips.com/unlock-bootloader-via-fastboot-on-android/)

![Unlocked bootloader on Pixel C](/images/posts/2021-2-28/1_unlocked-bootloader-warning.jpg)

- [Install TWRP on Pixel C Tablet](https://www.getdroidtips.com/root-and-install-twrp-on-pixel-c-tablet/)
  - [Pixel 2 XL 3.5.0_9-0](https://dl.twrp.me/dragon/twrp-3.5.0_9-0-dragon.img.html)
  - ^ Version of TWRP I used, re-flashed so I had the current version

![TWRP installed on Pixel C](/images/posts/2021-2-28/2_twrp-installed-pixel-c.jpg)

The basic order of operations is:

1. Enable developer mode on the device
2. Enable "OEM" unlock or bootloader unlock
3. Install TWRP

These steps will allow for the installation of the actual Android 11 image that will be usided to update the device or another other custom rom for that matter.

## Android 11 Image

Given the available options (check out the original guide [link](https://www.getdroidtips.com/android-11-google-pixel-c/)) I chose to download crDroidAndroid-11.0-20201219-dragon-v7.1. After updating my version of TWRP, I rebooted the device. Everything seemed fine (it booted and the device unlocked etc.) so I rebooted into recovery:

`$ adb reboot recovery`

Once in TWRP, I did a sideload of the Android image:

`$ adb sideload crDroidAndroid-11.0-20201219-dragon-v7.1.zip`

**Note**: This was done by going into Advanced in the TWRP menu and then selecting the sideload option, only when TWRP is ready (e.g. awaiting the sideload from adb) can you load the image.

![TWRP main menu](/images/posts/2021-2-28/3_twrp-main-menu.jpg)

![TWRP advanced menu](/images/posts/2021-2-28/4_twrp-advanced-menu.jpg)

![TWRP advanced sideload menu](/images/posts/2021-2-28/5_twrp-advanced-sideload-menu.jpg)

![TWRP advanced sideload console](/images/posts/2021-2-28/6_twrp-advanced-sideload-console.jpg)

This effort produced a "false positive" result for me, unfortunately. I did upload my image at which point I rebooted the device and saw the crAndroid logo, however, my disk was encrypted and this caused issues. After the logo, I was presented with a warning stating that my device had become corrupted. I was given the option to wipe the device (factory reset) but that seemed to "hang" (after about an hour I forced the device "off").

The problem was resolved by conducting several formats of my device (within TWRP) before sideloading the image once again. Now, the Pixel C tablet has been updated to Android 11 - great! time to move on to some applications - stock roms don't come with much!

![TWRP wipe menu](/images/posts/2021-2-28/7_twrp-wipe-menu.jpg)

## Applications without GApps

The point of my efforts are to:

- Allow the "safe" prolonged use of a device that I own
  - Google dropped support for my device so the last supported version of Android I could get was 8.1 - this allows for a more updated version
- Offer a light-hardware (something less than a laptop) hacking/developing/productivity device
  - Write Python (and serve Flask apps), take notes, check emails, etc. (yeah, sorta a lot)

The challenge is doing this without GApps – it's not that I couldn't get it, I simply don't want it. Firstly, there's a lot to be said about F-Droid as a viable alternative app store; it should be noted, though, that F-Droid doesn’t have everything. It does have termux (great for setting up some basic development tools) and the hacker keyboard (great on-screen keyboard when doing terminal/coding related tasks). Also, as I've learned from my previous Kali Nethunter endeavours, you can simply download the Nethunter Store which allows the installation of the Nethunter applications (if you have root).

That basically set-me-up-for-success for now – root, kali Linux app access (what I originally wanted when I started modifying the device...before this that is...), and some basic development tools (termux). I need a few other things worked out (how do I get Firefox and Microsoft Applications without GApps?) but this is good for now – one thing I've tried to embrace more is the idea of MVP (minimum viable product). Nothing can be perfect so you have to know when to stop and call it good. We can continue to iterate after this point but I've reached 1.0 :)

![Animated gif test](/images/posts/2021-2-28/Snapchat-1197914097.gif)

## Kali Nethunter - Pixel C

This documentation is just some notes and resources related to installing the Nethunter derivative of Kali Linux on the Google Pixel C tablet. This was quite a bit more of an undertaking than I had expected it to be. I considered myself to be "somewhat" experienced with Android – I've done some rudimentary application development, side-loaded apps, installed TWRP, modified older devices (ran scripts to get root), and have modified older devices as well (running a pirate box on my LG G4 at Def Con). However, I ran into this project headlong with no regard for being methodical. The documentation here is a postmortem of sorts; I've done my best to include the valuable information (e.g. links to sites that aren't trying to steal your info...) and give a little additional info where I could. Where this documentation is lacking (I apologize) know that the links provided do have additional information, resources, and explanation. I am, by no means, an authority on this subject matter – please do your own (additional) research before executing any modification of your own device(s). While there isn't a "plethora" of information out there, you'll find some of the same resources I found. Read through those step-by-step how-to's and fill in some of the blanks with the information given below.

### Magisk

The Magic Mask for Android

Magisk is a "root" application; the current version is an application that must be sideloaded in order to create a custom boot partition that is loaded onto the device.

- [Magisk Repo](https://github.com/topjohnwu/Magisk)
  - [Installation](https://topjohnwu.github.io/Magisk/install.html)
  - [Magisk Download](https://github.com/topjohnwu/Magisk/releases)

### TWRP

TeamWin Recovery Project is a 3rd-party replacement for the stock Android recovery partition. Version 3.1.1-0 (released 17-MAY-2017) was used to write this documentation. During the course of applying this modification I found that TWRP won't allow sideloads of Android versions that are older than it – e.g. if you load a version of TWRP from today, you cannot sideload a version of Android from yesterday (dates are obviously arbitrary). I found that I needed to use version 7.1.2 of Android from Aug 2017 and therefore needed to use version 3.1.1-0 of TWRP as it was the closest (most up-to-date) to that version's release date.

{% highlight bash %}
$ adb reboot bootloader
$ fastboot flash recovery twrp.img
$ fastboot reboot 
{% endhighlight %}

- [TWRP for Google Pixel C](https://twrp.me/google/googlepixelc.html)
- [TWRP for dragon](https://dl.twrp.me/dragon/)

### Kali Nethunter Project

Please read the information at the project page – I would simply be re-creating it here otherwise. My first attempt at getting Kali Nethunter installed on my device involved building the Nethunter package from the information provided by the Kali Nethunter Project repository. Here I found the information necessary to create a build for my device (the Pixel C) which I then attempted to sideload onto my device.

- [Kali Nethunter Project GitLab](https://gitlab.com/kalilinux/nethunter/build-scripts/kali-nethunter-project)

**Google Pixel C Info**

- Kernel ID:  dragon
- Android version:  nougat (Android 7.1)

[Build instructions](https://gitlab.com/kalilinux/nethunter/build-scripts/kali-nethunter-project/-/tree/master/nethunter-installer)

After building the package (using the info at the link above), loading it on the device, and installing the package via TWRP the device would simply fall into a bootloop.  However, after re-installing the OTA image (provided by Google – info further down), I was able to re-install TWRP, Magisk, and find that all the Kali apps were installed...so, win? I'm not entirely sure why this happened. The image that I sideloaded (the one that I built following the instructions provided by the Nethunter project) always bricked my device. Then, sideloading "stock" Android should have destroyed all the other information on the device (...had to sign-in with Google again...) yet the Nethunter applications remained and I was able to configure and use them!? Much more investigation into this whole matter must be done as, clearly, I don't fully understand what TWRP is doing when sideloading an image.

### Kernel Information

Used the info at the below link as a reference - this is the information used when executing the build scripts.

[Nethunter Kernels](https://kalilinux.gitlab.io/nethunter/build-scripts/kali-nethunter-devices/nethunter-kernels.html)

`git clone https://github.com/jcadduono/android_kernel_google_chromeos.git -b nethunter-7.1`

### Pixel C Stock Images

I managed to brick my Pixel C by wiping something (don't remember specifics, unfortunately...) while within TWRP and needed to re-install a stock image. I couldn't get any modified images to install because something required in the "stock image" was wiped out (I think I deleted a partition doing things I didn't fully understand...). Check out the "Credits and Resources below for the Google provided stock images.

Used version 7.1.2 (N2G48C, Aug 2017)

- [Full OTA Android Images](https://developers.google.com/android/ota)
  - Provided by Google for Google devices (Nexus and Pixel)
- [Factory Android Images](https://developers.google.com/android/images)
  - Provided by Google for Google devices (Nexus and Pixel)

## Credits and Resources

- [Linux on Pixel C](https://github.com/pixelc-linux)
- [Download And Install AOSP Android 11 for Google Pixel C](https://www.getdroidtips.com/android-11-google-pixel-c/)
  - This is the guide followed to create the material above
- [F-Droid](https://f-droid.org/)

### From original Nethunter lessons-learned

- [Full OTA Android Images](https://developers.google.com/android/ota)
  - Provided by Google for Google devices (Nexus and Pixel) 
- [Factory Android Images](https://developers.google.com/android/images)
  - Provided by Google for Google devices (Nexus and Pixel) 
- [Magisk Repo](https://github.com/topjohnwu/Magisk)
  - [Installation](https://topjohnwu.github.io/Magisk/install.html)
  - [Magisk Download](https://github.com/topjohnwu/Magisk/releases)
- [TeamWin Recovery Project](https://twrp.me/)

 