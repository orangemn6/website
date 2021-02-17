---
title: "Cyberspace History"
author: Jacob Goldstein
date: 2001-02-16T16:26:56-05:00
draft: false
type: post
categories:
 - htb
tags:
 - htb
---


# Orange CTF Writeup

So you see the site, and immediately think to bruteforce. WRONG.

Use some common sense! Look on my github, and find the creds in plain text, and login

What. All you see is a page. You think of cookie injection and fancy sql stuff. (All you have to do is logout)

Click the logout, and it brings you to /f-lag. base64, duh

decrypt that, bam
