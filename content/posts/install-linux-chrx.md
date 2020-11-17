---
title: Install Linux with CHRX
author: Jacob Goldstein
type: post
date: 2020-09-16T19:00:00
categories:
  - Linux
  - Chromebook
tags:
  - Linux
  - Chromebook
---

**Note**: to do this, all your chromeOS data will be wiped. I recommend reading through all of this post before starting.

This post is about how I got my chromebook dual booting galliumOS.


### Step one: go into Developer mode.
Developer mode is a setting that lets you do development. It's not on by default because it also makes it easier to install a malicious package. (APKs, or android packages, can't be opened without developer mode.)

To turn on developer mode, hold down the esc and reload key, then tap the power key. You will be greeted by a very scary popup saying "CHROMEOS IS MISSING OR DAMAGED." Hit control-D, and then it will say something along the lines of "START DEVELOPER MODE? all your data will be wiped." press enter. It will start.

### Step two: login
Your computer will restart and say "OS VERIFICATION IS OFF." Press control-D.

since starting Developer mode wiped all your data, you will have to log in again, etc. If you don't want to that, you can just go into guest mode.

### Step two: install Chrx
You will have to install and run Chrx, which is really easy. Just one curl command:

```
cd ; curl -Os https://chrx.org/go && sh go
```

Copy and paste that command in chrosh shell (ctrl-alt-T and then type shell.)

Go through the install script. At the bottom, it will have a "diagnosis." If it says it will only succeed if it has a firmware update keep that in mind. Reboot.

## Step two.two: Update firmware
If you need to update your firmware, you will have to download MrChromebox. Type this in the crosh shell:


```
cd; curl -LO https://mrchromebox.tech/firmware-util.sh && sudo bash firmware-util.sh 
```
You will see a menu.


Press 1 to update the firmware. (When you do this, you will install BIOS [Basic Input/Output System]).

### Step three: repeat "step six"
Type this command in chrosh (again):

```
cd ; curl -Os https://chrx.org/go && sh go 
```

That will install GaliumOS.

### Step four: Get into GalliumOS
Reboot. This time, when you have to type control-D, type control-L. It will go into BIOS, then GalliumOS. Username is chrx and password is chrx.


Other chrx info:

**chrx** can accept several command-line options:

```
Usage: chrx [ option ... ]

Options
   -d DISTRIBUTION OS-specific distribution to install [galliumos]
                     galliumos, ubuntu, lubuntu, xubuntu, kubuntu, edubuntu,
                     fedora
   -e ENVIRONMENT  distribution-specific environment [desktop]
                     galliumos: desktop
                     ubuntu etc: desktop, minimal, standard, server
                     fedora: desktop, workstation, kde, xfce, lxde, mate,
                       cinnamon, sugar
   -r RELEASE      distribution release number or name [latest]
                     galliumos: latest, 3.0, bismuth, 2.0, xenon, nightly
                     ubuntu etc: latest, lts, dev, 16.04, 16.10, xenial, etc
                     fedora: latest, 23, 24, 25
   -a ARCH         processor architecture (i386, amd64) [amd64]
   -m MIRROR       distribution-specific download mirror [primary]
                     galliumos: ny1.us, va1.us, rb1.fr
   -t TARGETDISK   target disk (/dev/mmcblk1, /dev/sdb, etc) []
   -p PACKAGE      additional packages to install, may repeat []
                     kodi, minecraft, steam, etc, see chrx.org for more
                     (not yet supported on fedora)
   -H HOSTNAME     hostname for new system [chrx]
   -U USERNAME     username of first created user [chrx]
   -L LOCALE       locale for new system [en_US.UTF-8]
   -Z TIMEZONE     timezone for new system, Eggert convention [America/New_York]
                     America/San_Francisco, Europe/Amsterdam, Etc/UTC, etc
   -n              disable success/failure notifications
   -s              skip all customization, install stock OS only
   -y              run non-interactively, take defaults and do not confirm
   -v              increase output verbosity
   -h              show this help

Default values are shown in brackets, e.g.: [default].

If TARGETDISK is not specified, chrx will select the internal SSD.

```

<a name="packages"></a>
### packages

**chrx** can install additional software packages after installing
your new operating system, using the `-p PACKAGE` option.

You can install any package in the Ubuntu repositories via this
method, plus a few non-Ubuntu packages for which **chrx** has
special handling, and some aliases for convenience:

