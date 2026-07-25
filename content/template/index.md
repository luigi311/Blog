+++
title = "Template"
description = "Template"
date = 2026-05-25
draft = true

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

- OS: 
- Kernel: 
- DE: 

# Introduction



# Hardware Supported

| Hardware              | Supported                                      |
| --------------------- | ---------------------------------------------- |
| GPS ²                 |   |
| aGPS ¹                |   |
| Cameras               |   |
| Microphone            |   |
| Bluetooth             |   |
| Modem                 |   |
| Accel/Tilt/Step/Wake  |   |
| Orientation/Gyroscope |   |
| Light/Pressure        |   |
| Proximity             |   |
| NPU                   |   |

¹ Not hardware but important usability feature and is optional

Some hardware is a grouping as those are all functions handled by a single sensor on the device and exposed as different metrics.

# Cell Service

Cell service was tested in the US utilizing US Mobile MVNO, [referral link](https://www.usmobile.com/referrals?referrer=0178DFD2&name=Luis&utm_campaign=monster_referral), as it allows for easy testing of the 3 major US network providers. The only downside is the TMobile service has deprioritized download speeds so your speeds can be on the slower side like mine based on location and network traffic. Download/Upload speed tests were done using ookla [speedtest.net](https://speedtest.net) and netflix [fast.com](https://fast.com) with the data waster option enabled. As service seems to vary from moment to moment, I ran multiple tests and grabbed the best results for each section.

Light Speed (Tmobile) seems to work great without any issues. While the FLX1s does support the bands for 5g, the 5g connection in the US seems to be unstable and causes issues as a result I have disabled the 5g bands. I have seen reports that lots of people outside the US use 5g without any issues. Dark Star (AT&T) along with Warp (Verizon) do not work as the upstream carrier have blocks in place for phones that have not gone through their certification process, which furilabs as a small company has not had the resources to go through.



## US Mobile Light Speed (Tmobile)

|  Phone    | Tech | Speedtest down | Fast down | Fast up  |                  VoLTE / VoNR                  |
| :-------: | :--: | :------------: | :-------: | :------: | :--------------------------------------------: |
| Librem 5  |  4G  |       |    |  |  |
| Pixel 6   |  5G  |   53.8 Mbps    |  45 Mbps  | 30 Mbps  |   {{ img(src="/icons/cross.svg" alt="No")}}    |
| Pixel 6   |  4G  |   81.9 Mbps    |  65 Mbps  | 12 Mbps  | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |

# Performance


# Compatibility


# Android


## Sensors passed to Android

Tested using [Sensors Toolbox](https://play.google.com/store/apps/details?id=com.exatools.sensors&hl=en_US) app

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


# Web Browsing


| Browsers          | Version | Toolkit      | Install   |
| ----------------- | ------- | ------------ | --------- |
| Firefox           |  | Gecko        | Repo      |
| Angelfish         |  | Chromium     | Flatpak   |
| Epiphany          |  | WebKit       | Flatpak   |
| Kumo              |  | Webkit/servo | Flatpak   |
| Waydroid Firefox  |  | Gecko        | Waydroid  |

## Speedometer 3.1

| Browser           | Score               |
| ----------------- | ------------------- |
| Firefox           |  |
| Angelfish         |  |
| Epiphany          |  |
| Kumo              |  |
| Waydroid Firefox  |  |


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
