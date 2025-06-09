+++
title = "Furilabs FLX1"
description = "Information about the Furilabs FLX1, its features and limitations."
date = 2025-06-09
draft = false

[taxonomies]
tags = ["Phones", "Furilabs", "Halium", "Mobile Linux"]
[extra]
keywords = "Phones, Markdown, Furilabs, Halium, Mobile Linux"
toc = true
series = "Phones"
+++

- Performance: 4/5
- Affordability: Great price for the hardware and support provided
- Compatibility: 3/5
- Battery Life: 5/5


# Setup information
- OS: FuriOS 13.0.9
- Kernel: 4.19.325
- DE: Phosh


# Hardware Supported

| Hardware              | Supported                                      |
|-----------------------|------------------------------------------------|
| GPS                   | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| aGPS ¹                | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Cameras               | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Microphone            | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Bluetooth ²           | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Modem                 | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| NFC                   | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Fingerprint           | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Accel/Tilt/Step/Wake  | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Orientation/Gyroscope | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Light/Pressure        | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Proximity             | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| NPU                   | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |

¹ Not hardware but important usability feature and is optional  
² Bluetooth is working but uses bluez and that seems to have difficulty connecting to some devices

Some hardware is a grouping as those are all functions handled by a single sensor on the device and exposed as different metrics.

# Cell Service

