+++
title = "Pinephone Pro"
description = "Information about the Pinephone Pro, its features and limitations."
date = 2026-01-08
draft = false

[taxonomies]
tags = ["Phones", "Pine", "Mainline", "Mobile Linux"]
[extra]
keywords = "Phones, Markdown, Pine, Mainline, Mobile Linux"
toc = true
series = "Phones"
+++

- Performance: 3/5
- Affordability: A bit expensive for the performance but decent for linux first devices
- Compatibility: 4/5
- Battery Life: 2/5


# Setup information
- OS: Danct Archlinux 2025/07/28 (Updated 2025/12/01)
- Kernel: 6.15.6 Megi Danct
- DE: Phosh
- Mesa: 25.2.7
- Uboot: Megi 2024.04 uboot w/ rkbin
- Modem Firmware: the-modem-distro


# Hardware Supported

| Hardware              | Supported                                          |
|-----------------------|----------------------------------------------------|
| GPS                   | {{ img(src="/icons/checkmark.svg" alt="Yes")}}     |
| aGPS ¹                | {{ img(src="/icons/exclamation.svg" alt="Maybe")}} |
| Cameras               | {{ img(src="/icons/checkmark.svg" alt="Yes")}}     |
| Microphone            | {{ img(src="/icons/checkmark.svg" alt="Yes")}}     |
| Bluetooth             | {{ img(src="/icons/checkmark.svg" alt="Yes")}}     |
| Modem                 | {{ img(src="/icons/checkmark.svg" alt="Yes")}}     |
| Accel/Tilt            | {{ img(src="/icons/checkmark.svg" alt="Yes")}}     |
| Orientation/Gyroscope | {{ img(src="/icons/checkmark.svg" alt="Yes")}}     |
| Light/Proximity       | {{ img(src="/icons/checkmark.svg" alt="Yes")}}     |

