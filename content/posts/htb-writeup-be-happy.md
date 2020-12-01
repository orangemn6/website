---
title: "Htb Writeup Be Happy"
author: Jacob Goldstein
date: 2020-11-30T15:10:07-05:00
draft: true
categories:
 - HTB
 - hacking
tags:
 - HTB
 - hacking
---

So when you first unzip the file, you will get an image file. it is an unprotected steganographed image. put it through steghide or stegosuite, and you will get instructions to make a GET request to https://www.jacobgoldstein.tk/happy/htb/index.html. once you do that you will get some base64 code. decode that and there is your flag!!
