# Congrats on your Hacker Development Kit!

Please note the "last-modified" date on this page - OSVR is a fast moving set of projects, so limitations mentioned here may no longer apply when you read this.

## Caveats/Limitations
- The current default configuration file on Windows assumes an HDK 1.3, direct mode rendering, and fused IMU and video-based (aka positional) tracking. If you are using a 1.2 (thumbscrew-adjusters on the lenses, not sliders), or can't/don't want to use direct mode, you'll want to switch config files. There are config files with self-documenting names included.
- The OSVR Server currently shows a console window that can be minimized, but should not be closed while you're using OSVR applications. A more appealing or invisible interface is coming.

## Setup

### Connect the HDK
There are a few connections to make: the headset to the beltbox, power from the wall to the beltbox, and HDMI and USB between the beltbox and your computer. Order does not particularly matter. You'll want to make sure that you have the beltbox held or clipped in such a way that cables don't tug during use.

If you're using the video-based tracker, make sure you get the sync cables set up at this point as well, too.

Once you have the headset, HDMI, power plugged in, the HMD should be recognized as a new display on your computer.  Windows users, you'll want to choose to "extend your display" in "Display Properties". (Linux users: you can extend your display to it or you can run a separate X screen on it, your choice depending on how you want to use it.)

It will likely show up as a 1080x1920 "Portrait" display by default. This is the highest-performance mode. However, at this time most applications don't work with it in that mode, so you'll want to select the 1920x1080 resolution instead. (This doesn't mean you have to change the "Rotation" setting - just choose the alternate resolution and the HMD will perform the rotation internally.)

### Install the driver pack (optional, recommended)
If you're on Windows, there's a driver pack installer that can improve your experience. While not necessary for basic use, it does provide better names for devices in the Device Manager, groups device components logically with corresponding icons in the "Devices and Printers" window, and on Windows 8.1 and earlier, is required to use the OSVR HDK control software to upgrade firmware, etc. (Windows 10 already includes the appropriate driver there, but the other benefits still apply.)  You can get the latest release here: <https://github.com/OSVR/OSVR-HDK-Windows-Drivers/releases> with some (continually slightly outdated) documentation if you get stuck here: <https://github.com/OSVR/OSVR-HDK-Windows-Drivers/blob/master/Inf-Installer-Instructions/README.md> (typically the driver pack has more functionality associated with it than described in those docs).

### Get OSVR Server
OSVR Server is part of the OSVR software framework, and provides the system for accessing device data, configuring peripherals, etc. The HDK drivers come bundled in the main OSVR Core package (which includes the server), and your HDK can be auto-detected, so you won't need to edit any config files unless you want to connect additional input devices.

There are two ways of getting the OSVR Server: the installer and build snapshots. Since the installer is not currently automatically updated, the best way is to download an OSVR Core snapshot, linked from the [Using OSVR][using] page. If you're using a 64-bit version of Windows, either 32 or 64 bit will work (and be compatible with both 32 and 64-bit applications), so just pick one.  (Linux users: please see the [OSVR-Core][] repository for [build instructions](https://github.com/OSVR/OSVR-Core/wiki/Linux-Build-Instructions).)

In any case, running the `osvr_server` application should open a command-line window displaying some messages. If everything is working right, you'll see a line that says something like:

```
Added device: com_osvr_Multiserver/OSVRHackerDevKit0
```
If you are on Linux on Mac and do not get this output line, refer to the [known issues].

You can minimize this window, but make sure to keep it running as long as you'll be using OSVR applications.

[OSVR-Core]: https://github.com/OSVR/OSVR-Core/
[using]: http://osvr.github.io/using/
[known issues]: https://github.com/OSVR/OSVR-Core/wiki/Linux-Build-Instructions#known-issues-temporary

### Adjust the Optics (HDK 1.0, 1.1, 1.2)
[[assets/HDK-optics-adjustment.png]]

This diagram of HDK optics adjustments ([[printable full-page PDF here|assets/HDK-optics-adjustment.pdf]]) shows what the adjustments are. You'll want to adjust them while wearing the display and with an image displayed on the screen (plugged in, etc.), but one eye at a time (close the other eye). You can use your glasses (or lack thereof) to estimate approximately where you'll want to start the focus control at, then adjusting the IPD until the lens feels and looks "centered" with your eye and all parts of the screen are equally sharp.

### Adjust the Optics (HDK 1.3)

The sliders on the bottom of the 1.3 adjust focus in diopters. If you normally wear glasses, you may be able to take them off and adjust the focus sliders instead to see a sharp image. Otherwise, just adjust them until you see a sharp image in both eyes, likely when both eyes are around the tick-mark labeled 0.

## Software

### Tracker Viewer
The first application we suggest you try isn't glamorous, but it's handy for checking to make sure that things are working. On the [Using OSVR][using] page, you'll see a download link for the OSVR Tracker Viewer. Download and run that (with the OSVR Server running!), and you'll get a small window with some 3D arrows in it. If you're 3D-graphics savvy or VR-savvy, you'll probably figure out what they are and what they mean, but the important part in general is to just verify that the small arrows in the middle move when you rotate the headset. (You can right-click and drag to zoom in to see it better)

Of course, you can skip this step, but if you have problems, someone will probably ask you what you see when you run Tracker Viewer.

### The "Palace" Demo
The [OSVR Unity Palace Demo](https://github.com/OSVR/OSVR-Unity-Palace-Demo/releases) [(source repo)](https://github.com/OSVR/OSVR-Unity-Palace-Demo) is a visually-rich environment to look around and explore in using OSVR-supported hardware, including the HDK. The first link contains binary downloads for Windows: just download and run (make sure the OSVR server is running!), and if desired move around in the environment with a gamepad or keyboard and mouse. On the start-up screen you'll want to choose the display that your HDK is configured as, and the 1920x1080 full HD resolution.

Note that in this application, as with all Unity applications, if you "click away" from the app (so it is no longer the focused/active application) it will stop updating the OSVR plugin, and thus the display will appear to freeze (since no tracking data is being received). Most of the time you can just click the taskbar icon for the application to restore focus and pick up where you left off.

## Help!

If you're having hardware or software problems in general, just open a help ticket with [OSVR Support](http://support.osvr.com).

If you'd like to develop OSVR software or contribute in some way, please see the [Developer Portal at osvr.github.io](http://osvr.github.io) to join the development discussion/mailing list, and see the list of projects and their contribution information.

Support tickets are monitored by multiple people so they'll be handed smoothly by the best person available and suited to your question. GitHub and the developer mailing list are the main ways to reach current developers contributing to OSVR.

- It's not recommended to ask about problems or post questions elsewhere (forums/reddit, twitter, etc.) if you want a developer or "official" response, since those aren't venues we (developers/technical people) necessarily frequent daily or control the "official" accounts on.
- As a general rule of open-source communities, and thus in OSVR as well, it's usually considered rude to email a developer personally with a question. Among other reasons, it only allows a single person to handle your question (when there may be others who could do so and perhaps better) and doesn't archive a potentially useful exchange in searchable archives. (Don't be surprised if your email gets forwarded to the support ticket system if you do this.)