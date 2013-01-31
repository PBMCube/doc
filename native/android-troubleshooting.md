# Troubleshooting Issues on Android

## Overview

When your game becomes unresponsive it may be due to a JavaScript exception.  Check the JavaScript logs (see below) to figure out what caused the problem.

## Using Android Devices

General knowledge of how to use Android devices is helpful while solving game problems:

### Uninstalling Games

To uninstall a game on Android:

1.  Open the Settings app.
2.  Select "Applications".
3.  Select "Manage applications".
4.  Select your game from the list.
5.  Tap [Uninstall] and tap OK.

### Force-Quitting Games

To force-quit a game on Android:

1.  Open the Settings app.
2.  Select "Applications".
3.  Select "Manage applications".
4.  Select your game from the list.
5.  Tap [Force Quit] and tap OK.

## Watching JavaScript Logs

To watch the JavaScript logs from a mobile device, connect it to your computer via a USB data cable, then use the `adb logcat` command at a terminal window.

Normally you will want to pair `adb logcat` with the standard `grep` tool to cut out most of the uninteresting log messages.  For example `$ adb logcat | grep JS` will primarily display messages from your game.

You may then pipe the output to a file with `$ adb logcat | grep JS > mylog.txt`.  Hit CTRL+C to terminate the log capture, and open it with `open mylog.txt`.

## Device Communication Failures

The Android Debug Bridge (ADB) may be used to help debug problems with the Android USB connection.  First off, use ADB to list the connected devices at a terminal window:

`$ adb devices`

If you run into problems getting your device to work, first unplug the USB cable and replug it in.  If that does not fix the problem, then try to stop the ADB server on your computer:

`$ adb kill-server`

Also attempt to reboot the mobile device if communication is still unsuccessful.

Further references:

* [Using Hardware Devices](http://developer.android.com/guide/developing/device.html)
* [Android Debug Bridge](http://developer.android.com/guide/developing/tools/adb.html)