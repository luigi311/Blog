+++
title = "Manufacture Device"
description = "Information about the Manufacture Device"
date = 2025-03-09
draft = true

[taxonomies]
tags = ["Phones"]
[extra]
keywords = "Phones"
toc = true
series = "Phones"
+++

- Performance: /5
- Affordability: /5
- Compatibility: /5
- Battery Life: /5


# Setup information
- OS: 
- Kernel: 
- DE: 


# Hardware Supported

| Hardware            | Supported                                            |
|---------------------|------------------------------------------------------|
| GPS                 |        |
| aGPS¹               |        |
| Cameras             |        |
| Microphone          |        |
| Bluetooth²          | {{ img(src="/icons/exclamation.svg" alt="Partial")}} |
| Modem               |        |
| NFC                 |        |
| Fingerprint         |        |
| Accelerometer       |        |
| Orientation         |        |
| Light               |        |
| Proximity           |        |
| NPU                 |        |
| Step Counter        |        |

---
¹  
² 


# Cell Service

Cell service was tested in the US utilizing US Mobile MVNO, [referral link](https://www.usmobile.com/referrals?referrer=0178DFD2&name=Luis&utm_campaign=monster_referral), as it allows for easy testing of the 3 major US network providers. The only downside is the TMobile service has deprioritized download speeds so your speeds can be on the slower side like mine based on location and network traffic. Download/Upload speed tests were done using ookla [speedtest.net](https://speedtest.net) and netflix [fast.com](https://fast.com)

## US Mobile Warp (Verizon)

| Phone   | Tech | Speedtest down | Fast down | Fast up | VoLTE / VoNR                                   |
| :------ | :--- | -------------: | --------: | ------: | :--------------------------------------------: |
|         |      |              X |         X |       X | |
| Pixel 6 | 5G   |              X |         X |       X | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |


## US Mobile Dark Star (AT&T)

| Phone   | Tech | Speedtest down | Fast down | Fast up | VoLTE / VoNR                                   |
| :------ | :--- | -------------: | --------: | ------: | :--------------------------------------------: |
|         |      |              X |         X |       X | |
| Pixel 6 | 5G   |              X |         X |       X | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |


## US Mobile Light Speed (Tmobile)

| Phone   | Tech | Speedtest down | Fast down | Fast up  | VoLTE / VoNR                                   |
| :------ | :--- | -------------: | --------: | -------: | :--------------------------------------------: |
|         |      |              X |         X |        X |  |
| Pixel 6 | 5G   |              X |         X |        X | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |

# Performance

Talk about CPU/Memory, its limitations if any. Experience with web browsers and media playback


# Compatibility

What OS and DEs can it run. Any issues with GTK or QT?


# Android

Waydroid experience overview. Any downstream features if manufacture downstream support


## Sensors passed to Android

Tested using [Sensors Toolbox](https://play.google.com/store/apps/details?id=com.exatools.sensors&hl=en_US) app

| Sensor              | Passed through |
|---------------------|----------------|
| GPS                 |  |
| Cameras             |  |
| Microphone          |  |
| Bluetooth           |       |
| Modem               |  |
| NFC                 |  |
| Fingerprint         |  |
| Accelerometer       |  |
| Geomagnetic         |  |
| Orientation         |       |
| Gyroscope           |  |
| Light               |  |
| Pressure            |  |
| Proximity           |  |
| Gravity             |  |
| Linear Acceleration |  | 
| Rotation Vector     |       |
| Step Counter        |  |


# Docking

Hows docking support using a usb c dock and/or the nexdock. Wireless display support?


# Web Browsing

Benchmarking results with [speedometer 3.1](https://browserbench.org/Speedometer3.1/) with scale set to 100% are below. 

Any downstream manufacture specific changes?

| Browser           | Score               | Version | Toolkit  | Install    |
|-------------------|---------------------|---------|----------|------------|
| Firefox           |                     |         | Gecko    |            |
| Angelfish         |                     |         | Chromium |            |
| Epiphany          |                     |         | WebKit   |            |
| Kumo              |                     |         | Webkit   |            |
| Waydroid Firefox |                     |         | Gecko    |            |


# Media Playback

Overview of media playback such as what is recommended to be used

### Player Information

| Player            | Version  | Method    |
|-------------------|----------|-----------|
| MPV               |          |           |
| Clapper           |          |           |
| Livi              |          |           |
| Celluloid         |          |           |
| Firefox           |          |           |
| Waydroid Firefox  |          |           |

### H.264/AVC

#### 1080p@30fps

| Player            | Realtime Playback | Hardware Acceleration |
|-------------------|-------------------|-----------------------|
| MPV               |        |       |
| Clapper           |        |       |
| Livi              |        |       |
| Celluloid         |        |       |
| Firefox           |        |       |
| Waydroid Firefox  |        |       |


#### 720p@30fps

| Player            | Realtime Playback | Hardware Acceleration |
|-------------------|-------------------|-----------------------|
| MPV               |  |   |
| Clapper           |  |   |
| Livi              |  |   |
| Celluloid         |  |   |
| Firefox           |  |   |
| Waydroid Firefox  |  |   |


---
### H.265/HEVC

#### 1080p@30fps

| Player           | Realtime Playback | Hardware Acceleration |
|------------------|-------------------|-----------------------|
| MPV              |  |  |
| Clapper          |  |  |
| Livi             |  |  |
| Celluloid        |  |  |
| Firefox²         |  |  |
| Waydroid Firefox |  |  |

¹ Stutters on render  
² No video output at all


#### 720p@30fps

| Player           | Realtime Playback | Hardware Acceleration |
|------------------|-------------------|-----------------------|
| MPV              |  |  |
| Clapper          |  |  |
| Livi²            |  |  |
| Celluloid        |  |  |
| Firefox²         |  |  |
| Waydroid Firefox |  |  |


---
### AV1

#### 1080p@30fps

| Player           | Realtime Playback | Hardware Acceleration |
|------------------|-------------------|-----------------------|
| MPV              |  |  |
| Clapper          |  |  |
| Livi             |  |  |
| Celluloid        |  |  |
| Firefox          |  |  |
| Waydroid Firefox |  |  |



#### 720p@30fps

| Player           | Realtime Playback | Hardware Acceleration |
|------------------|-------------------|-----------------------|
| MPV              |  |  |
| Clapper          |  |  |
| Livi             |  |  |
| Celluloid        |  |  |
| Firefox          |  |  |
| Waydroid Firefox |  |  |


---
### VP9

#### 1080p@30fps

| Player           | Realtime Playback | Hardware Acceleration |
|------------------|-------------------|-----------------------|
| MPV              |  |  |
| Clapper          |  |  |
| Livi             |  |  |
| Celluloid        |  |  |
| Firefox          |  |  |
| Waydroid Firefox |  |  |


#### 720p@30fps

| Player           | Realtime Playback | Hardware Acceleration |
|------------------|-------------------|-----------------------|
| MPV              |  |  |
| Clapper          |  |  |
| Livi             |  |  |
| Celluloid        |  |  |
| Firefox          |  |  |
| Waydroid Firefox |  |  |


# Camera

Talk about the camera stack and support. Quality, speed. Video and Audio? 

| Library        |  Supported                                     | 
|----------------|------------------------------------------------|
| Libcamera      |  |
| Droidmedia     |  |
| CameraProvider |  |


| Abstraction Layer   |  Supported                                     |
|---------------------|------------------------------------------------|
| LibMegapixels       |  |
| v4l2                |  |
| Gstreamer           |  |
| Qcamera             |  |
| Pipewire            |  |

## Example

| Temp   | Kelvin | Led                |
|--------|--------|--------------------|
| Normal | 5000k  | B35AM              |
| Low    | 2500k  | 519A 3500K dedome  |

| Light  | Description |
|--------|-------------|
| Medium | Convoy S21B 3rd click pointed at ceiling |
| Low    | Emisar DW4 Minimum brightness. Ceiling for superman. Direct from distance for color checker |

## Superman Normal Temp Medium Light

|      |        |           |
|------|--------|-----------|
| {{ resize_image(path="", width=360, alt="") }} | {{ resize_image(path="", width=360, alt="") }} | {{ resize_image(path="", width=360, alt="") }} |

## Superman Low Temp Low Light

|      |        |           |
|------|--------|-----------|
| {{ resize_image(path="", width=360, alt="") }} | {{ resize_image(path="", width=360, alt="") }} | {{ resize_image(path="", width=360, alt="") }} |

## Color Normal Temp Medium Light

|      |        |           |
|------|--------|-----------|
| {{ resize_image(path="", width=360, alt="") }} | {{ resize_image(path="", width=360, alt="") }} | {{ resize_image(path="", width=360, alt="") }} |

## Color Low Temp Low Light

|      |        |           |
|------|--------|-----------|
| {{ resize_image(path="", width=360, alt="") }} | {{ resize_image(path="", width=360, alt="") }} | {{ resize_image(path="", width=360, alt="") }} |


# Battery Life

Talk about battery life, suspend, standby

Testing was done using the following settings:

- Screen brightness set to 50%
- Screen timeout disabled
- Measured from 100% battery to device shutdown except for standby
- Without android unless specified
- With sim unless specified
- Video playback is 720p 30 fps

| Method                           | Battery Life |
|----------------------------------|-------------:|
| Screen on                        |  |
| Screen on + Android              |  |
| Screen on without sim            |  |
| MPV Video Playback               |  |
| Firefox Video Playback           |  |
| Waydroid Firefox Video Playback  |  |
| Stress cpu                       |  |
| Standby                          |  |
| Standby without sim              |  |
| Standby + Android                |  |


# Support

community supports? manufacture supported?


# Conclusion


