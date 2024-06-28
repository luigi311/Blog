+++
title = "Pine64 Pinephone"
description = "Information about the Pine64 Pinephone, its features and limitations."
date = 2024-06-22
draft = false

[taxonomies]
tags = ["Phones", "Pine64", "Downstream", "Mobile Linux"]
[extra]
toc = true
series = "Mobile Linux"
+++

- Performance: 1/5
- VoLTE Calls: Supported
- GPS and aGPS: Both work, but the antenna is weak, leading to potential delays in locking on or difficulties indoors
- Affordability: Designed to be super cheap, making it a good entry point for developers interested in mobile Linux
- Compatibility: Great
- Camera Support:
    * Libcamera: New support, handles everything in software as there is no ISP
    * Megapixels: Currently the better option, offering decent quality but slow processing due to the phone’s speed and the heavy processing required for raw images
- Battery Life: Decent, from 2-3.5 hours of active use and around multiple days on standby

# Performance

The Pinephone is slow. It uses an Allwinner A64 SOC, which is a quad-core Cortex-A53 processor. This SOC is very old and slow. It comes with 3GB of RAM, which is enough for most tasks. The performance is passable for basic tasks like calling, texting and other light applications but can struggle with heavy applications like web browsers and media playback that doesnt use hardware acceleration.

# Web Browsing

Web browsing is slow, and the phone can struggle especially with heavy websites. Performance is also affected by the browser used. Based on benchmarking results with [speedometer 3.0](https://browserbench.org/Speedometer3.0/) you should use either Epiphany or Angelfish for web browsing.

| Browser | Score | Toolkit |
|---------|-------|---------|
| Firefox | 0.372 &plusmn; 0.014   | Gecko   |
| Angelfish | 0.436 &plusmn; 0.0074 | Chromium |
| Epiphany | 0.451 &plusmn; 0.0065 | WebKit |

# Media Playback

Your best bet for media playback is to avoid doing it in the browser and instead downloading the video or audio file and playing it in a dedicated media player with hopefully hardware acceleration. The phone can struggle with high-resolution videos so keeping to 720p and lower is recommended and should be fine since the screen is only 720p anyway. 

Below is a table of different video codecs and their playback performance listing the highest resolution that can be played back in real-time per codecs, if the resolution is higher and not listed they all failed, if the resolution is lower then they all passed. Real-time playback means that the video can be played back without any dropped frames or stuttering. Hardware acceleration means that the video is being decoded by the GPU instead of the CPU, which can help with performance and battery life. 

Based on the table below if you are using h.264 you should use clapper or livi, for everything else you should use mpv.

### H.264/AVC

| Resolution | Player | Realtime Playback | Hardware Acceleration |
|------------|--------|-------------------|-----------------------|
| 1080p      | MPV    | {{ img(src="/icons/cross.svg" alt="No")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 1080p      | Clapper | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| 1080p      | Livi | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| 720p       | MPV    | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 720p       | Clapper | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| 720p       | Livi | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |

### H.265/HEVC

| Resolution | Player | Realtime Playback | Hardware Acceleration |
|------------|--------|-------------------|-----------------------|
| 576p       | MPV    | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 576p       | Clapper | {{ img(src="/icons/cross.svg" alt="No")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 576p       | Livi | {{ img(src="/icons/cross.svg" alt="No")}} | {{ img(src="/icons/cross.svg" alt="No")}} |

### AV1

| Resolution | Player | Realtime Playback | Hardware Acceleration |
|------------|--------|-------------------|-----------------------|
| 576p       | MPV    | {{ img(src="/icons/exclamation.svg" alt="Maybe")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 576p       | Clapper | {{ img(src="/icons/cross.svg" alt="No")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 576p       | Livi | {{ img(src="/icons/cross.svg" alt="No")}} | {{ img(src="/icons/cross.svg" alt="No")}} |

### VP9

| Resolution | Player | Realtime Playback | Hardware Acceleration |
|------------|--------|-------------------|-----------------------|
| 720p       | MPV    | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 720p       | Clapper | {{ img(src="/icons/cross.svg" alt="No")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 720p       | Livi | {{ img(src="/icons/cross.svg" alt="No")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 576p       | MPV    | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 576p       | Clapper | {{ img(src="/icons/cross.svg" alt="No")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 576p       | Livi | {{ img(src="/icons/cross.svg" alt="No")}} | {{ img(src="/icons/cross.svg" alt="No")}} |


{{ img(src="/icons/exclamation.svg" alt="Maybe")}} Close to real-time playback, few dropped frames in heavy scenes only


# Camera

There are two supported camera stacks that support the pinephone, libcamera and megapixels. Megapixels is the better option for now as it offers better quality and more features. The camera quality is decent but the processing is slow due to the phone's speed and the heavy processing required for raw images. The camera is not suitable for fast moving objects or low light conditions due to the slow processing and high noise levels. Its useful if you need to take a quick picture of something static.

### Libcamera 

Libcamera support has been added to the pinephone but it is not the best option as it handles everything in software as there is no ISP that it can use. It also currently lacks autofocus so it is not the best option for now.

Image pending for autofocus support


### Megapixels

Megapixels is the better option for now as it offers better quality and more features. The processing is slow due to the phone's speed and the heavy processing required for raw images. I have written a postprocessing script that can be used that will give slightly different results compared to postprocessd, you can find it [here](https://github.com/luigi311/megapixels_postprocess). It allows you to change processing settings and the final image codec to be used so you can get the best results for your use case such as avif or jxl.


#### Postprocessd

{{ img(src="/images/camera/pinephone/superman_postprocessd_stacked.jpg" alt="Superman Postprocessd") }}


#### Custom Postprocessing

{{ img(src="/images/camera/pinephone/superman_custom_processed.jpg" alt="Superman Custom") }}


# Battery Life

Testing was done using the following setup:

- Screen brightness set to 50%
- Screen timeout disabled
- Battery life was measured from 95% to device shutdown


| Method | Battery Life |
|--------|--------------|
| Screen on | 3.71 hours |
| Livi 720p Video Playback | 3.31 hours |
| mpv 720p Video Playback | 2.19 hours |
| stress cpu | 2.12 hours |

# Recommended

Only for using it as a base for mobile linux development. Its downstream kernel is well maintained and the software support is great but the hardware is slow and outdated. If you are just looking for a mobile linux device to use then you should take a look at the pinephone pro or even getting a used android device with mobile linux support.