- `minecraft` installs [Minecraft](https://minecraft.net/)
- `steam` installs [Steam](http://store.steampowered.com/about/)
- `kodi` installs [Kodi Media Center](http://kodi.tv/about/)
- `chrome` installs Google Chrome
- `admin-misc` is an alias for `"ssh tmux rsync vim"`
- `dev-misc` is an alias for `"arduino geany geany-plugins ruby"`

To install multiple packages from the **chrx** command line, you
can repeat the `-p PACKAGE` option as many times as you need, or
you can quote the argument, e.g.: `-p "gimp blender inkscape"`.


### examples

[GalliumOS](https://galliumos.org/) Desktop (latest), verbosely:

`chrx -v`

[GalliumOS](https://galliumos.org/) Desktop (latest), plus packages:

`chrx -p "minecraft steam kodi"`

[Lubuntu](http://lubuntu.net/) Desktop (latest):

`chrx -d lubuntu`

[Ubuntu](https://ubuntu.com/) Standard, version 16.04, system name `hal`, first user `dave`, including some administrative tools:

`chrx -d ubuntu -e standard -r 16.04 -H hal -U dave -p admin-misc`


<!--
<a name="advanced-usage"></a>
### advanced usage

You may choose to host or cache these installation files yourself.
There are many good reasons to do so, especially if you'll be doing
a large number of installations. However, setup can be somewhat more
complicated, and instructions are outside the scope of this README.

To point **chrx** at your cache, just set the `CHRX_WEB_ROOT`
environment variable before running the `chrx` script, like this:

```
export CHRX_WEB_ROOT="http://myserver/chrx"
cd ; curl -O $CHRX_WEB_ROOT/go && sh go
```
-->

<a name="compatibility"></a>
## compatibility


<a name="chromebooks"></a>
### chromebooks
status            |CPU family                           |notes
:----------------:|-------------------------------------|------------------
:white_check_mark:|Intel Haswell                        |[Firmware update](https://mrchromebox.tech/#fwscript) available (RW_LEGACY)
:white_check_mark:|Intel Broadwell                      |[Firmware update](https://mrchromebox.tech/#fwscript) *recommended* (RW_LEGACY)
:white_check_mark:|Intel Skylake                        |[Firmware update](https://mrchromebox.tech/#fwscript) *recommended* (RW_LEGACY)
:white_check_mark:|Intel Kaby Lake                      |[Firmware update](https://mrchromebox.tech/#fwscript) *recommended* (RW_LEGACY)
:white_check_mark:|Intel Bay Trail                      |[Firmware update](https://mrchromebox.tech/#fwscript) **required** (RW_LEGACY)
:white_check_mark:|Intel Braswell                       |[Firmware update](https://mrchromebox.tech/#fwscript) **required** (RW_LEGACY)
:white_check_mark:|Intel Apollo Lake                    |[Firmware update](https://mrchromebox.tech/#fwscript) **required** (RW_LEGACY)
:question:        |Intel Sandy/Ivy Bridge               |Requires SeaBIOS with Legacy Boot capability
:question:        |Intel Pineview                       |Requires SeaBIOS with Legacy Boot capability
:x:               |ARM                                  |ARM support is very unlikely

If you do not know the CPU in your device, check here: https://wiki.galliumos.org/Hardware_Compatibility

<a name="operating-systems"></a>
### operating systems

status| OS  | distribution | notes
:----:| --- | ------------ | -----
:white_check_mark:|Linux|[GalliumOS](https://galliumos.org/)|Derived from Xubuntu, developed specifically for compatibility and optimized performance on Chromebook hardware.
:white_check_mark:|Linux|[Lubuntu](http://lubuntu.net/)|A light-weight variant of Ubuntu, with the LXDE desktop environment.
:white_check_mark:|Linux|[Xubuntu](http://xubuntu.org/)|A light-weight variant of Ubuntu, with the Xfce desktop environment.
:white_check_mark:|Linux|[Kubuntu](http://kubuntu.org/)|Ubuntu with the KDE desktop environment.
:white_check_mark:|Linux|[Edubuntu](http://edubuntu.org/)|Full Ubuntu plus application bundles used in educational settings.
:white_check_mark:|Linux|[Ubuntu](https://ubuntu.com/)|The standard full Ubuntu distro.
:white_check_mark:|Linux|[Fedora](https://fedoraproject.org/)|New 20161121!
:x:|FreeBSD||Work in progress!


<a name="recommendations"></a>
### recommendations

Chromebooks perform best with lighter-weight operating systems and desktop environments, and they often require updated kernel drivers to support their new and tightly integrated hardware.

Selecting a distribution which meets these needs is therefore an important part of Linux-on-Chromebook happiness. While any updated distro will work for ordinary tasks, there are a few that stand out:

- **GalliumOS** is optimized specifically for Chromebooks. It scores well on all metrics, looks great, and installs quickly. Some memory-hungry applications (e.g. Steam games) perform *best* on GalliumOS thanks to careful optimizations. GalliumOS is the default distro installed by **chrx**.
- **Lubuntu** also scores and performs well. It uses significantly less RAM than other distros.
- **Xubuntu** is another good choice. It's a bit heavier-weight than Lubuntu, but still performs very well.
- **Fedora** comes in several "spins" (desktop environments, selected with `-e ENVIRONMENT`), some of which (lxde) are lightweight, and some of which (desktop (gnome), default) are heavier. A few sample spins have been added to measurements below.
- I would not choose standard, full, Ubuntu for a Chromebook. It is perfectly usable, bit it's heavier and suffers in performance, without offering any important benefits. Memory use starts higher and increases much more quickly as you use the desktop apps (not reflected in measurements below). If your Chromebook model has 4GB of RAM, the performance differences are reduced but not eliminated.


#### sample measurements

distribution&sup1; | disk space&sup2; | RAM use&sup3; | install time&#8308; | recommended? |
------------------ | ----- | ----- | ------- |:---:|
GalliumOS 3.0      | 3.2GB | 320MB | 10 mins | :white_check_mark: |
GalliumOS 2.0      | 2.5GB | 291MB | 9 mins  | :white_check_mark: |
GalliumOS 1.0      | 2.8GB | 287MB | 10 mins | :white_check_mark: |
Lubuntu 15.10      | 2.7GB | 227MB | 18 mins | :white_check_mark: |
Lubuntu 16.04      | 3.1GB | 185MB | 19 mins | :white_check_mark: |
Xubuntu 15.04      | 3.0GB | 360MB | 22 mins | :white_check_mark: |
Ubuntu 15.04       | 3.5GB | 440MB | 28 mins | :x: |
Kubuntu 15.10      | 4.2GB | 613MB |         | :x: |
Fedora 24 (lxde)   | 2.9GB | 182MB | 20 mins | :white_check_mark: |
Fedora 24 (cinnamon)| 3.8GB | 384MB | 27 mins | :white_check_mark: |
Fedora 24          | 4.5GB | 647MB | 27 mins | :x: |


1. All distributions were installed with the `desktop` environment option, except where noted.
1. Disk space can be reduced by removing unwanted packages. The number shown reflects the default install for the desktop environment.
1. RAM use is measured after graphical login, connecting to Wi-Fi, and opening one window of the default Terminal program to run `/usr/bin/free` after a couple minutes for the system to stabilize. The number shown is an average of several tests, and variance is very low (2-3%).
1. Installation time will vary greatly depending on your Internet connection, but the ratios should be representative.


## test suite

"Working" is defined as:

- system boots cleanly and quickly
- installation remnants are cleaned up
- swap and compressed RAM are enabled
- proper drivers are properly loaded
- trackpad works (standard & australian)
- trackpad settings are usable
- audio works, including after sleep/wake
- wireless works, including after sleep/wake
- function keys for backlight are functional
- function keys volume control are functional
- microphone input works
- webcam input works
- power management sleeps system when lid closed
- power management wakes system when lid opened
- no user configuration is required for basic use

This list might evolve. Your input is welcome!


## alternatives

**chrx** is a command-line installer which requires requires no physical
media or other preparation to install. It allows you to dual-boot, so you
can choose Linux or ChromeOS each time you turn on your Chromebook. This
is a flexible setup, well-suited for many users, but of course not all.

Consider these alternatives:

- Single-Boot instead of dual-boot. If you don't need or want ChromeOS,
you don't need to keep it. You can install directly from a Linux ISO
written to a USB/SD device. As with dual-boot, you might need to update
firmware (full ROM/UEFI is recommended for single-boot only), and
[GalliumOS](https://wiki.galliumos.org/Installing) is the distro of choice.
- [Crouton](https://github.com/dnschneid/crouton) allows you to run ChromeOS
and Linux simultaneously, instead of dual-booting like **chrx**.
This arrangement has a few drawbacks, but if you spend most of your time in
ChromeOS and your Linux needs are limited, it should serve well.
- [Crostini](https://chromium.googlesource.com/chromiumos/docs/+/master/containers_and_vms.md) is Google's Linux-apps-in-containers-inside-virtual-machines-on-ChromeOS project. It's only available on newer Chromebook models, so be sure to check the compatibility list first.

