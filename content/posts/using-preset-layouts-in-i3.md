---
title: "Using Preset Layouts in I3"
author: Jacob Goldstein
date: 2021-01-14T12:05:56-05:00
draft: false
type: post
categories:
 - linux
 - i3
 - ricing
tags:
 - linux
 - i3
 - ricing
---

While I already knew how to launch programs with my i3 `config` file, I was lacking a way to predefine specific workspace layouts that I would want to launch on startup.

That’s where i3 layouts come in handy.

The first step in creating a layout is to spawn the windows you want to be launched when the layout is deployed.

In this example I created a `monitor` layout, which I use to monitor system stats, crypto prices, the news, and more.

We can save the layout of the target workspace into a `json` file with the following command:

    i3-save-tree --workspace 8 > ./monitor.json
    

In this command `8` is the number of the workspace I wanted to capture.

Opening this file should give you a `json` layout that includes the programs and position of your windows.

We can save this `json` file in a safe place for later use.

Let’s say we want this layout to launch when we log into i3. First, we need to add the following command to your i3 `config` file.

    exec --no-startup-id "i3-msg 'workspace 8: Monitor ; append_layout /home/gideon/.config/i3/layouts/monitor.json'"
    

Here we would replace `workspace 8: Monitor ` with the number and name of the workspace where you want this layout to be deployed.

We would also change the filepath to reflect the actual location of the file where you stored your layout.

What this will do is open up a series of windows corresponding to the position defined in the `json` file. However, these windows will not be populated with any programs.

These windows are placeholders, and as soon as they see a specific program has been launched, it swallows it into that window.

So to get the programs to launch into our layout, we can launch them with our i3 `config`. Here is an example for `urxvt`

What this will do is open up a series of windows corresponding to the position defined in the `json` file. However, these windows will not be populated with any programs.

These windows are placeholders, and as soon as they see a specific program has been launched, it swallows it into that window.

So to get the programs to launch into our layout, we can launch them with our i3 `config`. Here is an example for `urxvt`.

    exec i3-msg 'exec urxvt -name cointop-startup -e fish -c cointop'
    exec i3-msg 'exec urxvt -name gotop-startup -e fish -c gotop'
    exec i3-msg 'exec urxvt -name mop-startup -e fish -c mop'
    exec i3-msg 'exec urxvt -name newsboat-startup -e fish -c newsboat'
    

If you know you want a certain series of windows opened up in a certain way, i3 layouts are for you.

I only covered launching a layout as i3 starts, but you could just as easily bind a hotkey to start a layout for a specific task.
