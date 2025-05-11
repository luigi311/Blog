+++
title = "Widevine on Mobile/ARM Linux"
description = "Guide to install widevine for basic drm support on mobile/arm linux"
date = 2025-05-04
draft = false

[taxonomies]
tags = ["Mobile Linux", "DRM", "Guide", "ARM"]
[extra]
toc = true
series = "Mobile Linux"
+++

# What is widevine

Widevine is a DRM system used to protect copyrighted media content. It contains 3 different levels that determines what level of content you have access too usually seperated based on quality. The 3 levels consist of L1 > L2 > L3 with L3 being the lowest level and is done in software so it is something that can be do on all devices as long as its an architecture that google has released binaries for. L1 and L2 can only be implemented by the hardware manufacture for your individual device as it requires a hardware secure element and certification. 


# Why so complicated

Why do I need to use widevine on my mobile/arm linux device while my desktop linux just works?

Your AMD/Intel based linux machine is still using widevine L3, the major difference is firefox/chrome both automatically install and configure it for you on AMD64 machines. 

When you are using firefox and try to access any media with DRM for the first time, firefox will prompt you if you want to enable support for it. If you allow it then firefox will go out and fetch widevine L3 and get it configured automatically for you so its a seamless experience. This feature though is only implemented for AMD64 based builds of firefox so it is not avaliable on the ARM builds. There have been feature requests for firefox to enable this functionality for their arm builds but until then the process has to be done manually.


# Limitations

Limitations on access and quality based on online posts.

| Widevine Level | Spotify                                        | Netflix                                     | Disney+                                     |
|----------------|------------------------------------------------|---------------------------------------------|---------------------------------------------|
| L1             | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | 4k                                          | 4k                                          |
| L3             | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | 480p¹                                       | 720p                                        |
| None           | {{ img(src="/icons/cross.svg" alt="None")}}    | {{ img(src="/icons/cross.svg" alt="None")}} | {{ img(src="/icons/cross.svg" alt="None")}} |

¹ Requires a specific User Agent to work

# Before/After

Here are some screenshots to show a before and after widevine L3 has been configured

| Website                                     | Before                                                                                        | After                                                                                       |
|---------------------------------------------|-----------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------|
| [Bitmovin](https://bitmovin.com/demos/drm/) | {{ resize_image(path="/widevine/Before_Bitmovin.png", width=256, alt="Bitmovin no access") }} | {{ resize_image(path="/widevine/After_Bitmovin.png", width=256, alt="Bitmovin widevine") }} |
| Spotify                                     | {{ resize_image(path="/widevine/Before_Spotify.png", width=256, alt="Spotify no access") }}   | {{ resize_image(path="/widevine/After_Spotify.png", width=256, alt="Spotify working") }}    |


# Prerequisites

- curl
- git
- python3
- unsquashfs


## Debian/Ubuntu

```bash
sudo apt install curl git python3 squashfs-tools
```


# Install

Tested on a Furilabs FLX1

Clone into the git repo by AsahiLinux
```bash
git clone https://github.com/AsahiLinux/widevine-installer.git
cd widevine-installer
```

Find your lib directory
```bash
export LIBDIR=$(dirname $(find /usr/lib* -name "firefox" -type d))
echo "$LIBDIR"
```

This should hopefully return a single directory, in my case `/usr/lib`  
If multiple directories are returned then you will need to figure out which one actually contains your firefox config that is being used and use that as your LIBDIR

Run the widevine-installer script as root with your libdir and follow the instructions in the terminal, mostly enter to accept license agreements
```bash
sudo LIBDIR="$LIBDIR" ./widevine-installer
```
or
```bash
sudo LIBDIR="/usr/lib" ./widevine-installer
```

Once completed, give your system a reboot and you should be good to go! Try opening the bitmovin drm testing site and see if it reports widevine is supported.


# Special thanks

- AsahiLinux for developing and maintaining the installer
- Widevine folks for creating a software L3
- Google for releasing widevine L3 binaries for both AMD64 and ARM64, hopefully more architectures too at some point
