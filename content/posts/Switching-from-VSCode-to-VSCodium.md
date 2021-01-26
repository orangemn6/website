---
title: "Switching From VSCode to VSCodium"
author: Jacob Goldstein
date: 2021-01-24T11:38:56-05:00
draft: true
type: post
categories:
 - vscode
tags:
 - vscode
---

24 Oct 2019

![Screenshot of this post as I write it in VSCodium.](https://ar.al/2019/10/24/how-to-migrate-from-vscode-to-vscodium-the-best-code-editor-ever-minus-the-corporate-bullshit/writing-this-post-in-vscodium.jpeg)

Blogception: a post on VSCodium as it’s being written in VSCodium.

I am writing this blog post in [VSCodium](https://github.com/VSCodium/). What? Is that like VSCode?

Yes, it’s basically VSCode minus the corporate bullshit like surveillance and proprietary-licensed binaries.

An ode to VSCode
----------------

VSCode is the best code editor I’ve ever used.

It’s actually rather delightful.

There, I’ve said it – and I’ve used a lot of editors across 10+ years of programming.

VS-what?
--------

![Screenshot of the VSCode logo](https://ar.al/2019/10/24/how-to-migrate-from-vscode-to-vscodium-the-best-code-editor-ever-minus-the-corporate-bullshit/vscode-logo.jpeg)

VSCode: it’s not just for code (ok, it is).

For those of you who are not programmers (yet!) or have been living under a rock, VSCode is an open source code editor from Microsoft.

I know, I was shocked too.

Enter, the bullshit
-------------------

Even though it’s awesome, Microsoft is still Microsoft so – of course – it comes with telemetry (read: surveillance) by default. So while I love using it, I had to qualify every recommendation to others with “and remember to turn telemetry off.”

Well, no longer!

Beyond the bullshit
-------------------

When I started using vscode, I heard about an open-source version called VS Codium.

It sounded great so I decided to check it out and I’m very glad I did (thanks, cukmekerb).

Enter VSCodium
--------------

![Screenshot of the VSCodium page on GitHub showing the VSCodium logo – looks like a blue coral or mycelium of some sort – and reads “VSCodium: Free/Libre Open Source Software Binaries of VSCode”](https://ar.al/2019/10/24/how-to-migrate-from-vscode-to-vscodium-the-best-code-editor-ever-minus-the-corporate-bullshit/vscodium.jpeg)

The VSCodium project page on Microsoft GitHub.

So it turns out that some enterprising freedom-lovers created a project called VSCodium that takes the MIT-licensed source code, removes the telemetry (read: surveillance) from the codebase (along with the branding and licenses the resulting binaries under the MIT license, just like the code itself.

How yummy!

Bonus: auto updates!
--------------------

Also, given that my main development machine is a laptop running Linux, I had to keep installing VSCode updates by hand as Microsoft does not make automatic updates available for my platform. VSCodium fixes that for me as [they have an apt repository](https://gitlab.com/paulcarroty/vscodium-deb-rpm-repo#how-to-install-for-debianubuntulinux-mint).

Shut up and don’t take my money!
--------------------------------

So how does one install VSCodium? Also, given there’s a high chance you’re already running VSCode (because, like, who isn’t, amirite?), how do you migrate your extensions and other settings to it?

Easy peasy!

If you’re on a Debian-derived operating system, you can just copy/paste the following commands and be up and running in the next few seconds.

For other platforms, it’s just as easy if not easier ([read the download/install instructions](https://github.com/VSCodium/vscodium#downloadinstall) and the [migrating from Visual Studio Code to VSCodium](https://github.com/VSCodium/vscodium/blob/master/DOCS.md#migrating-from-visual-studio-code-to-vscodium) section of the documentation for details).

1.  Install VSCodium with auto updates
    ----------------------------------
    
    On Debian-derived operating systems that have the `apt` package manager:
    
        # Authorise Paul Carroty’s repository.
        # (https://twitter.com/paulcarroty)
        wget -qO - https://gitlab.com/paulcarroty/vscodium-deb-rpm-repo/raw/master/pub.gpg | sudo apt-key add -
        
        # Add Paul’s custom apt repository to your apt sources list.
        echo 'deb https://gitlab.com/paulcarroty/vscodium-deb-rpm-repo/raw/repos/debs/ vscodium main' | sudo tee --append /etc/apt/sources.list
        
        # Update your apt package list and install VSCodium.
        sudo apt update
        sudo apt install codium
    
2.  Copy your extensions and settings over from VSCode to VSCodium.
    ---------------------------------------------------------------
    
    On Linux:
    
        # Create the folder to host your extensions.
        mkdir -p ~/.vscode-oss/
        
        # Copy your extensions over from VSCode.
        cp -R ~/.vscode/extensions ~/.vscode-oss/
        
        # Create the folder to hold your settings.
        mkdir -p $HOME/.config/VSCodium/
        
        # Copy your settings over from VSCode.
        cp -R $HOME/.config/Code/User $HOME/.config/VSCodium/User/
    

After you’ve followed the above instructions – or those for your own platform – you should be able to launch VSCodium by just typing `codium` in Terminal

