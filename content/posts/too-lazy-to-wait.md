---
title: "Too Lazy to Wait - skipping the 2b2t queue"
author: Jacob Goldstein
date: 2021-01-31T22:13:12-05:00
draft: false
type: post
categories:
 - webdev
 - web-dev
tags:
 - webdev
 - web-dev
---

The oldest anarchy server in Minecraft, known as 2b2t.org, has a very long queue. This was implemented due to the server’s growing popularity.

When you log on you are connected to the queue. The queue looks something like this:

![](https://cdn-images-1.medium.com/max/2000/0*FCcbiCr6qid3a3Q3.png)

Sometimes the queue can even go up to 8000 players! Well, with this method you can practically skip the queue completely.

The way this works is by using a proxy that you can connect to the queue with from your phone. Using a discord bot you can send commands to it like ‘stop’ and ‘start’ to stop/start the queue. This is very useful when you are on the go!

You can connect to the 2b2t queue on the go and then play immediately when you get home!

## How to install

The creator of this program warns you to read the source code first to make sure he is not stealing your information.

I looked through it and it looks safe. These are the steps that they have given on the website:
```
 Read the code to ensure i’m not stealing your credentials. i’m not, but you shouldn’t take my word for it. If you don’t know how to read it, downloading stuff off the internet and giving it your password is probably a bad idea anyway.
 Download node.js and install it. On non-windows platforms, you also need npm.
 Download this repository with the green button (top right of this page). If you downloaded it as zip, unzip it.
 Open a terminal and navigate to the folder you downloaded it
 Run npm install
 Change directory to 2b2w/
 Run npm install
 Inside the directory 2b2w/ copy secrets.json.example and name it secrets.json. Fill out your minecraft information in the file. Note that you must use your email adress and not your minecraft username.
 If you so wish, edit the configuration in config.json. (On Linux ports below 1024, including port 80, require you to run the program with administrator rights.)
 You need to create a discord bot. Follow this tutorial up until the programming part.
 In the directory above edit the file auth.json and replace BOT_TOKEN with your bots token
 For trust reasons, this tool does not update automatically. Check back here once in a while to see if there are any updates.
```
That will install the program. Now to use it you have to follow his instructions again:
```
 Run node discordBot.js (you might need to run this as administrator/sudo)
 Your bot should be online now, in discord it should show up with “Queue stopped.”
 See below for commands on how to start the queue.
 You can access the original 2bored2wait web interface from [http://localhost](http://localhost/)
 Once the queue reaches a low number, connect to the minecraft server at address localhost. Currently, you have to connect BEFORE reaching the end of the queue or you will not spawn in the world correctly (I'm told that sneaking around and right-clicking things eventually makes you spawn correctly but I was not able to verify that).
 After you log off, click the “stop queuing” button. This is really important, as you will not actually disconnect from 2b2t until you do that.
```

How to use, whilst on discord run these commands:
```
 ‘start’ will start the queue. It takes between 15–30 seconds for the bot to update with the queue position.
 ‘update’ will send an update to the current channel with your position and ETA.
 ‘stop’ will stop the queue.
```

This is a very useful piece of software, I’d consider donating to the creator as he said it helps him speed up the development. The creator also linked their discord in case you need help: surprisejedi#8384

Here is the link to the website to download: [https://github.com/surprisejedi/2lazy2wait](https://github.com/surprisejedi/2lazy2wait)
