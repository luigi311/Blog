+++
title = "Purism Librem 5"
description = "Review of the Purism Librem 5, going over its features and limitations."
date = 2026-09-02
draft = false

[taxonomies]
tags = ["Phones", "Purism", "Mainline", "Mobile Linux"]
[extra]
keywords = "Phones, Markdown, Purism, Mainline, Mobile Linux"
toc = true
series = "Phones"
+++

- Performance: 2/5 (Limited by WIP GPU drivers)
- Affordability: Expensive for what it is and provides compared to others
- Compatibility: 4/5
- Battery Life: /5

# Setup information

- OS: Pureos 11 Crimson
- Kernel: 6.12.0 (Downstream)
- DE: Phosh 0.34.0
- Mesa: 22.3.6 [(Downstream)](https://source.puri.sm/pureos/packages/mesa)

# Introduction

The Purism librem 5 is an interesting phone with a troubled past that it's trying to move ahead from. During their intial sale/preorder customers were waiting for years until their devices were shipping and during that time they were getting the run around in terms of shipping and refunds. For me I ordered my Librem 5 refurbished way after on October 11, 2023 and it was shipped out October 12, 2023 as they were refurbished in stock. I think they current have Librem 5s in stock so you shouldn't be running into that same issue the preorder folks ran into. The librem 5 itself is a nice feeling but heavy and thick phone with it being my thickest device even compared to other devices in full cases so its important to keep in mind. It was also one of the first linux first phones similar to the pinephones and even has kill switches like the pinephones but these kill switches are infinitely more useful as they are accessable externally without having to remove the back cover and requiring tweezers to confidenly switch. These are on the side of the phone and are really nice and easy to toggle on and off. Another phone with similar external kill switches is the FuriLabs FLX1s but I would consider the L5 kill switchs to be in another class compared to the FLX1s in terms of feel and finish.

While the Pinephone revolutionized the community side of mobile linux with them releasing a cheap platform that open source developers can utilize to develop the mobile linux environment but they did not provide any software development themselves so if something was missing drivers/support it was up to the community to figure it out. Purism on the other hand revolutionized the manufacturer/vendor side of mobile linux which massively pushed the ecosystem forward as they were able to bring in focus as they were pushing software solutions to problems that their customers were running into that software did not exist for or was lacking. 

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

² Support exists but not included by default but it is possible

Some hardware is a grouping as those are all functions handled by a single sensor on the device and exposed as different metrics.

# Cell Service

Cell service was tested in the US utilizing US Mobile MVNO, [referral link](https://www.usmobile.com/referrals?referrer=0178DFD2&name=Luis&utm_campaign=monster_referral), as it allows for easy testing of the 3 major US network providers. The only downside is the TMobile service has deprioritized download speeds so your speeds can be on the slower side like mine based on location and network traffic. Download/Upload speed tests were done using ookla [speedtest.net](https://speedtest.net) and netflix [fast.com](https://fast.com) with the data waster option enabled. As service seems to vary from moment to moment, I ran multiple tests and grabbed the best results for each section.

Light Speed (Tmobile) seems to work great without any issues. The Librem 5 only supports 4g officially though there is a community member that was able to [install a 5g module](https://forums.puri.sm/t/librem5-5g-is-here-modem-sim8202g-tested-successfully/28359) though that is not officially supported. Dark Star (AT&T) along with Warp (Verizon) do not work as the upstream carrier have blocks in place for phones that have not gone through their certification process.



## US Mobile Light Speed (Tmobile)

|  Phone    | Tech | Speedtest down | Fast down | Fast up  |                  VoLTE / VoNR                  |
| :-------: | :--: | :------------: | :-------: | :------: | :--------------------------------------------: |
| L5        |  4G  |       |    |  |  |
| Pixel 6   |  5G  |      |    |    |   {{ img(src="/icons/cross.svg" alt="No")}}    |
| Pixel 6   |  4G  |      |    |    | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |

# Performance

Performance on the L5 is kinda tricky currently. 

The CPU itself is not terrible, I would still consider it on the lower end of the spectrum in terms of usable in today's day and age with how heavy things are getting especially with more and more AI developed applications/websites instead of the handcrafted artisanal development. The 3GB of RAM is also on the limiting side of things though both the CPU+RAM should be enough if you are running lighter apps and avoid heavy websites or have lots of tabs open.

The GPU though is where things get tricky, the driver stack, etnaviv, itself is still being worked on trying to bring GLES3. The problem with Crimson though is its a stable distro that is locked in time so it is stuck with the mesa version from 2023 plus whatever was backported. This should massively improve come the next OS version, dawn, which will bring mesa itself forward many years as it is built on debian 13 trixie. The good thing is the current mesa version does have some of etnaviv GLES3 improvements so it can be test/enabled via `MESA_GLES_VERSION_OVERRIDE=3.1` environment variable though results will vary in terms of graphical issues and/or crashes due to it not being to spec yet. Upstream GLES3 progress can be tracked at [mesamatrix](https://mesamatrix.net/) under the OpenGL ES etnaviv sections and should give you a feel for what the L5 is capable of in the future.

Performance in non-3d application is really smooth and responsive. Weirdly enough the L5 is the most responsive device I have testing in terms of responding to inputs where as every other device seems to have a miniscule delay to it. Once the GLES3 driver is in a good enough state to be used by default this will make a really good device to be used as long as you are not doing anything compute heavy and assuming that GLES3 enablement doesen't bring in the tiny delay that I feel on other devices. When not doing intesive things the phone itself is a joy to use as it is really responsive but it all falls apart and is frustrating once it leaves its performance/gpu thresholds.

# Compatibility

From the kernel side, purism and in particular [Sebastian Kryzszkowiak](https://social.librem.one/@dos) has done a great job in getting the L5 into a great spot both downstream and even upstream. With the upstream etnaviv work being done by 3rd party developer [Christian Gmeiner](https://mastodon.social/@austriancoder@fosstodon.org) and with their heavy push recently it should hopefully mean better GLES 3 support so it will not run into the same compatability issues that the original Pinephone runs into where certain apps are not supported and/or runs slowly. Vulkan support is in a similar situation as GLES3 where technically the GPU itself supports it but driver are missing/lacking so there is no current way to use vulkan and I am not familiar if anyone is working on mesa vulkan support similar to what christian is doing for GLES3 but luckily GLES3 should cover a lot of the usecases. The CPU is also similar to the one going to be used by the upcoming Mecha Comet so hopefully that also means improved upstream mainline support down the line as the Mecha team seeems to be prioritizing mainline support and not downstream only. 

Other OS seem to have very little support with [PostmarketOS](https://wiki.postmarketos.org/wiki/Purism_Librem5_(purism-librem5)) seeming to be the only 3rd party OS port that I know of that is actually still being actively maintained. The big benefit of PostmarketOS is that it brings with it a much more recent mesa so it lets you play more with the etnaviv improvements to see a glimps of what the L5 hardware is capable of and should hopefully be like in future PureOS releases such as dawn and onwards. As far as I know there should be much in terms of limiting other OS from being ported to the L5 but it might have trouble attracting other developers that are willing to take that work on due to how expensive the L5 itself is for what it offers in terms of performance today.

# Android

Android support is handled by a minimal [downstream waydroid](https://source.puri.sm/Librem5/debs/waydroid) built on top waydroid 1.6.1 which is from Dec 2025 so not to far behind upstream. Setting it up is as simple as installing Waydroid from the PureOS Store, launching it and tapping the Download button with the default options. With the limited EMMC space on the standard L5 though its very easy to blow through all your free space with the android system setup and running. 

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

The L5 is pretty docking friendly as they support DP-ALT mode and they [themselves push a kit](https://puri.sm/products/lapdock-kit/) with Nex Computer Nexdock lapdock system. I can't seem to get miracast via gnome network displays to work but it does seem like the wireless card itself is atleast capabile of doing p2p but gnome network displays complains about screencasting portal is unavailable even with xdg-desktop-portal-wlr and xdg-desktop-portal-gtk both installed and pipewire running so not sure if there is something else that is missing in crimson or its just a version issue as gnome-network-displays is version 0.90.5 which dates back to 2021.

Docking via DP-ALT mode works and is relatively smooth as long as the hardware itself is able to keep up with the rendering. Connecting to the NexDock works instantly but has issues with the touch screen where instead of the touchscreen mapping to what is displayed on the NexDock itself, its mapping it to the phone screen itself even if you disable the phone screen so usage/navigation is limited to keyboard and mouse only. Phosh docking experience on the included version, 0.34.0 dating back to December 2023, is also not great but hopefully that will improve in future releases of phosh. Other DE may have a better portable and docking experience but since Pureos only supports phosh that is what you are stuck with in terms of support but would be interesting to see what docking would look like on other DEs in PMOS especially once GLES3 is fleshed out.


# Web Browsing

Web browsing on the L5 seems to mostly depend on the browser you are using and how heavy the website is. Firefox and Epiphany are really slow to the point where it is painful to use and you can not watch youtube comfortably even when at 144p. Angelfish while has way better performance to the point where you can atleast watch a youtube video, seems to run into other issues where websites are not sizing correctly so you have a side scroll and occasionally it has display rendering hiccups where it will display cyan blue pixels. Even with those issues though the performance is so much better on angelfish that its worth dealing with them over firefox/epiphany.

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

Aquarium currently doesn't work due to the incomplete GLES 3 so hopefully this improves in the future.

| Fish amount | Firefox | Epiphany | Waydroid Firefox  |
| ----------- | ------- | -------- | ----------------- |
| 100         | N/A     | N/A      | N/A               |
| 500         | N/A     | N/A      | N/A               |
| 1,000       | N/A     | N/A      | N/A               |
| 5,000       | N/A     | N/A      | N/A               |
| 10,000      | N/A     | N/A      | N/A               |
| 15,000      | N/A     | N/A      | N/A               |
| 20,000      | N/A     | N/A      | N/A               |
| 25,000      | N/A     | N/A      | N/A               |
| 30,000      | N/A     | N/A      | N/A               |


# Media Playback

Below is a table of different video codecs and their playback performance. The best results for native seem to come from MPV though 1080p support seems to be at the upper limit so i would try to limit everything to 720p at most and at that point most players are able to handle it.

### Player Information

| Player            | Version  | Method    |
| ----------------- | -------- | --------- |
| MPV               | 0.35.1   | Repo      |
| Clapper           | 0.10.0   | Flatpak   |
| Livi              | 0.0.3    | Repo      |
| Celluloid         | 0.20     | Repo      |
| Firefox           | 140.13.0 | Repo      |
| Waydroid Firefox  | 153.0    | Waydroid  |

### H.264/AVC

| Player            | 1080p@30                                       | 720p@30                                        |
| ----------------- | ---------------------------------------------- | ---------------------------------------------- |
| MPV               | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Clapper           | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Livi              | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Celluloid         | {{ img(src="/icons/cross.svg" alt="No")}}      | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Firefox           | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Waydroid Firefox  | {{ img(src="/icons/cross.svg" alt="No")}}      | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |

---

### H.265/HEVC

| Player            | 1080p@30                                           | 720p@30                                            |
| ----------------- | -------------------------------------------------- | -------------------------------------------------- |
| MPV               | {{ img(src="/icons/cross.svg" alt="No")}}          | {{ img(src="/icons/checkmark.svg" alt="Yes")}}     |
| Clapper           | {{ img(src="/icons/checkmark.svg" alt="Yes")}}     | {{ img(src="/icons/checkmark.svg" alt="Yes")}}     |
| Livi ¹            | {{ img(src="/icons/exclamation.svg" alt="Maybe")}} | {{ img(src="/icons/exclamation.svg" alt="Maybe")}} |
| Celluloid         | {{ img(src="/icons/cross.svg" alt="No")}}          | {{ img(src="/icons/cross.svg" alt="No")}}          |
| Firefox           | {{ img(src="/icons/cross.svg" alt="No")}}          | {{ img(src="/icons/cross.svg" alt="No")}}          |
| Waydroid Firefox  | {{ img(src="/icons/cross.svg" alt="No")}}          | {{ img(src="/icons/checkmark.svg" alt="Yes")}}     |

¹ Performs well but has some minor rendering issues

---

### AV1

| Player            | 1080p@30                                       | 720p@30                                        |
| ----------------- | ---------------------------------------------- | ---------------------------------------------- |
| MPV               | {{ img(src="/icons/cross.svg" alt="No")}}      | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Clapper           | {{ img(src="/icons/cross.svg" alt="No")}}      | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Livi              | {{ img(src="/icons/cross.svg" alt="No")}}      | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Celluloid         | {{ img(src="/icons/cross.svg" alt="No")}}      | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Firefox           | {{ img(src="/icons/cross.svg" alt="No")}}      | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Waydroid Firefox  | {{ img(src="/icons/cross.svg" alt="No")}}      | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |

---

### VP9

| Player            | 1080p@30                                       | 720p@30                                        |
| ----------------- | ---------------------------------------------- | ---------------------------------------------- |
| MPV               | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Clapper           | {{ img(src="/icons/cross.svg" alt="No")}}      | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Livi              | {{ img(src="/icons/cross.svg" alt="No")}}      | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Celluloid         | {{ img(src="/icons/cross.svg" alt="No")}}      | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Firefox           | {{ img(src="/icons/cross.svg" alt="No")}}      | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Waydroid Firefox  | {{ img(src="/icons/cross.svg" alt="No")}}      | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |


# Camera

Camera on the L5 is in a pretty good spot right now compared to other linux phones when going through millipixels, their own downstream camera application. Sebastian/dos has done really great work on the postprocessing side of things to get this useful in everyday life with colors all looking great and processing speed being the fastest on non-isp based camera stacks, fast enough to not be annoying like it is with the initial PP/PPP megapixels implementations. You can find camera examples on [mastodon under #shotonlibrem5](https://mastodon.social/tags/shotonlibrem5) and I also took some on my trip to [Calsbad Caverns New Mexico](https://photos.luigi311.com/s/carlsbad-librem5) which stressed its low light performance. On my trip, focus wasn't always great since auto finding the maximum focus point can sometimes be slow but when things are in focus the pictures come out great!

| Library        |                                      Supported |
| -------------- | ---------------------------------------------: |
| Libcamera      | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| LibMegapixels  | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |


| Abstraction Layer |                                      Supported |
| ----------------- | ---------------------------------------------: |
| v4l2              |  |
| Gstreamer         |  |
| Qcamera           |  |
| Pipewire ¹        | {{ img(src="/icons/exclamation.svg" alt="Maybe")}} |

¹ Possible but not enabled out of the box in crimson https://forums.puri.sm/t/lib-rem5-camera-to-use-everywhere/28090/22

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

Support for the L5 has had its ups and downs over the years wiplashing from one extreme to the other. 

The L5 had an atrocious launch with the entire preorder/delay fiasco. This soured all forms of support for purism and the L5 and is responsible for a lot of the current negative sentiment towards the L5.

Once it was released support seemed to be on the good side with lots of software development happening to get things to a usable state in terms of making applications mobile friendly and development new applications. Lots of work was also making their way upstream to applications and the linux kernel and lead to lots of improvements into the entire mobile linux ecosystem. 

Then we hit a massive rough spot with a really long period where software development basically came to a complete halt. There was very little happening in terms of software development and it seems like the entire software development team was actually let go with no signs of any of them returning.

In 2024 Purism added their PureOS subscription to optionally help them fund the development of PureOS and work on their next release crimson. At this point blog post after blog post of their development reports continued to come out and they were making progress, slowly but progress was being made and things were being redesigned.

Finally in mid 2026 PureOS released their next L5 OS, crimsion, which is based on Debian 12 Bookworm, bringing application releases from 2021 to 2023 so now its only 3 years behind instead of the now 5 years behind we were stuck with.

Luckily since then it seems like they have been full steam ahead to their next debian rebase for PureOS dawn built on top of Debian 13 trixie which will hopefully bring software up to the current year of 2026 and hopefully its release isn't so delayed like crimson was that by the time it releases it will be massively out of date too. Hopefully their rebase to crimsion allowed them to redesign and cleanup a lot of what made that transition so long and painful and puts them in a way better position to rebase for future releases.

As it currently stands Purism does seem to be focusing on continued development of the L5 but with such a massive swings back and forth its hard to tell how long their motivation will continue. The good thing is, they do have a strong focus on upstreaming their kernel development which is the most important piece of this and that means that down the line any OS could potentially add in L5 support and handle the OS side of things and keeping that part of the system up to date. They are also one of the few linux first mobile device company that is actually handling the software development internally and publishing their development out to the greater mobile linux ecosystem.


# Conclusion

The Librem 5 is a tricky device, it's great at what it does, it's really awful at what it doesn't do, its future was really negative at some points in its life but it's currently looking as best as it ever has been. Responsiveness is best in class even though its overall performance is not that great. The camera processing is also really good and fast allowing it to actually be useful out in the real world unlike other mainline linux devices which are lacking in terms of focus and color.

While it's hard to recommend a product based on what the future might be for it, its even harder to recommend a device with not even a potential future such as the Pinephone (Pro) at this point. As of right now atleast the L5 has a potential positive future with vendor support at a high point and 3rd party graphics driver development really hitting its strides right now making leaps and bounds and its work making its way upstream. If the current momentum continues, the L5 will stand to become a really useful device in the mobile linux world even though it has aging hardware.

As things currently stand right now, I think purchasing the L5 should only be done if you are looking for a way to fund its future development. To tell purism that you are interested in the work they are doing and want to financially support them so they do not stop their work and you support their mission/ethos. There have been talks for a long time about a refreshed L5, Fir/v2, and looks like it is still in the plans and is [currently in progress](https://forums.puri.sm/t/librem-5-fir-batch/9491/223) and I hope to hear something soon about it.

If you care about price to performance then there are now a few way better devices that also include vendor provided support one way or another so I would recommend to look more for those devices first and only fall back to the current L5 if it provides a niche usecase that the other devices to not meet. 

Up until the last couple of years it was hard to recommend any of the other devices because there were very few that fit the bill of being able to make phone calls on your phone, but things have recently been changing with more and more having a more reliable ceullar stack and actually supporting VoLTE so it could even make calls in the US, so it is no longer just the pinephones and the librem 5 only at this point that can be used as actual cellphones. 


# My Involvement / Disclosures

My involvement with Librem 5/purism is very minimal, i've interacted with the developers a few times over social media. I do like purism as a company and what they stand for, when they are standing behind it, and hope they continue to exist long into the future. As such I have purchased the Librem 5 directly from them with my own money for testing and subscribe to their $10/month PureOS subscription to help them finanically continue development. I will also be purchasing their Librem 5 V2, assuming it ever actually gets released and am excited to see what purism can accomplish with more modern hardware.
