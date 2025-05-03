---
title: "Hugo Website With Blowfish Pt. 1"
date: 2025-04-30
tags: ["Hugo", "Blowfish"]
---
## Required Tools
- [Hugo](https://gohugo.io/) <br>
- [Blowfish Theme](https://blowfish.page/)<br>

## Background
It was really a spur of the moment decision to port my CTF writeups from my dedicated GitHub repository over to a Hugo site. Prior to making this, I had absolutely no website building experience apart from a little bit of JavaScript I played around with in high school. But then my friend introduced me to Hugo: an open-source static website generator which uses [Markdown](https://www.markdownguide.org/) to generate each page, which is a language I had become familiar with in making my CTF writeups, so I figured I would give it a shot. This post will detail my experience in creating my Hugo site locally with the Blowfish theme on Windows 10, but not how I made it internet-facing or any of the customization details, which I will make another post about at a later date. 

## Installing Hugo (v0.120.4)
A quick disclaimer, I had to use an older version of Hugo to get this website to work since I couldn't get it to instantiate the Blowfish theme on the most recent version (v0.147.1). Using PowerShell and the [Chocolatey](https://chocolatey.org/) package manager, I ran this command to install the older version of Hugo:
```
choco install hugo-extended --version=0.120.4 -y
```
If you're using this as a tutorial, you should run ``hugo version`` to verify the installation, it should say ``hugo v0.120.4-f11bca5fec2ebb3a02727fb2a5cfb08da96fd9df+extended`` if it was successful. Next, in the directory you want the website to be housed in, run this command to create the shell of a Hugo website.
```
hugo new site [your site name]
```
## Installing Blowfish Theme
For this part I highly recommend that you have [Git](https://git-scm.com/downloads) installed to install Blowfish as a Git submodule. If you already have Git, you can run this set of commands to download Blowfish.
```
cd [your website directory]
git init
git submodule add -b main https://github.com/nunocoracao/blowfish.git themes/blowfish
```
This will take a few minutes to install. Once it finishes, go to the ``\themes\blowfish\config\_default`` directory and copy the contents into the ``config`` directory of the root folder (Note: you will have to create the ``_default`` directory in your root config folder and drop the six .toml files in there). You should delete the ``hugo.toml`` that was auto-generated in the root directory as well. Those .toml files all have different purposes in configurating the website, but to get to the default Blowfish site, you simply have to uncomment the 5th line in the hugo.toml file. 
![uncomment this line](https://i.imgur.com/07F9m77.png)

## Opening The Site
At this point, all you have to do is run ``hugo server`` in your powershell instance and your website should go up on your localhost:1313!
![default](https://i.imgur.com/yR1xvWR.png)

## Next Steps
There's a lot more to do before our website is in a complete state, but now we have a default Blowfish site on Hugo. From here, you can start making use of [Blowfish's extensive configuration capabilities](https://blowfish.page/docs/configuration/) to personalize your site, and start creating content using markdown files. In part 2, I will detail my configuration choices, and how to start making content. 
