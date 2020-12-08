---
title: "Linux Ricing Checklist"
author: Jacob Goldstein
date: 2020-12-08T08:55:35-05:00
draft: false
type: posts
categories:
 - linux
 - ricing
tags:
 - linux
 - ricing
---

I just started ricing at the start of August 2019. 
So I made this list of things you might want to know when 
getting started with ricing your setup so that I couldn't 
forget it easily.

Hopefully, it can be useful for you, too.

NOTE: The listed programs is mostly applied to 
Linux-based systems. 
You can look for some alternatives if you're using 
anything else. 
Sorry, can't help much with that. 


== A display server
In order to fully make use of window programs like 
Firefox, Inkscape, GIMP, Blender, and many others, you have 
to install a display server (or windows server). 
Otherwise, you would be stuck using with a command line. 

NOTE: This is required for any setup with a graphical 
desktop.

There are 
https://en.wikipedia.org/wiki/List_of_display_servers[many display servers out there]
but one of the more popular choices are https://www.x.org/wiki/[Xorg] 
(an implementation of X protocol) and 
https://wayland.freedesktop.org/[Wayland].

If your hardware is a bit old, I recommend to stick with
Xorg since it is older thus more developed than Wayland.
Wayland is still a relatively new technology still in development 
but still keep an eye for it since it is meant to replace X 
with simpler options. 

Also, I recommend to look at their respective Arch Linux wiki entry 
if you want to get started. 
(Pretty much I recommend the Arch Linux wiki for most of the 
Linux stuff, really.)


== A desktop environment/window manager
In order to have that graphical desktop experience, you 
either need a _desktop environment_ or a _window manager_ 
(or even both).

A window manager does what its name does: manages and controls 
windows from its appearance, content, and behavior.
There are 
https://wiki.archlinux.org/index.php/window_manager[many choices to choose from]
but personally I recommend https://i3wm.org/[i3], https://swaywm.org/[Sway], 
https://wiki.archlinux.org/index.php/Bspwm[Bspwm], and 
https://awesomewm.org/[awesome]. 

Usually with a window manager, you can extend more stuff with it 
such as a status bar and a lock screen to improve your 
desktop experience.
Anyways, you should try and experiment with the configuration 
of the window manager of your choosing.

Meanwhile, a desktop environment is a more detailed setup 
built on top of a window manager. 
They have more built-in stuff like a status bar, 
a session manager, a display manager, and a window manager of 
their own.

Like window managers, 
https://wiki.archlinux.org/index.php/Desktop_environment#List_of_desktop_environments[You have many choices] 
here.
For my personal recommendations, https://xfce.org/[Xfce] and 
https://www.kde.org/plasma-desktop[KDE Plasma] is the 
top-tier choices.

