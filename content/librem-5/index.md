+++
title = "Purism Librem 5"
description = "Review of the Purism Librem 5, going over its features and limitations."
date = 2026-07-25
draft = false

[taxonomies]
tags = ["Phones", "Purism", "Mainline", "Mobile Linux"]
[extra]
keywords = "Phones, Markdown, Purism, Mainline, Mobile Linux"
toc = true
series = "Phones"
+++

- Performance: /5
- Affordability: 
- Compatibility: /5
- Battery Life: /5

# Setup information

- OS: Pureos 11 Crimson
- Kernel: 6.12.0 (Downstream)
- DE: Phosh 0.34.0
- Mesa: 22.3.6 [(Downstream)](https://source.puri.sm/pureos/packages/mesa)

# Introduction

The Purism librem 5 is an interesting phone with a troubled past that it's trying to move ahead from.  

# Hardware Supported

| Hardware              | Supported                                      |
| --------------------- | ---------------------------------------------- |
| GPS                   | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| aGPS ¹ ²              | {{ img(src="/icons/exclamation.svg" alt="Maybe")}} |
| Cameras               | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Microphone            | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Bluetooth             | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Modem                 | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Accel/Tilt            | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Orientation/Gyroscope | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Light/Pressure        | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Proximity             | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |

¹ Not hardware but important usability feature and is optional

² Support exists but not included by default

Some hardware is a grouping as those are all functions handled by a single sensor on the device and exposed as different metrics.

# Cell Service

Cell service was tested in the US utilizing US Mobile MVNO, [referral link](https://www.usmobile.com/referrals?referrer=0178DFD2&name=Luis&utm_campaign=monster_referral), as it allows for easy testing of the 3 major US network providers. The only downside is the TMobile service has deprioritized download speeds so your speeds can be on the slower side like mine based on location and network traffic. Download/Upload speed tests were done using ookla [speedtest.net](https://speedtest.net) and netflix [fast.com](https://fast.com) with the data waster option enabled. As service seems to vary from moment to moment, I ran multiple tests and grabbed the best results for each section.

Light Speed (Tmobile) seems to work great without any issues. The Librem 5 only supports 4g officially though there is a community member that was able to [install a 5g module](https://forums.puri.sm/t/librem5-5g-is-here-modem-sim8202g-tested-successfully/28359) though that is not officially supported. Dark Star (AT&T) along with Warp (Verizon) do not work as the upstream carrier have blocks in place for phones that have not gone through their certification process.



## US Mobile Light Speed (Tmobile)

|  Phone    | Tech | Speedtest down | Fast down | Fast up  |                  VoLTE / VoNR                  |
| :-------: | :--: | :------------: | :-------: | :------: | :--------------------------------------------: |
| L5        |  4G  |       |    |  |  |
| Pixel 6   |  5G  |   53.8 Mbps    |  45 Mbps  | 30 Mbps  |   {{ img(src="/icons/cross.svg" alt="No")}}    |
| Pixel 6   |  4G  |   81.9 Mbps    |  65 Mbps  | 12 Mbps  | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |

# Performance

Performance on the L5 is kinda tricky currently. 

The CPU itself is not terrible i would still consider it on the lower end of the spectrum in terms of usable in today's day and age with how heavy things are getting. The 3GB of RAM is also on the limiting side of things though both the CPU+RAM should be enough if you are running lighter apps and avoid heavy websites or have lots of tabs open.

The GPU though is where things get tricky, the driver stack, etnaviv, itself is still being working trying to bring GLES3. The problem with Crimson though is its a stable distro that is locked in time so it is stuck with the mesa version from 2023 plus whatever was backported. This should improve come the next OS version, dawn, which will bring mesa itself forward many years as it is built on debian 13 trixie. The good thing is the current mesa version does have some of etnaviv GLES3 improvements so it can be test/enabled via `MESA_GLES_VERSION_OVERRIDE=3.1` environment variable though results will vary in terms of graphical issues and/or crashes due to it not being to spec yet. Upstream GLES3 progress can be tracked at [mesamatrix](https://mesamatrix.net/) under the OpenGL ES etnaviv sections.

Performance in non3d application is really smooth and responsive. Weirdly enough the L5 is the most responsive device I have testing in terms of responding to inputs where as every other device seems to have a miniscule delay to it. Once the GLES3 driver is in a good enough state to be used by default this will make a really good device to be used as long as you are not doing anything compute heavy and assuming that GLES3 enablement doesen't bring in the tiny delay that I feel on other devices.

# Compatibility

Purism and in particular [Sebastian Kryzszkowiak](https://social.librem.one/@dos) has done a great job in getting the L5 into a great spot both downstream and even upstream in the linux kernel. With the upstream etnaviv work being done and with a heavy push recently it should hopefully mean better GLES 3 support so it will not run into the same compatability issues that the original Pinephone runs into where certain apps are not supported and/or runs slowly. Vulkan support is in a similar situation as GLES3 where technically the GPU itself supports it but driver are missing/lacking so there is no current way to use vulkan. The CPU is also similar to the one going to be used by the upcoming Mecha Comet so hopefully that also means improved upstream mainline support down the line as mecha commet seeems to be prioritizing mainline. 

Other OS seem to have very little support with [PostmarketOS](https://wiki.postmarketos.org/wiki/Purism_Librem5_(purism-librem5)) seeming to be the only 3rd party OS port that I know of that is actually still being actively maintained. The big benefit of PostmarketOS is that it brings with it a much more recent mesa so it lets you play more with the etnaviv improvements to see a glimps of what the L5 hardware is capable of and should hopefully be like in future PureOS releases such as dawn and onwards.

# Android

Android support is handled by a minimal [downstream waydroid](https://source.puri.sm/Librem5/debs/waydroid) built on top waydroid 1.6.1 which is from Dec 2025 so not to far behind upstream. Setting it up is as simple as installing Waydroid from the PureOS Store, launching it and tapping the Download button with the default options. With the limited EMMC on the standard L5 though its very easy to blow through it all with the android system setup and running. 

Waydroid itself does not integrate with the system in any way so theres no settings for it in the gnome settings app but [waydroid-helper](https://github.com/ayasa520/waydroid-helper) seems to work when installed following their debian 12 instructions. Notifications also seem to work so it makes it nice if you are running android only messaging apps in the background.

Waydroid performance is good enough to run simple/important apps just dont expect to be doing much gaming on it or breaking any world records in benchmarking apps. 2D only apps such as going through fdroid and aurora store worked without any performance issues which boads well for casual daily use for your important android only apps. Microg is not installed by default and will need to be installed via waydroid helper or else you will run into a lot of issues running apps from aurora store.

Leaving it running will eat up limited resources so its best to keep it off, luckily startup time is under a minute so you can start it up just when needed and then shut it down.

## Sensors passed to Android

[Sensors Toolbox](https://play.google.com/store/apps/details?id=com.exatools.sensors&hl=en_US) app fails to run with microg-unoffical-installer 1.3.2-beta and 1.3.2.48-alpha

| Sensor              | Passed through                                 |
| ------------------- | ---------------------------------------------- |
| GPS                 |  |
| Cameras             |  |
| Microphone          |  |
| Bluetooth           |  |
| Modem               |  |
| Accelerometer       |  |
| Geomagnetic         |  |
| Orientation         |  |
| Gyroscope           |  |
| Light               |  |
| Pressure            |  |
| Proximity           |  |
| Gravity             |  |
| Linear Acceleration |  |
| Rotation Vector     |  |
| Step Counter        |  |

# Docking

The L5 is pretty docker friendly as they support DP-ALT mode and they [themselves push](https://puri.sm/products/lapdock-kit/) a kit with Next Computer Nexdock lapdock system.


# Web Browsing


| Browsers          | Version  | Toolkit      | Install   |
| ----------------- | -------- | ------------ | --------- |
| Firefox           | 140.13.0 | Gecko        | Repo      |
| Angelfish         | 26.04.3  | Chromium     | Flatpak   |
| Epiphany          | 40.3     | WebKit       | Flatpak   |
| Waydroid Firefox  | 153.0    | Gecko        | Waydroid  |

## Speedometer 3.1

| Browser           | Score                |
| ----------------- | -------------------- |
| Firefox           | 0.908 &plusmn; 0.042 |
| Angelfish         | 1.27 &plusmn; 0.040  |
| Epiphany          | 0.979 &plusmn; 0.066 |
| Waydroid Firefox  | 1.37 &plusmn; 0.048  |


## WebGL Aquarium

| Fish amount | Firefox | Epiphany | Waydroid Firefox |
| ----------- | ------- | -------- | ----------------- |
| 100         |  |        |            |
| 500         |  |        |            |
| 1,000       |  |        |            |
| 5,000       |  |        |            |
| 10,000      |  |        |            |
| 15,000      |  |        |            |
| 20,000      |  |        |            |
| 25,000      |  |        |            |
| 30,000      |  |        |            |

¹ Estimated range as the fps seemed to fluctuate a lot while running making it hard to see actual numbers

# Media Playback

Below is a table of different video codecs and their playback performance. The hardware has support for decoding h264/h265/vp9 and they are working on adding in the software support necessary. The best results for native seem to come from MPV/Celluloid/firefox so as long as you are using any of those performance should be fine and inline with each other.

### Player Information

| Player            | Version | Method    |
| ----------------- | ------- | --------- |
| MPV               |   | Repo      |
| Clapper           |   | Flatpak   |
| Livi              |   | Flatpak   |
| Celluloid         |   | Repo      |
| Firefox           |   | Repo      |
| Waydroid Firefox  |   | Waydroid  |

### H.264/AVC

| Player            | 1080p@30                                       | 720p@30                                        |
| ----------------- | ---------------------------------------------- | ---------------------------------------------- |
| MPV               | |  |
| Clapper           | |  |
| Livi              | |  |
| Celluloid         | |  |
| Firefox           | |  |
| Waydroid Firefox  | |  |

---

### H.265/HEVC

| Player            | 1080p@30                                       | 720p@30                                        |
| ----------------- | ---------------------------------------------- | ---------------------------------------------- |
| MPV               |  |  |
| Clapper           |  |  |
| Livi              |  |  |
| Celluloid         |  |  |
| Firefox           |  |  |
| Waydroid Firefox  |  |  |

---

### AV1

| Player            | 1080p@30                                       | 720p@30                                        |
| ----------------- | ---------------------------------------------- | ---------------------------------------------- |
| MPV               |  |  |
| Clapper           |  |  |
| Livi              |  |  |
| Celluloid         |  |  |
| Firefox           |  |  |
| Waydroid Firefox  |  |  |

---

### VP9

| Player            | 1080p@30                                       | 720p@30                                        |
| ----------------- | ---------------------------------------------- | ---------------------------------------------- |
| MPV               |  |  |
| Clapper           |  |  |
| Livi              |  |  |
| Celluloid         |  |  |
| Firefox           |  |  |
| Waydroid Firefox  |  |  |


# Camera


| Library        |                                      Supported |
| -------------- | ---------------------------------------------: |
| Libcamera      | |
| Droidmedia     | |
| CameraProvider | |

| Abstraction Layer |                                      Supported |
| ----------------- | ---------------------------------------------: |
| LibMegapixels     |  |
| v4l2              |  |
| Gstreamer         |  |
| Qcamera           |  |
| Pipewire          |  |

## Example

| Temp   | Kelvin | Led               |
| ------ | ------ | ----------------- |
| Normal | 5000k  | B35AM             |
| Low    | 2500k  | 519A 3500K dedome |

| Light  | Description                                 |
| ------ | ------------------------------------------- |
| Medium | Convoy S21B 3rd click, Emisar DW4 High Ramp |
| Low    | Convoy S21B 1st click, Emisar DW4 Moonlight |

Flashlights were pointed at the ceiling and everything left on auto, Pixel 9 and Iphone 12 both have a night mode where it took 3s for the low light photos.

## Normal Temp Medium Light

|                                                                L5                                                                 |                                                         Pixel 9                                                          |                                                          iPhone 12                                                           |
| :---------------------------------------------------------------------------------------------------------------------------------: | :----------------------------------------------------------------------------------------------------------------------: | :--------------------------------------------------------------------------------------------------------------------------: |
|  | {{ resize_image(path="/camera/Pixel_9_Normal_Temp_Medium_Lux.jpg", width=300, alt="pixel 9 B35AM 5000k Medium Light") }} | {{ resize_image(path="/camera/Iphone_12_Normal_Temp_Medium_Lux.jpg", width=360, alt="iPhone 12 B35AM 5000k Medium Light") }} |

## Normal Temp Low Light

|                                                             L5                                                             |                                                      Pixel 9                                                       |                                                       iPhone 12                                                        |
| :---------------------------------------------------------------------------------------------------------------------------: | :----------------------------------------------------------------------------------------------------------------: | :--------------------------------------------------------------------------------------------------------------------: |
|  | {{ resize_image(path="/camera/Pixel_9_Normal_Temp_Low_Lux.jpg", width=300, alt="pixel 9 B35AM 5000k Low Light") }} | {{ resize_image(path="/camera/Iphone_12_Normal_Temp_Low_Lux.jpg", width=360, alt="iPhone 12 B35AM 5000k Low Light") }} |

## Low Temp Medium Light

|                                                               L5                                                                |                                                         Pixel 9                                                         |                                                          iPhone 12                                                          |
| :--------------------------------------------------------------------------------------------------------------------------------: | :---------------------------------------------------------------------------------------------------------------------: | :-------------------------------------------------------------------------------------------------------------------------: |
| | {{ resize_image(path="/camera/Pixel_9_Low_Temp_Medium_Lux.jpg", width=300, alt="pixel 9 519a 3500K DD Medium Light") }} | {{ resize_image(path="/camera/Iphone_12_Low_Temp_Medium_Lux.jpg", width=360, alt="iPhone 12 519a 3500K DD Medium Light") }} |

## Low Temp Low Light

|                                                            L5                                                             |                                                      Pixel 9                                                      |                                                       iPhone 12                                                       |
| :--------------------------------------------------------------------------------------------------------------------------: | :---------------------------------------------------------------------------------------------------------------: | :-------------------------------------------------------------------------------------------------------------------: |
|  | {{ resize_image(path="/camera/Pixel_9_Low_Temp_Low_Lux.jpg", width=300, alt="pixel 9 519a 3500K DD Low Light") }} | {{ resize_image(path="/camera/Iphone_12_Low_Temp_Low_Lux.jpg", width=360, alt="iPhone 12 519a 3500K DD Low Light") }} |

# Battery Life


Testing was done using the following settings:

- Screen brightness set to 50%
- Screen timeout disabled
- Measured from 100% battery to device shutdown
- Without android unless specified
- With sim unless specified
- With Wifi enabled
- Video playback is 720p 30 fps no audio
- Charge time tested on pinepower v1 desktop
- Prometheus polling
  - Standard: every 15 seconds
  - Standby: every 30 minutes

## Screen Time

| Method                 | Battery Life | Drain Per Hour |
| ---------------------- | -----------: | -------------: |
| Screen on              |   |          |
| Screen on + Android    |   |          |
| Screen on + Stress CPU |   |          |
| Screen on without sim  |   |          |

---

## Video Playback

| Method            | Battery Life | Drain Per Hour |
| ----------------- | -----------: | -------------: |
| MPV               |   |         |
| Firefox           |   |         |
| Waydroid Firefox  |   |         |

---

## Standby

| Method              | Battery Life | Drain Per Hour |
| ------------------- | -----------: | -------------: |
| Standby             |     |          |
| Standby + Android   |     |          |
| Standby without sim |     |          |

---

## Charging

| Method       | Charging Time |
| ------------ | ------------: |
| Charge 0-80% |        |

### Charging Curve

- Measured from Sonoff S31 running esphome


# Support



# Conclusion



# My Involvement / Disclosures