Cell service was tested in the US utilizing US Mobile MVNO, [referral link](https://www.usmobile.com/referrals?referrer=0178DFD2&name=Luis&utm_campaign=monster_referral), as it allows for easy testing of the 3 major US network providers. The only downside is the TMobile service has deprioritized download speeds so your speeds can be on the slower side like mine based on location and network traffic. Download/Upload speed tests were done using ookla [speedtest.net](https://speedtest.net) and netflix [fast.com](https://fast.com) with the data waster option enabled. As service seems to vary from moment to moment, I ran multiple tests and grabbed the best results for each section. Light Speed (Tmobile) seems to work perfectly without any issues, while the FLX1 does support the bands for 5g, the 5g connection in the US seems to be unstable and causes issues. In my case with the 5g bands enabled, the phone would no longer connect to service so I had to stay on the 4g network. I have seen reports that lots of people outside the US use 5g without any issues. I've attempted Dark Star (AT&T) and ran into issues getting a complete connection, data wasnt working but was able to make calls and text. 

I also put in my JMP.Chat eSIM with their data plan and while the phosh settings says AT&T, speedtest says its T-Mobile and I dont have a reliable way to validate it since they route it so you come out of Poland for privacy reasons. The eSIM works on my FLX1 and even has a built in way to change profiles and add new profiles, it is clunky but it is enough to get the job done. It does not work with [eSIM Manager](https://codeberg.org/lucaweiss/lpa-gtk), hopefully it will in the future or the build in app is improved.

## US Mobile Light Speed (Tmobile)

| Phone   | Tech | Speedtest down | Fast down | Fast up  | VoLTE / VoNR                                   |
| :------ | :--- | -------------: | --------: | -------: | :--------------------------------------------: |
| FLX1    | 4G   |      10.7 Mbps |  9.6 Mbps | 8.0 Mbps | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Pixel 6 | 5G   |      86.6 Mbps |  100 Mbps |  12 Mbps | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Pixel 6 | 4G   |      25.2 Mbps |   23 Mbps |  12 Mbps | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |

## JMP.Chat Data Plan

| Phone   | Tech | Speedtest down | Fast down | Fast up  |
| :------ | :--- | -------------: | --------: | -------: |
| FLX1    | 4G   |      6.2 Mbps |  9.3 Mbps | 5.0 Mbps |
| Pixel 6 | 4G   |     13.1 Mbps |   10 Mbps |  10 Mbps |

# Performance

The FLX1 is a fast phone in general. The Mediatek Dimensity 900 is a fast SOC especially compared to the pinephone/pinephone pro/librem 5 devices. It comes with 6GB of RAM , which is more than enough for most tasks but can be limiting. Web browsing and media playback are fast and smooth. Android container is fully supported with acceleration working well and the performance is great. There are some acceleration issues with flatpak qt6 based applications due to upstream QT flatpak gles issues. Flatpak qt5/gtk4 and native qt5/qt6/gtk4 are all accelerated and seem to be working without issues.


# Compatibility

The FLX1 is a halium based device so it is limiting to what OS/DE you can run on it. Currently you can run both FuriOS and Ubuntu Touch, though FuriOS is the only one officially supported by the FuriLabs team. You wont be able to run any of the other mainline OS though like arch and postmarketos. For desktop environments (DE) you are also limited to Phosh in FuriOS and Lomiri in the Ubuntu Touch port. GTK based applications seem to function the best while some QT based applications have issues such as acceleration and/or failing to launch like angelfish due to upstream issues around GLES support and inclusion in the flatpak builds. The FLX1 also supports multiboot allowing you to install multiple OS side by side. This makes it simple to test new changes without breaking your main image or even testing out separate different OS as they are released. The app they created to manage this is bootman and once an OS is integrated with it then its as simple as telling it to create a new partition of X size and telling it what OS to flash onto the partition. It will then show up as a touch interface when turning the phone on to select what OS/Partition you want to boot into.


# Android

Android support is amazing with lots of sensors passed through to the container, listed below. The android system is called [Andromeda](https://github.com/FuriLabs/andromeda) which forked off Waydroid and has made tons of improvements and updates to the base android system. You should be able to run most android applications without any issues except the usually culprits that have Integrity API (Safetynet replacement) like banking apps. Video playback works and I can confirm Grayjay works perfectly except the volume control guesture control. Android also integrated perfectly with the rest of the OS with all your android applications showing up in the app drawer. There is a gnome software plugin so you can search and install android apps from fdroid through the gnome software store as if it was a native application removing the need to manually open fdroid. There's a android section in the gnome settings that exposes a lot of android settings to the user as shown below.

{{ resize_image(path="/furilabs-flx1/FLX1_Gnome_Settings_Android.png", width=480, alt="FuriOS Android Settings") }}


## Sensors passed to Android

Tested using [Sensors Toolbox](https://play.google.com/store/apps/details?id=com.exatools.sensors&hl=en_US) app

| Sensor              | Passed through |
|---------------------|----------------|
| GPS                 | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Cameras             | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Microphone          | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Bluetooth           | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Modem               | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| NFC                 | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Fingerprint         | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Accelerometer       | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Geomagnetic         | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Orientation         | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Gyroscope           | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Light               | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Pressure            | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Proximity           | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Gravity             | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Linear Acceleration | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | 
| Rotation Vector     | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Step Counter        | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |


# Docking

The FLX1 docking is in a weird position as the hardware does not support usb dp-alt mode but they are still able to utilize evdi to get output externally. They are also working on a wireless solution like what UT has with Miracast. Neither of these options are avaliable publically though so only time will tell how well it works out and how universal the solutions are.


# Web Browsing

Web browsing works really well. Firefox runs well and comes with a custom configuration similar to postmarketos  mobile-config-firefox for a better experience on mobile screens. Benchmarking results with [speedometer 3.1](https://browserbench.org/Speedometer3.1/) with scale set to 100% are below, based on results I would recommend sticking with firefox. If you do have andromeda running in the background then running firefox in it is also an option and has great performance since a lot is accelerated.

| Browser           | Score               | Version | Toolkit  | Install    |
|-------------------|---------------------|---------|----------|------------|
| Firefox           | 2.54 &plusmn; 0.074 | 135.0.1 | Gecko    | Repo       |
| Angelfish ¹       | N/A                 | 25.04.1 | Chromium | Flatpak    |
| Epiphany          | 1.86 &plusmn; 0.065 | 48.3    | WebKit   | Flatpak    |
| Kumo ¹            | N/A                 | 1.1.0   | Webkit   | Flatpak    |
| Andromeda Firefox | 4.43 &plusmn; 0.066 | 138.0.3 | Gecko    | Andromeda  |

¹ Fails to launch

# Media Playback

Below is a table of different video codecs and their playback performance. The hardware has support for decoding h264/h265/vp9 and they are working on adding in the software support necessary. The best results for native seem to come from MPV/Celluloid/firefox so as long as you are using any of those performance should be fine and inline with each other.

### Player Information

| Player            | Version  | Method    |
|-------------------|----------|-----------|
| MPV               | 0.40.0   | Repo      |
| Clapper           | 0.8.0    | Flatpak   |
| Livi              | 0.3.1    | Flatpak   |
| Celluloid         | 0.28     | Repo      |
| Firefox           | 135.0.1  | Repo      |
| Andromeda Firefox | 138.0.3  | Andromeda |

### H.264/AVC

| Player    | 1080p@30    | 720p@30    |
|-----------|-------------|------------| 
| MPV       | {{ img(src="/icons/checkmark.svg" alt="Yes")}}        | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Clapper   | {{ img(src="/icons/cross.svg" alt="No")}}             | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Livi      | {{ img(src="/icons/cross.svg" alt="No")}}             | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Celluloid | {{ img(src="/icons/checkmark.svg" alt="Yes")}}        | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Firefox   | {{ img(src="/icons/checkmark.svg" alt="Yes")}}        | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Andromeda Firefox | {{ img(src="/icons/checkmark.svg" alt="Yes")}}        | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |

---
### H.265/HEVC

| Player    | 1080p@30    | 720p@30    |
|-----------|-------------|------------| 
| MPV       | {{ img(src="/icons/checkmark.svg" alt="Yes")}}       | {{ img(src="/icons/checkmark.svg" alt="Yes")}}       |
| Clapper   | {{ img(src="/icons/cross.svg" alt="No")}}            | {{ img(src="/icons/checkmark.svg" alt="Yes")}}       |
| Livi ¹     | {{ img(src="/icons/cross.svg" alt="No")}}            | {{ img(src="/icons/cross.svg" alt="No")}}            |
| Celluloid | {{ img(src="/icons/checkmark.svg" alt="Yes")}}       | {{ img(src="/icons/checkmark.svg" alt="Yes")}}       |
| Firefox ¹  | {{ img(src="/icons/cross.svg" alt="No")}}            | {{ img(src="/icons/cross.svg" alt="No")}}            |
| Andromeda Firefox | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |

¹ No video output at all

---
### AV1

| Player    | 1080p@30    | 720p@30    |
|-----------|-------------|------------| 
| MPV       | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Clapper   | {{ img(src="/icons/cross.svg" alt="No")}}      | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Livi      | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Celluloid | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Firefox   | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Andromeda Firefox | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |

---
### VP9

| Player    | 1080p@30    | 720p@30    |
|-----------|-------------|------------| 
| MPV       | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Clapper   | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Livi      | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Celluloid | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Firefox   | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Andromeda Firefox | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |


# Camera

The phone does not support libcamera and megapixels like mainline linux phones. Instead it has it's own camera stack and exposes the cameras out via v4l, gstreamer, qcamera and pipewire. This allows it to be used universally by other applications. For example for video chatting through firefox. The camera quality is really good and the processing is instant as it's using the mediatek isp. The camera application also opens up quickly. It can also capture video with audio correctly in sync. The phone has 3 camera sensors and all them are supported and exposed individually. There is no advance mode to manually control WB, ISO, codec, etc but it does have tap to auto adjust the focus/wb/iso and it works really well.

| Library        |  Supported                                     | 
|----------------|-----------------------------------------------:|
| Libcamera      | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Droidmedia     | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| CameraProvider | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |


| Abstraction Layer   |  Supported                                     |
|---------------------|-----------------------------------------------:|
| LibMegapixels       | {{ img(src="/icons/cross.svg" alt="No")}}      |
| v4l2                | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Gstreamer           | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Qcamera             | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Pipewire            | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |

## Example

| Temp   | Kelvin | Led   |
|--------|--------|-------|
| Normal | 5000k  | B35AM |
| Low    | 2500k  | 519A 3500K dedome  |

| Light  | Description |
|--------|-------------|
| Medium | Convoy S21B 3rd click, Emisar DW4 High Ramp |
| Low    | Convoy S21B 1st click, Emisar DW4 Moonlight |

Flashlights were pointed at the ceiling and everything left on auto, Pixel 6 and Iphone 12 both have a night mode where it took 3s for the low light photos

## Normal Temp Medium Light

| FLX1 | Pixel 6| iPhone 12 |
|------|--------|-----------|
| {{ resize_image(path="/furilabs-flx1/camera/FLX1_Normal_Temp_Medium_Lux.jpg", width=360, alt="FLX1 B35AM 5000k Medium Light") }} | {{ resize_image(path="/furilabs-flx1/camera/Pixel_6_Normal_Temp_Medium_Lux.jpg", width=360, alt="Pixel 6 B35AM 5000k Medium Light") }} | {{ resize_image(path="/furilabs-flx1/camera/Iphone_12_Normal_Temp_Medium_Lux.jpg", width=360, alt="iPhone 12 B35AM 5000k Medium Light") }} |

## Normal Temp Low Light

| FLX1 | Pixel 6| iPhone 12 |
|------|--------|-----------|
| {{ resize_image(path="/furilabs-flx1/camera/FLX1_Normal_Temp_Low_Lux.jpg", width=360, alt="FLX1 B35AM 5000k Low Light") }} | {{ resize_image(path="/furilabs-flx1/camera/Pixel_6_Normal_Temp_Low_Lux.jpg", width=360, alt="Pixel 6 B35AM 5000k Low Light") }} | {{ resize_image(path="/furilabs-flx1/camera/Iphone_12_Normal_Temp_Low_Lux.jpg", width=360, alt="iPhone 12 B35AM 5000k Low Light") }} |

## Low Temp Medium Light

| FLX1 | Pixel 6| iPhone 12 |
|:----:|:------:|:---------:|
| {{ resize_image(path="/furilabs-flx1/camera/FLX1_Low_Temp_Medium_Lux.jpg", width=360, alt="FLX1 519a 3500K DD Medium Light") }} | {{ resize_image(path="/furilabs-flx1/camera/Pixel_6_Low_Temp_Medium_Lux.jpg", width=360, alt="Pixel 6 519a 3500K DD Medium Light") }} | {{ resize_image(path="/furilabs-flx1/camera/IPhone_12_Low_Temp_Medium_Lux.jpg", width=360, alt="iPhone 12 519a 3500K DD Medium Light") }} |

## Low Temp Low Light

| FLX1 | Pixel 6| iPhone 12 |
|:----:|:------:|:---------:|
| {{ resize_image(path="/furilabs-flx1/camera/FLX1_Low_Temp_Low_Lux.jpg", width=360, alt="FLX1 519a 3500K DD Low Light") }} | {{ resize_image(path="/furilabs-flx1/camera/Pixel_6_Low_Temp_Low_Lux.jpg", width=360, alt="Pixel 6 519a 3500K DD Low Light") }} | {{ resize_image(path="/furilabs-flx1/camera/IPhone_12_Low_Temp_Low_Lux.jpg", width=360, alt="iPhone 12 519a 3500K DD Low Light") }} |



# Battery Life

The phone has amazing battery life with the screen on and on standby. Standby is also different from the mainline devices as it does not use deep sleep. Instead it uses a low power mode, this allows it to continue running applications and keep network alive. This has the major benefit of allowing you to ssh in at anytime and continue to receive notifications from all apps including web based apps. Charging speed is also great supporting Power Delivery at 10v 3a allowing you to get multiple hours of battery life with just a handful of minutes on the charger. 

Testing was done using the following settings:

- Screen brightness set to 50%
- Screen timeout disabled
- Measured from 100% battery to device shutdown
- Without android unless specified
- With sim unless specified
- With Wifi enabled
- Video playback is 720p 30 fps
- Charge time tested on pinepower v1 desktop
- Prometheus polling every 15 seconds

## Screen Time

| Method                           | Battery Life | Drain Per Hour |
|----------------------------------|-------------:|---------------:|
| Screen on                        | 9.82 hours   | 10.18%         |
| Screen on + Android              | 8.83 hours   | 11.32%         |
| Screen on + Stress CPU           | 4.86 hours   | 20.58%         |
| Screen on without sim            | 10.11 hours  | 9.89%          |

---

## Video Playback

| Method                           | Battery Life | Drain Per Hour |
|----------------------------------|-------------:|---------------:|
| MPV                              | 6.43 hours   | 15.55%         |
| Firefox                          | 6.90 hours   | 14.49%         |
| Andromeda Firefox                | 6.67 hours   | 14.99%         |

---

## Standby

- prometheus polling every 30 mins

| Method                           | Battery Life | Drain Per Hour |
|----------------------------------|-------------:|---------------:|
| Standby                          | 4.47 days    | 0.93%          |
| Standby + Android                | 3.19 days    | 1.30%          |
| Standby without sim              | 7.86 days    | 0.53%          |

---

## Charging

| Method                           | Charging Time |
|----------------------------------|--------------:|
| Charge 0-80%                     | 51.5 mins     |

### Charging Curve

- Prometheus polling every 5 seconds
- Measured from Sonoff S31 running esphome

{{ resize_image(path="/furilabs-flx1/Charge_Curve.png", width=1080, alt="FX1 Battery charging curve") }}

# Support

Support from FuriLabs has been outstanding. They are all constantly in the telegram group so when issues are discovered by endusers and they mention it in the chat they are able to immediately replicate it on their side so they can troubleshoot and fix it. They also have a great system to allow users to test fixes similar to Ubuntu Touch where there is a new repository for each fix that the user can install and uninstall. While UT requires the user to use the terminal to install said repository the FuriLabs folks have instead decided to create a GUI so even users that are terminal shy can test fixes and provide feedback. Overall getting ahold of them and getting software support from them is amazing but I have yet to interact with them when it comes to hardware defects so I can't comment on their warranty experience.


# Conclusion

This is a great device for the price when you consider both performance and support. It is constantly getting new improvements and updates. The phone is great to use and the battery life is amazing. The camera is good and better than all mainline linux phones I have tested, pp/ppp/l5. The only downside is the lack of software support for other OSes and DEs but that is expected with a halium devices. The docking situation is a bummer but will hopefully improve soon. Even with those caveats it is still a great device to use and I would 100% recommend it to anyone looking for a linux phone that is usable.


# My Involvement / Disclosures

I've followed Bardia, the CEO, development over the years across different devices prior to founding FuriLabs, while he was working on Droidian. While he was working on droidian, I financially donated to him in order for him to acquire hardware.

The FLX1 was purchased with my own money and I was the first one to official purchase a device from them. I did feel confident purchasing the device when they first opened up and their promise for support because of my connection and good experience with Bardia. I minimally contribute to their development, mostly on the user side of things like their gallery app and andromeda system. Everything ive contributed on the software side is open in my [Github](https://github.com/luigi311) and tagged as such on their official repos. I also currently participate in their software QA testing prior to its public release when I have time.
