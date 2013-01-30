# Install the Android Platform

The Game Closure SDK supports building and deploying to
Android devices.

## Install the Android SDK

Download and install the
[Android SDK](http://developer.android.com/sdk/) to your
local machine. If you are using the
[Homebrew](http://mxcl.github.com/homebrew/) package
manager, run:

~~~
$ brew install android
~~~

Running `android` at the command-line brings up a GUI
front-end that will allow you to install various android 
api targets. Install the SDK Platform under Android 4.0.3 
(API 15), Android Support Library in the Extras sections 
at the bottom of the list, and the Android SDK Platform-tools 
in the tools section at the top.

<div class="figure-wrapper">
<figure>
<img src="./assets/android/packages.png" />
<figcaption>All the checked items are required for android installation.</figcaption>
</figure>
</div>

You will then be prompted with an Accept window. Check `Accept All`
and patiently wait for the download and installation to finish.

<div class="figure-wrapper">
<figure>
<img src="./assets/android/accept-all.png" />
<figcaption>Accept installation of the required packages.</figcaption>
</figure>
</div>

## Install the Game Closure SDK Android Component

Simply run `basil install android`. This will automatically
clone the [Android repository](https://github.com/gameclosure/android)
and setup the path in your `config.json`.

If at any point this process fails. You can do the same thing
manually by following these steps:

Clone the Game Closure
[Android repository](https://github.com/gameclosure/android). Switch
to this directory and make sure everything is up-to-date:

~~~
$ git clone git@github.com:gameclosure/android.git
$ cd ./android
$ ./install.sh
~~~

To let basil know where to find the android repository,
update the `config.json` file located in the root of the
basil install:

~~~
{
  "android": {
    "root": "path/to/android"
  }
}
~~~

And make sure all the required sub-modules are updated:

## Build the apk

In the top-level of your project, run:

~~~
$ basil build native-android
~~~

This creates an apk file located at `path/to/project/build/myapp.apk`.

To create a debugging version, just add the appropriate flag:

~~~
$ basil build native-android --debug --clean --no-compress
~~~

Install the application to your device:

~~~
$ adb install -r path/to/project/build/myapp.apk
~~~

Run the game on your device by clicking its icon in the
Application menu!


## Configure the Device

To set up your Android device for development, enable *USB
Debugging*. (This option is located in `Settings > Applications > Development`.)

### Using adb, the Android Development Bridge

List the connected devices in the form: 'serialnumber device':

~~~
$ adb devices
~~~

Issue commands to a specific emulator/device:

~~~
$ adb -s <serialnumber> <command>
~~~

Install an application to a device:

~~~
$ adb install -r <path-to-apk>
~~~

Print logging information to the console:

~~~
$ adb logcat <option> <optional-filter-spec>
~~~

Stop the server if something is hanging:

~~~
$ adb kill-server
~~~

Also attempt to reboot the mobile device if it still hangs.

Reference:
* [Using Hardware Devices](http://developer.android.com/guide/developing/device.html)
* [Android Debug Bridge](http://developer.android.com/guide/developing/tools/adb.html)