¹ Not hardware but important usability feature, not built in and requires a 3rd party [python script](https://gist.github.com/alastair-dm/263209b54d01209be28828e555fa6628) to use it


# Cell Service

Cell service was tested in the US utilizing US Mobile MVNO on the T-Mobile Network, [referral link](https://www.usmobile.com/referrals?referrer=0178DFD2&name=Luis&utm_campaign=monster_referral). Download/Upload speed tests were done using ookla [speedtest.net](https://speedtest.net) and netflix [fast.com](https://fast.com) with the data waster option enabled. As service seems to vary from moment to moment, I ran multiple tests and grabbed the best results for each section. This was tested with the 3rd party modem firmware, [the modem distro](https://github.com/the-modem-distro/pinephone_modem_sdk), which is the recommended modem firmware for the EG25 as it fixes a lot of issues with the stock firmware and also reduces power usage/heat on it.

**Note: US Mobile seems to think the EG25-G/PPP is a mobile hotspot device and will kick the line offline if you are on an unlimited plan and requires you to be on a by the gig/pooled line instead. Learned this the hard way by physically moving my personal sim from my FLX1 to the pinephone pro and the line went dead and required customer support and inserting it into my pixel 6 to fix it.**

The eSIM adapter works on the PPP but it doesnt have a built in way to change profiles easily. It does not work with [eSIM Manager](https://codeberg.org/lucaweiss/lpa-gtk), hopefully it will in the future as I see there are discussions and even commits related to enabling AT backend support.

## US Mobile Light Speed (Tmobile)

| Phone   | Tech | Speedtest down | Fast down | Fast up  | VoLTE / VoNR                                   |
| :------ | :--- | -------------: | --------: | -------: | :--------------------------------------------: |
| PPP     | 4G   | 5.44 Mbps      | 4.1 Mbps  | 8.5 Mbps | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Pixel 6 | 5G   | 30.78 Mbps     | 29 Mbps   | 17 Mbps  | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Pixel 6 | 4G   | 24.77 Mbps     | 15 Mbps   | 7.1 Mbps | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |

# Performance

The PPP is not a fast device, while leagues faster than the original pinephone it does not hold a candle to other devices in its price point. The RK3399s with its 4GB of memory can be pretty limiting but is decent enough for non demanding end users that have some patience. Where it falls flat though is when it comes to doing development work that requires compliation or even with any application or framework that is compute heavy that isn't accelerated somewhere in hardware. The RK3399s even though is binned is still not really designed for such a small form factor so it gets very hot and as a result will start to throttle in any sustained workload, the modem itself also generates significant heat when in use which only exasterbates the problem when trying to use the device out in the real world. Luckily GTK4 and QT6 "should" all be accelerated automatically so most applications run just fine without any hassle. Browsing the web is not fast but is decent enough to not be painful to use and can even handle video playback in software.

# Compatibility

The PPP is almost compatible with everything, its a mainline device running a downstream kernel that has been built into pretty much every mobile linux OS and works with every mobile linux DE. The SOC is way newer than the one in the pinephone so it has support for opengl ES 3.1 so it doesnt run into the same issues that the pinephone is running into now adays with GTK dropping GLES 2.0 support. It is sadly lacking support for vulkan so applications that are vulkan only or even applications that implement GLES as an after thought might run into issues. One example of this is the rust WGPU library which is the main library used most rust applications for getting hardware acceleration. WGPU gles implementation seems to be spotty on mobile linux so it doesn't actually work on the PPP so all rust GUI applications need to be forced to run in software. Some of the other qualcom mainline devices work around this by just running WGPU in vulkan but that isn't an option on the PPP. The good thing though is those are far and few in between and pine has a large community around it so when new mobile linux applications are developed they are usually tested on the PP or the PPP.

Other OS have varying levels of community support such as Sailfish, Ubuntu Touch, postmarketos and mobian. While sailfish and ubuntu touch are prodominetely OS used in halium devices they run on the PPP perfectly fine utilizing the mainline drivers for everything. UT on the PPP though does lack some features that make it hard to daily, OTA/Camera/Spotty Calls, compared to other halium UT devices. All the OS that the PPP runs though are all community supported with no involvment usually from the parent companies, with the exception of mobian with the mobian team officially supporting the PPP.


# Android

Android support is handled by the [upstream waydroid](https://github.com/waydroid/waydroid). Setting it up is pretty easy by installing waydroid from the danctnix repo or from aur. Another helpful tool is [waydroid-helper](https://github.com/ayasa520/waydroid-helper) which is also in the aur for easy install. Waydroid does not integrate with the system in anyway so theres no settings for it in the gnome settings app but waydroid helper does atleast make it easy to manager certain features such as mapping in folders and even stopping and starting the container from a GUI. Sensor passthrough is pretty limited which some work arounds existing such as for GPS with the following script [geobridge](https://gitlab.com/papiris/geobridge). Waydroid performance is actually better than expected though there is a slight delay when tapping. Leaving it running will eat up limited resources so its best to keep it off, luckily startup time is under a minute so you can start it up just when needed and then shut it down.


## Sensors passed to Android

Tested using [Sensors Toolbox](https://play.google.com/store/apps/details?id=com.exatools.sensors&hl=en_US) app

| Sensor              | Passed through |
|---------------------|----------------|
| GPS                 | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Cameras             | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Microphone          | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Bluetooth           | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Modem               | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Accelerometer       | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Geomagnetic         | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Orientation         | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Gyroscope           | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Light               | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Pressure            | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Proximity           | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Gravity             | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Linear Acceleration | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Rotation Vector     | {{ img(src="/icons/cross.svg" alt="No")}}      |


# Docking

The PPP similar to the original PP has excellent docking support. It supports video out natively through DP-Alt mode so you can use any dock that utilizes that standard or even plug directly into something like a NexDock for a laptop like experience. This level of docking support is what all other mobile linux devices should strive for and makes it great for using it as a single device to cover all your needs. It makes it super handy for traveling as it allows you to keep all your files in a single location and research information in a bigger screen and then take it to go with you when you are heading out.

What is missing though is a way to handle wireless docking such as the halium devices running UT that can wirelessly cast to a remote display via miracast. If the PPP does support miracast in hardware then no one has gotten around to getting the software side of it implemented and UT on the PPP does not have this feature implemented. There is limited development around miracast in general though so not sure if this is something someone will ever develop/research for the PPP.

# Web Browsing

Web browsing works decently. Firefox runs well and comes with postmarketos mobile-config-firefox for a better experience on the mobile screen. Benchmarking results with [speedometer 3.1](https://browserbench.org/Speedometer3.1/) with scale set to 100% are below, based on results below kumo works the best for performance but stuggles with videos as shown in the next section. Kumo itself is relatively new so if you run into any [issues please report them](https://github.com/catacombing/kumo) so they can be fixed, the developers are very active and friendly. Waydroid firefox actually has really good performance and scales really well since its an android app, just know since it requires waydroid running so it will consume resources even when not in use.  

| Browser           | Score                | Version | Toolkit  | Install    |
|-------------------|----------------------|---------|----------|------------|
| Firefox           | 1.24 &plusmn; 0.17   | 145.0.2 | Gecko    | Repo       |
| Angelfish         | 1.20 &plusmn; 0.03   | 25.08.0 | Chromium | Flatpak    |
| Epiphany          | 1.23 &plusmn; 0.04   | 49.2    | WebKit   | Flatpak    |
| Kumo              | 1.29 &plusmn; 0.03   | 1.6.1   | Webkit   | Flatpak    |
| Waydroid Firefox  | 1.99 &plusmn; 0.12   | 146.0   | Gecko    | Waydroid   |


# Media Playback

Below is a table of different video codecs and their playback performance. The hardware has support for decoding h264/h265/vp9 and there is work being done on adding in the software support though no timeline on when it will be widely avaliable in everything. Results seem to be pretty mixed though luckily almost everything is able to play h264 which is still pretty much everywhere. It does struggle to play some of the newer codecs that are starting to take over such as AV1 being limited to just 720p. Waydroid firefox struggles with everything so if you need a browser for video playback just stick with native firefox. Kumo seems to be in a weird part where it can play 720p av1 and vp9 but h264 stutters and seems to struggle.

### Player Information

| Player            | Version  | Method    |
|-------------------|----------|-----------|
| MPV               | 0.40.0   | Repo      |
| Clapper           | 0.8.0    | Flatpak   |
| Livi              | 0.3.2    | Flatpak   |
| Celluloid         | 0.29     | Repo      |
| Firefox           | 145.0.2  | Repo      |
| Waydroid Firefox  | 146.0    | Waydroid  |
| Kumo              | 1.6.1    | Flatpak   |

### H.264/AVC

| Player           | 1080p@30    | 720p@30    |
|------------------|-------------|------------|
| MPV              | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Clapper          | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Livi             | {{ img(src="/icons/cross.svg" alt="No")}}      | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Celluloid        | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Firefox          | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Waydroid Firefox | {{ img(src="/icons/cross.svg" alt="No")}}      | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Kumo             | {{ img(src="/icons/cross.svg" alt="No")}}      | {{ img(src="/icons/cross.svg" alt="No")}}      |

---

### H.265/HEVC

| Player           | 1080p@30    | 720p@30    |
|------------------|-------------|------------|
| MPV              | {{ img(src="/icons/cross.svg" alt="No")}}      | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Clapper          | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Livi             | {{ img(src="/icons/cross.svg" alt="No")}}      | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Celluloid        | {{ img(src="/icons/cross.svg" alt="No")}}      | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Firefox          | {{ img(src="/icons/cross.svg" alt="No")}}      | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Waydroid Firefox | {{ img(src="/icons/cross.svg" alt="No")}}      | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Kumo             | {{ img(src="/icons/cross.svg" alt="No")}}      | {{ img(src="/icons/cross.svg" alt="No")}}      |

---

### AV1

| Player           | 1080p@30    | 720p@30    |
|------------------|-------------|------------|
| MPV              | {{ img(src="/icons/cross.svg" alt="No")}} | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Clapper          | {{ img(src="/icons/cross.svg" alt="No")}} | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Livi             | {{ img(src="/icons/cross.svg" alt="No")}} | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Celluloid        | {{ img(src="/icons/cross.svg" alt="No")}} | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Firefox          | {{ img(src="/icons/cross.svg" alt="No")}} | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Waydroid Firefox | {{ img(src="/icons/cross.svg" alt="No")}} | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Kumo             | {{ img(src="/icons/cross.svg" alt="No")}} | {{ img(src="/icons/cross.svg" alt="No")}}      |

---

### VP9

| Player           | 1080p@30    | 720p@30    |
|------------------|-------------|------------|
| MPV              | {{ img(src="/icons/cross.svg" alt="No")}} | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Clapper          | {{ img(src="/icons/cross.svg" alt="No")}} | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Livi             | {{ img(src="/icons/cross.svg" alt="No")}} | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Celluloid        | {{ img(src="/icons/cross.svg" alt="No")}} | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Firefox          | {{ img(src="/icons/cross.svg" alt="No")}} | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Waydroid Firefox | {{ img(src="/icons/cross.svg" alt="No")}} | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Kumo             | {{ img(src="/icons/cross.svg" alt="No")}} | {{ img(src="/icons/cross.svg" alt="No")}}      |


# Camera

Cameras on the PPP are working but not in a great position. The libcamera stack that is used across multiple apps such as gnome snapshot/camera and what the browsers use lack autofocus so its almost impossible to use in the real world as everything will be out of focus and blurry. There was a PoC that someone created for the rkisp for libcamera but looks like its been stuck and has not progressed upstream into libcamera. On the other hand Megapixles has autofocus and manual focus but the processing on it is very slow as it is all done on the CPU instead of the rkisp like libcamera. Megapixels processing by default also has a green tint to all the images though it can be worked around by using an external [postprocessing script like mine](https://github.com/luigi311/megapixels_postprocess) or manually processing the images via darktables and/or gimp or modifying postprocessd to enable auto white balance in the raw processing step. Overall its great that the camera works at all so in a pinch you can make use of it but its not something you would want to use as your main camera for taking pictures. If autofocus support is added to libcamera in the future then the camera situation will be greatly improved as libcamera has way better performance than megapixels and the quality is already really good even without the image tuning. 

There is a [WiP autofocus for the software isp](https://git.nekocwd.link/NekoCWD/libcamera) in libcamera so maybe onces thats merged in we can use that as a base for designing the rkisp version for atleast a generic autofocus implementation and maybe down the line someone can implement the phase detection autofocus that the imx258 supports.

| Library        |  Supported                                           |
|----------------|-----------------------------------------------------:|
| Libcamera      | {{ img(src="/icons/exclamation.svg" alt="Maybe")}} ¹ |

¹ Libcamera supports the sensors but as of this review, it is missing autofocus which is a hard requirement for actual usage


| Abstraction Layer   |  Supported                                           |
|---------------------|-----------------------------------------------------:|
| LibMegapixels       | {{ img(src="/icons/checkmark.svg" alt="Yes")}}       |
| Gstreamer           | {{ img(src="/icons/exclamation.svg" alt="Maybe")}} ¹ |
| Pipewire            | {{ img(src="/icons/exclamation.svg" alt="Maybe")}} ¹ |

¹ Gstreamer and Pipewire are handled through Libcamera so the same issues that affect libcamera also affect these layers

## Example

| Temp   | Kelvin | Led   |
|--------|--------|-------|
| Normal | 5000k  | B35AM |
| Low    | 2500k  | 519A 3500K dedome  |

| Light  | Description |
|--------|-------------|
| Medium | Convoy S21B 3rd click, Emisar DW4 High Ramp |
| Low    | Convoy S21B 1st click, Emisar DW4 Moonlight |

Flashlights were pointed at the ceiling and everything left on auto, pixel 9 and Iphone 12 both have a night mode where it took 3s for the low light photos

## Versions

| Application    | Method  | Version      |
|----------------|---------|--------------|
| Megapixels     | Repo    | 2.0.0        |
| Libcamera      | Repo    | 0.6.0        |
| Gnome Snapshot | Flatpak | 49.0         |

## Normal Temp Medium Light

| Megapixels Postprocessd | Megapixels Personal | Gnome Snapshot |
|------------------------|--------------------|----------------|
| {{ resize_image(path="/pinephone-pro/camera/megapixels/PPP_Postprocessd_Normal_Temp_Medium_Lux.jpg", width=360, alt="Megapixels Postprocessd") }} | {{ resize_image(path="/pinephone-pro/camera/megapixels/PPP_Personal_Normal_Temp_Medium_Lux.png", width=360, alt="Megapixels Personal ") }} | {{ resize_image(path="/pinephone-pro/camera/libcamera/PPP_Libcamera_Normal_Temp_Medium_Lux.jpg", width=320, alt="") }} |

| Pixel 9 | iPhone 12 |
|---------|-----------|
| {{ resize_image(path="/camera/Pixel_9_Normal_Temp_Medium_Lux.jpg", width=300, alt="pixel 9 B35AM 5000k Medium Light") }} | {{ resize_image(path="/camera/Iphone_12_Normal_Temp_Medium_Lux.jpg", width=360, alt="iPhone 12 B35AM 5000k Medium Light") }} |

## Normal Temp Low Light

| Megapixels Postprocessd | Megapixels Personal | Gnome Snapshot |
|------------------------|--------------------|----------------|
| {{ resize_image(path="/pinephone-pro/camera/megapixels/PPP_Postprocessd_Normal_Temp_Low_Lux.jpg", width=360, alt="Megapixels Postprocessd") }} | {{ resize_image(path="/pinephone-pro/camera/megapixels/PPP_Personal_Normal_Temp_Low_Lux.png", width=360, alt="Megapixels Personal ") }} | {{ resize_image(path="/pinephone-pro/camera/libcamera/PPP_Libcamera_Normal_Temp_Low_Lux.jpg", width=320, alt="") }} |

| pixel 9 | iPhone 12 |
|---------|-----------|
| {{ resize_image(path="/camera/Pixel_9_Normal_Temp_Low_Lux.jpg", width=300, alt="pixel 9 B35AM 5000k Low Light") }} | {{ resize_image(path="/camera/Iphone_12_Normal_Temp_Low_Lux.jpg", width=360, alt="iPhone 12 B35AM 5000k Low Light") }} |

## Low Temp Medium Light

| Megapixels Postprocessd | Megapixels Personal | Gnome Snapshot |
|------------------------|--------------------|----------------|
| {{ resize_image(path="/pinephone-pro/camera/megapixels/PPP_Postprocessd_Low_Temp_Medium_Lux.jpg", width=360, alt="Megapixels Postprocessd") }} | {{ resize_image(path="/pinephone-pro/camera/megapixels/PPP_Personal_Low_Temp_Medium_Lux.png", width=360, alt="Megapixels Personal ") }} | {{ resize_image(path="/pinephone-pro/camera/libcamera/PPP_Libcamera_Low_Temp_Medium_Lux.jpg", width=320, alt="") }} |

| pixel 9 | iPhone 12 |
|---------|:---------:|
| {{ resize_image(path="/camera/Pixel_9_Low_Temp_Medium_Lux.jpg", width=300, alt="pixel 9 519a 3500K DD Medium Light") }} | {{ resize_image(path="/camera/Iphone_12_Low_Temp_Medium_Lux.jpg", width=360, alt="iPhone 12 519a 3500K DD Medium Light") }} |

## Low Temp Low Light

| Megapixels Postprocessd | Megapixels Personal | Gnome Snapshot |
|------------------------|--------------------|----------------|
| {{ resize_image(path="/pinephone-pro/camera/megapixels/PPP_Postprocessd_Low_Temp_Low_Lux.jpg", width=360, alt="Megapixels Postprocessd") }} | {{ resize_image(path="/pinephone-pro/camera/megapixels/PPP_Personal_Low_Temp_Low_Lux.png", width=360, alt="Megapixels Personal ") }} | {{ resize_image(path="/pinephone-pro/camera/libcamera/PPP_Libcamera_Low_Temp_Low_Lux.jpg", width=320, alt="") }} |

| pixel 9 | iPhone 12 |
|---------|:---------:|
| {{ resize_image(path="/camera/Pixel_9_Low_Temp_Low_Lux.jpg", width=300, alt="pixel 9 519a 3500K DD Low Light") }} | {{ resize_image(path="/camera/Iphone_12_Low_Temp_Low_Lux.jpg", width=360, alt="iPhone 12 519a 3500K DD Low Light") }} |


# Battery Life

The phone is not great when it comes to active usage battery life. The RK3399s is a power hungry SOC and the PPP has a relatively small battery for the power draw of the SOC and will require charging throughout the day if you are a heavy phone user. Standby battery life is decent enough though and will last throughout the day, so for users that only need a phone for communication this is more that good enough. 

One major problem though is the phone seems to lose the battery percentage that it's at, with it sometimes just staying at 100% until the battery runs dry and the phone turns off. This problem is made even worse when utilizing suspend which seems to cause more problems with the battery percentage drifting off. One workaround for this seems to be removing the battery from the phone itself and holding the power button while the battery is unplugged. While this seems to temporarily fix the issue, this is not an ideal solution as you wont know your battery percentage is stuck so you cant rely on the battery not being almost dead when you need it. Since non suspended battery is not great you could end up in a situation where the phone didnt enter suspend and ate up your battery and you won't know until it suddenly dies on you. During the standby tests below, the phone was reporting that it still had 50-60% battery left when it suddenly shut off and would not turn back on until plugged in for a while to bring the battery back to life.

Testing was done using the following settings:

- Screen brightness set to 50%
- Screen timeout disabled
- Measured from 100% battery to device shutdown
- Without android unless specified
- With sim unless specified
- With Wifi enabled
- Video playback is 720p 30 fps h264
- Charge time tested on pinepower v1 desktop
- Prometheus polling every 15 seconds

## Screen Time

| Method                           | Battery Life | Drain Per Hour |
|----------------------------------|-------------:|---------------:|
| Screen on                        | 4.50 hours   | 22.22%         |
| Screen on + Android              | 4.25 hours   | 23.52%         |
| Screen on + Stress CPU           | 1.41 hours   | 70.59%         |
| Screen on without sim            | 4.50 hours   | 22.22%         |

---

## Video Playback

| Method                           | Battery Life | Drain Per Hour |
|----------------------------------|-------------:|---------------:|
| MPV                              | 0.96 hours   | 103.45%        |
| Firefox                          | 1.15 hours   | 86.96%         |
| Waydroid Firefox                 | 1.30 hours   | 76.92%         |

---

## Standby

- taken with [sleepwalk](https://github.com/L0v3P01s0n/sleepwalk) enabled utilizing the default settings
    - SLEEP_STEP=30
    - SLEEP_MAX_SECS=600
    - WAKE_SECS=30

| Method                           | Battery Life | Drain Per Hour |
|----------------------------------|-------------:|---------------:|
| Standby                          | 22.78 hours  | 4.39%          |
| Standby + Android                | 21.75 hours  | 4.60%          |
| Standby without sim              | 27.11 hours  | 3.69%          |

---

## Charging

| Method                           | Charging Time |
|----------------------------------|--------------:|
| Charge 0-80%                     | 78 mins       |

### Charging Curve

- Prometheus polling every 5 seconds
- Measured from Sonoff S31 running esphome

{{ resize_image(path="/pinephone-pro/Charge_Curve.png", width=1080, alt="PPP Battery charging curve") }}


# Support

Support from Pine64 on the software side is nonexistent, especially now that they have officially discontinued the device and are no longer producing it. Even before the discontinuation the only official support pine provided was if something was broken on arrival but due to the low warranty period it was a rush job to go through that process of validating it and contacting them. I've had to contact them once for a separate pine device, keyboard, and the support itself was great for me. In that instance they sent me a replacement motherboard that I then had to go in and manually swap out and this was outside the warranty period at the time. 

Most of the support for the pine devices actually come from the community side. Due to the low price of entry for most pine devices, the community itself is massive especially compared to all other mobile linux communities. The PINE64 discord community is the primary place where everyone works and talks all pine things so if you are keeping up with the conversations you know everything going on with all the pine ecosystems. Most of the developers that work on pine devices all hangout in there so its great to ask them questions about what they are working on or if you run into issues. One of the great things about the community based development is that tons of people can pick it up and focus on things that are important for them, one of the main driving forces is Megi on the downstream kernel that is used everywhere on pine devices and you can [read his blog](https://xnux.eu/log/), though its imporant to note that his development on the PPP has basically come to a standstill and is just carrying forward his current patches so we can continue to use newer linux kernels. Some members in the community though are not so keen on relying on a downstream kernel forever so there are a handful of memebers in the community that have been working on upstreaming bits and pieces to reduce the hard requirement of the downstream kerenel. Overall the community is great and very helpful so if you run into any issues or need help setting something up you can usually find someone willing to help you out. Though after so many years with the same pine devices it seems like actual development has slowed down a lot compared to a few years ago.


# Conclusion

The Pinephone Pro is in a weird place when it comes to its future outlook and if it will ever reach the point of recommendation for daily usage. The hardware itself is decent enough for actual usage as long as the battery life is enough for you but the real problem comes from the software side with things being in a almost good enough state but not quite there. The camera situation is a big issue with it lacking autofocus in libcamera which is a hard requirement for actually using the camera in the real world, the megapixels side lacking performance and having the green tint issue by default. The battery percentage issue is also a big problem since you can't relying on your phone to not being close to dying when you need it. The dwindling amount of active developers working on the PPP itself also makes it hard to have a positive outlook on the future of the device as it seems like most developers have moved on to other devices/projects. The lack of first party software support from pine64 also means if the remaining developers in the community move on to other things then development will stop entirely. Luckily all the work that was done is still being carried forward so the PPP continues to run newer kernels and OS releases instead of rotting away like downstream only SBC boards but improvements seem to be coming at a dripping pace at this point. So if the PPP functions well enough for you as it currently stands then it can be a decent enough daily driver but I would not get it with the expectation that it will continue to improve as it has in the past.


# My Involvement / Disclosures

I've been involvement in multiple different pine related projects. Ive worked on Megapixels and Libcamera for the user camera software stack on implementing fixes and features for a better experience. My biggest contribution I'm most proud of would be locating the Raspberry PI imx258 (rear camera) driver in the pi downstream kernel and adapting it so it supports the imx258 variant used by the PPP and pushing it all upstream to the offical linux kernel which then made its way to megi's kernel and all pine devices. This brought an improvement to the camera quality in the driver side of things and also allows for less reliance on a downstream kernel for camera support.

The pinephone pro and all pine devices were all purchased with my own money. I have financially contributed to multiple developers in the pine/mobile linux ecosystem such as Megi (Kernel), Martijn (Megapixels), Guido (Phosh), PostmarketOS (OS), Ubuntu Touch (OS) and hope to continue to provide financial support.

My involvement with the pine community has mostly dwindled as I've moved to other devices in the mobile linux ecosystem but I do try to keep up with things that are happening as I still have some pine devices I wish to use more in the future such as my PineTab 2.