Usually, desktop environments let you replace their 
window manager (or any of their components, if they provided 
one). 
For example, you can install Xfce and replace their built-in 
window manager (https://docs.xfce.org/xfce/xfwm4/start[Xfwm]) 
with i3wm.

Don't forget to use some themes for the desktop environment 
of your choice.

TIP: Always check for the requirements of the window manager 
or the desktop environment before trying it. 
It can affect performance or simply won't work because 
of incompatibility.


== A compositor
A https://en.wikipedia.org/wiki/Compositing_window_manager[compositor] 
(or a composite manager) is a program that provides 
an off-screen buffer for application windows. 
Thus, repainting and rendering application windows will mitigate 
against common graphical issues such as screen tearing or leaving a 
"trail" or a black block.
Those issues will be way more obvious when moving your windows or 
using an application with a lot of moving parts on your screen. 
(I can't record it since it's not present when viewing it in a video.)

It can also provide additional processes with those application 
windows such as adding transitions, adding animations, and 
applying opacity for the windows. 
In other words, it can add pizzazz to your setup.

TIP: Like window managers, always check for the requirements 
before using it. 
Certain compositors can only support certain setups or 
will break under certain conditions in your setup.

One of the more popular compositors are 
https://github.com/yshui/compton[Compton] for X window system 
and https://swaywm.org/[Sway] for Wayland.

Once you have configured the compositor, you can certainly see 
some notable differences with it.

Since I have installed Xorg which is an implementation of the X window 
system, I'm using Compton. 
The following videos are demonstrations using without and with Compton 
running in the background.

Here's a video of my setup using no Compton.

video::assets/compton-less-demo.mp4[width=100%]

Here's another video of my setup using Compton this time. 
Take note that it uses the default config located at 
`/etc/xorg/compton.conf`.

video::assets/compton-demo.mp4[width=100%]


== A display manager
A display manager is a graphical interface for logging in a session. 
It could be pretty useful for those who are using with multiple users 
that might be intimidated with using a TTY as their first screen. 
Most importantly, it could be used for additional swag. 

Aside from giving the user login interface a makeover, it can also 
do other things such as authenticating users and session management. 

https://wiki.archlinux.org/index.php/Display_manager#List_of_display_managers[There is a list of choices out there] 
and my pick is https://github.com/CanonicalLtd/lightdm/[LightDM] 
since I find it easy to start and it does have a cool login interface. 


== GUI library themes
GUI library such as https://www.gtk.org/[GTK] and 
https://www.qt.io/[Qt] might have a unified configuration that 
describes the widgets appearance, color scheme, and fonts.

I'll be mainly discussing on GTK theming since a lot of widely used 
programs are built with it. 

https://www.gtk.org/[GTK] is a cross-platform free and open source GUI library. 
Popular programs built (as of this writing) with the library include 
https://www.mozilla.org/en-US/firefox/new/[Firefox], 
https://www.thunderbird.net/[Thunderbird], 
http://www.gimp.org/[GIMP], and http://www.inkscape.org/[Inkscape].

There are many ways on configuring your color scheme and icon sets but 
I recommend to start with http://wiki.lxde.org/en/LXAppearance[LXAppearance] 
or https://github.com/themix-project/oomox[oomox]. 
Even better you could use them to take a look at a GTK config file and edit 
it yourself afterwards.

You could also not customize it and leave it to the distro. 
For Arch Linux, it has Raleigh as the default GTK theme which looks 
very dated if you ask me.

.GTK Raleigh theme
image::assets/gtk-raleigh-theme-demo.webp[GTK Raleigh theme]

For my custom configuration, I chose the https://github.com/NicoHood/arc-theme[Arc] 
theme along with its https://github.com/NicoHood/arc-icon-theme[icon set] simply 
because they're the popular choice. I also think the darker scheme is pretty 
cool.

.GTK Arc Darker theme 
image::assets/gtk-arc-darker-theme-demo.webp[GTK Arc Darker theme]

You can look for more GTK themes at https://www.gnome-look.org/[GNOME Look].

NOTE: Not all GTK-built programs follow and apply the configuration. 
You could also set individual themes for each program given that they provided one.


== Color scheme generator
Having your own color scheme for your setup is very great. 
However, if you're inexperienced with choosing your own colors, 
a color scheme generator can help.

There are a lot software built for it such as https://coolors.co/[Coolors], 
https://color.adobe.com/create[Adobe Color], and 
https://colorpalettes.net/[a color pallete sharing site] but 
there are two particular program that I personally recommend 
because they're specifically made for ricing.

=== pywal
Enter https://github.com/dylanaraps/pywal[pywal], a program that easily generates a 
color scheme and replace it with your already existing terminal setup.
You could also make some templates in order to apply it to other programs like 
https://github.com/DaveDavenport/rofi[rofi], for example.

One of the most popular highlights of pywal is that you can generate color schemes 
with images.

So far, I'm content with the color scheme generated from 
https://www.reddit.com/r/wallpapers/comments/cckpj0/i_made_this_simple_and_clean_drawing_over_the/[this image].
It's pretty easy on the eyes and it is also cool to be background image for 
your desktop.

You can certainly automate it to make it as your theme selector similar 
to how https://www.youtube.com/watch?v=Es79N_9BblE[Luke Smith] did with his setup.
Or just like how 
https://www.reddit.com/r/unixporn/comments/973qcn/i3rofipywal_automated_theme_switching_with_rofi/[this ricer from `/r/unixporn` made rofi to be the theme selector].

=== wpgtk
wpgtk, as it is described in its https://github.com/deviantfero/wpgtk[own GitHub page], 
is a colorscheme, wallpaper and template manager for *nix-based systems. 
It is what it is.

* It can generate and manage different color scheme with 
https://github.com/dylanaraps/pywal[pywal] which I discussed it shortly earlier.
* It can manage wallpapers and templates.
* Comes with a graphical user interface built with https://www.gtk.org/[GTK].

It is a pretty cool tool and can turn ricing into a more satisfying 
experience with the convenience it offers. 
I fully recommend looking into this tool if you want a cool color scheme 
generator and a manager for common ricing tasks.


== A notification system
A status bar is not enough fill up some info especially if it's not 
needed that much. 
A desktop notification system could be handy for those situations. 
It can also be useful for immediate feedback that is shortly 
not needed after. 

In order to setup a notification system working, you need two components:

* a notifier that sends notifications
* a notification daemon that recieves those notifications

NOTE: If you're using with a desktop environment, usually it already 
has a notification system installed. Feel free to skip this section 
if you want.

For the former, https://developer.gnome.org/libnotify/[`libnotify`] 
(with `notify-send`) is the toolbelt for that.

For the latter, you have more choices. 
In my setup, I have https://dunst-project.org/[Dunst] since I see 
it included in a lot of posts at `/r/unixporn`. 

Dunst is also easy to configure and extend.
You can change the color of the text and background, change the 
appearance for notifications of varying urgency levels, and integrate 
scripts that'll run whenever a certain type of notification has been 
recieved. 
It's pretty fantastic.

One very useful example in my case is making a notification for screenshots. 

I made a script which takes a screenshot which will be binded with the `PrintScr` key 
which will be used in i3. 

In i3, running a script takes place in the background so there's no way to know 
if the screenshot capture is a success or not unless you send some data to a 
server. Simply sending a notification with `notify-send` while running Dunst in the 
background can go a long way.

.Using dunst for screenshot notifications
image::assets/dunst-screenshot-demo.webp[Using dunst for screenshot notifications]

I also made it to send notifications for delayed screenshots. 

video::assets/dunst-delayed-screenshot-demo.mp4[width=100%]

If you're curious about the screenshot script, you can find it 
https://github.com/foo-dogsquared/dotfiles/blob/master/.scripts/maim-screenshot.sh[here].


== A dotfiles manager
Managing your dotfiles can be tricky since different programs have 
different ways on where to store their configuration files.

NOTE: Dotfiles simply means your configurations of the installed 
programs. Its name also came from how Linux considers a file/folder
with a period in front of the name to be hidden (i.e., `.config`, 
`.vimrc`, `.bashrc`). 

If you would continue with no tool at all, you would most likely:

* edit and manage it by hand
* create a folder where all of your dotfiles are in and symlink it 
in various locations
* create a script that'll manage your dotfiles for you ;p

Depending on your experience, it could be elegant or a nightmare.
Which is why I totally recommend to use a dotfiles manager.

https://wiki.archlinux.org/index.php/Dotfiles[You have some choices] 
(or you know create one yourself) for managing your dotfiles easily.
For me, I chose https://www.gnu.org/software/stow/[`stow`] since it is 
widely distributed among Linux-based systems. The runner-up is 
https://github.com/TheLocehiliosan/yadm[`yadm`] which integrates the 
concepts usually found in Git.


== A backup tool
Imagine spending time for your setup that you visioned then having 
to put all of that down for a ridiculous reason.

That's what backups are for. 
It's a simple thing to backup your dotfiles whether through simple 
copy-pasting it in another storage device, an online drive, or 
a self-hosted server. 

For my dotfiles, I simply use a remote Git repo as my online "backup". 
I also have the benefit of putting my dotfiles under version control 
which means I can easily experiment with my settings. 


== Anything else?
Your usual programs, of course. 
Your web browser, text editor, terminal, file manager, or even some 
games (granted that they support it on Linux). 

If you feeling adventurous and want to explore more, you can 
https://wiki.archlinux.org/index.php/List_of_applications[view this application list on Arch Linux wiki].
Or explore around on GitHub, GitLab, or wherever that is. 

You can also check out 
https://wiki.archlinux.org/index.php/Desktop_environment#Custom_environments[this list of components] 
if you want more stuff for your desktop setup. 

If you want some inspiration for your ricing journey, be sure 
to check out https://www.reddit.com/r/unixporn/[`/r/unixporn`]. 
The amount of creativity is overflowing from the community. 

I also have my own set of dotfiles that you can check it 
up on https://github.com/foo-dogsquared/dotfiles[my GitHub repo] 
(also have it on https://gitlab.com/foo-dogsquared/dotfiles[GitLab as a mirror]).

== Further looking
You can find most of the valuable stuff on https://wiki.archlinux.org/[Arch Linux wiki]. 
Most of the concepts apply even when you're not using Arch Linux. 
The documentation is pretty thorough and periodically updated so be sure to 
check it out often. 

=== Web
https://wiki.archlinux.org/index.php/Desktop_environment[_Desktop environment_ from *Arch Wiki*]::
An Arch Linux wiki entry on desktop environments. 
Features a list of desktop environments with their own 
wiki page and a list of components that make up a 
graphical environment.

https://wiki.archlinux.org/index.php/Desktop_notifications[_Desktop notifications_ from *Arch Wiki*]::
An entry on desktop notifications on Arch Linux wiki. 
Also contains a list of programs to look out for and 
information on setting up one.

https://wiki.archlinux.org/index.php/Display_manager[_Display manager_ from *Arch Wiki*]:: 
An Arch Linux wiki entry on display managers. 
Features a list of display managers with their own 
wiki page.

https://wiki.archlinux.org/index.php/Dotfiles[_Dotfiles_ from *Arch Wiki*]::
It's a page on Arch Wiki that shortly describes about dotfiles. 
Also features a list of programs that can help you process and 
manage your dotfiles.

https://github.com/addy-dclxvi/i3-starterpack[_i3-starterpack_ GitHub repo by *addy-dclxvi*]:: 
A great start on starting with your i3 setup and can also teach 
a little of bit of ricing.

http://brandon.invergo.net/news/2012-05-26-using-gnu-stow-to-manage-your-dotfiles.html[_Using GNU Stow to Manage Your Dotfiles_ by *Brandon Invergo*]::
It's a short but sweet article on https://www.gnu.org/software/stow/[GNU Stow], 
a symbolic link farm manager suitable for controlling configuration files.

https://wiki.archlinux.org/index.php/window_manager[_Window manager_ from *Arch Wiki*]::
An Arch Linux wiki entry on window managers. 
Provides a list of window managers with their own 
wiki entry that documents the installation and configuration 
process.

=== Video
https://www.youtube.com/playlist?list=PL5ze0DjYv5DbCv9vNEzFmP6sU7ZmkGzcf[i3wm series from *Code Cast*]::
A fantastic video series by Code Cast on getting started with i3 and ricing. 
It's a bit outdated (heads up for the part where you setup for rofi) 
but most of the concepts still apply today.

