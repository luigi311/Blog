+++
title = "Pinephone Pro"
description = "Information about the Pinephone Pro"
date = 2025-03-09
draft = false

[taxonomies]
tags = ["Phones", "Pine", "Mainline", "Mobile Linux"]
[extra]
keywords = "Phones, Markdown, Pine, Mainline, Mobile Linux"
toc = true
series = "Phones"
+++

- Performance: 3/5
- VoLTE Calls: Supported
- GPS and aGPS: 
- Affordability: Expensive for the hardware provided
- Compatibility: 5/5
- Camera Support:
    * Libcamera: Supported
    * Megapixels: Supported
    * v4l2: Supported
    * Gstreamer: Supported
    * Qcamera: Supported
- Battery Life: /5

# Setup information
- OS: PostmarketOS Edge
- Kernel: 6.13.0
- DE: Phosh


# Performance




# Compatibility




# Android



## Sensors passed to Android

| Sensor              | Passed through |
|---------------------|----------------|
| GPS                 |  |
| Cameras             |  |
| Microphone          |  |
| Bluetooth           |  |
| Modem               |  |
| NFC                 |  |
| Fingerprint Sensor  |  |
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
| Step Counter        |   |




# Docking




# Web Browsing

Web browsing works really well. Firefox is a custom build that they maintain internal with improvements to performance and scaling to make it more mobile friendly. Due to it being a custom build it is possible for it to fall behind a few releases due to diffs in new releases but so far they are on top of it and the changes are amazing. Benchmarking results with [speedometer 3.0](https://browserbench.org/Speedometer3.0/) are below but I would recommend sticking with firefox. Angelfish does not launch at all.

| Browser | Score | Version | Toolkit | Install Method |
|---------|-------|---------|---------|--------|
| Firefox |   | 135.0.1 | Gecko   | Repo |
| Angelfish |   | 24.12.3 | Chromium | Flatpak |
| Epiphany |   | 47.3.1 | WebKit | Flatpak |


# Media Playback

Below is a table of different video codecs and their playback performance. 

### Player Information

| Player | Version | Method |
|--------|---------|--------|
| MPV    | 0.39.0  | Repo |
| Clapper | 0.6.1  | Flatpak |
| Livi | 0.3.1  | Flatpak |

### H.264/AVC

| Resolution | FPS | Player | Realtime Playback | Hardware Acceleration |
|------------|-----|--------|-------------------|-----------------------|
| 1080p      | 30  | MPV |  |  |
| 1080p      | 30  | Clapper |  |  |
| 1080p      | 30  | Livi |  |  |
| 720p       | 30  | MPV    |  |  |
| 720p       | 30  | Clapper |  |  |
| 720p       | 30  | Livi |  |  |

### H.265/HEVC

| Resolution | FPS | Player | Realtime Playback | Hardware Acceleration |
|------------|-----|--------|-------------------|-----------------------|
| 1080p      | 30  | MPV    |  |  |
| 1080p      | 30  | Clapper |  |  |
| 1080p      | 30  | Livi |  |  |
| 720p       | 30  | MPV    |  |  |
| 720p       | 30  | Clapper |  |  |
| 720p       | 30  | Livi |  |  |

### AV1

| Resolution | FPS | Player | Realtime Playback | Hardware Acceleration |
|------------|-----|--------|-------------------|-----------------------|
| 1080p      | 30  | MPV    |  |  |
| 1080p      | 30  | Clapper |  |  |
| 1080p      | 30  | Livi |  |  |
| 720p       | 30  | MPV    |  |  |
| 720p       | 30  | Clapper |  |  |
| 720p       | 30  | Livi | {{ img(src="/icons/exclamation.svg" alt="Maybe")}} |  |

### VP9

| Resolution | FPS | Player | Realtime Playback | Hardware Acceleration |
|------------|-----|--------|-------------------|-----------------------|
| 1080p      | 30  | MPV    |  |  |
| 1080p      | 30  | Clapper |  |  |
| 1080p      | 30  | Livi |  |  |
| 720p       | 30  | MPV    |  |  |
| 720p       | 30  | Clapper |  |  |
| 720p       | 30  | Livi |  |  |


{{ img(src="/icons/exclamation.svg" alt="Maybe")}} Close to real-time playback, few dropped frames in heavy scenes only


# Camera



| Temp   | Kelvin | Led   |
|--------|--------|-------|
| Normal | 5000k  | B35AM |
| Low    | 2500k  | 519A 3500K dedome  |

| Light | Description |
|-------|-------------|
| Medium | Convoy S21B 3rd click pointed at ceiling |
| Low    | Emisar DW4 Minimum brightness. Ceiling for superman. Direct from distance for color checker |

## Superman Normal Temp Medium Light

| FLX1 | Pixel 6| iPhone 12 |
|------|--------|-----------|
|  | {{ resize_image(path="/images/camera/pixel_6/pixel_6_superman_b35am_5000k_medium_light.jpg", width=360, alt="Pixel 6 Superman B35AM 5000k Medium Light") }} | {{ resize_image(path="/images/camera/iphone_12/iphone_12_superman_b35am_5000k_medium_light.png", width=360, alt="iPhone 12 Superman B35AM 5000k Medium Light") }} |

## Superman Low Temp Low Light

| FLX1 | Pixel 6 (6 sec) | iPhone 12 (3 sec) |
|------|-----------------|-------------------|
|  | {{ resize_image(path="/images/camera/pixel_6/pixel_6_superman_519a_2500k_low_light.jpg", width=360, alt="Pixel 6 Superman 519A 2500k Low Light") }} | {{ resize_image(path="/images/camera/iphone_12/iphone_12_superman_519a_2500k_low_light.png", width=360, alt="iPhone 12 Superman 519A 2500k Low Light") }} |

## Color Normal Temp Medium Light

| FLX1 | Pixel 6 | iPhone 12 |
|------|---------|-----------|
|  | {{ resize_image(path="/images/camera/pixel_6/pixel_6_colorchecker_b35am_5000k_medium_light.jpg", width=360, alt="Pixel 6 Color Checker B35AM 5000k Medium Light") }} | {{ resize_image(path="/images/camera/iphone_12/iphone_12_colorchecker_b35am_5000k_medium_light.png", width=360, alt="iPhone 12 Color Checker B35AM 5000k Medium Light") }} |

## Color Low Temp Low Light

| FLX1 | Pixel 6 | iPhone 12 (3 seconds) |
|------|---------------------|------------------------|
|  | {{ resize_image(path="/images/camera/pixel_6/pixel_6_colorchecker_519a_2500k_low_light.jpg", width=360, alt="Pixel 6 Color Checker 519A 2500k Low Light") }} | {{ resize_image(path="/images/camera/iphone_12/iphone_12_colorchecker_519a_2500k_low_light.png", width=360, alt="iPhone 12 Color Checker 519A 2500k Low Light") }} |


# Battery Life



Testing was done using the following settings:

- Screen brightness set to 50%
- Screen timeout disabled
- Measured from 100% battery to device shutdown except for standby
- Without android unless specified
- With sim unless specified

| Method | Battery Life |
|--------|--------------|
| Screen on |  |
| Screen on + Android |  |
| mpv 720p Video Playback |  |
| Stress cpu |  |
| Standby |  |
| Standby without sim |   |
| Standby + Android |  |


# Support




# Conclusion

