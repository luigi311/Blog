+++
title = "Furilabs FLX1"
description = "Information about the Furilabs FLX1, its features and limitations."
date = 2025-03-09
draft = false

[taxonomies]
tags = ["Phones", "Furilabs", "Halium", "Mobile Linux"]
[extra]
keywords = "Phones, Markdown, Furilabs, Halium, Mobile Linux"
toc = true
series = "Phones"
+++

- Performance: 4/5
- GPS and aGPS: GPS works well even without aGPS. aGPS can be enabled in the settings
- Affordability: Great price for the hardware and support provided
- Compatibility: 3/5
- Battery Life: 5/5

# Setup information
- OS: FuriOS 13.0.9
- Kernel: 4.19.325
- DE: Phosh

# Service

| Phone    | Service             | Technology | Speed | VoLTE/VoNR                                     |  
|----------|---------------------|------------|-------|------------------------------------------------|
| FLX1     | US Mobile (Tmobile) | 4G         |       | 
| Pixel 6a | US Mobile (Tmobile) | 5G         |       | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| FLX1     | US Mobile (Verizon) | 4G         |       |
| FLX1     | US Mobile (AT&T)    | 4G         |       |


# Performance

The FLX1 is a fast phone in general. The Mediatek Dimensity 900 is a fast SOC especially compared to the pinephone/pinephone pro/librem 5 devices. It comes with 6GB of RAM , which is more than enough for most tasks but can be limiting. Web browsing and media playback are fast and smooth. Android container is fully supported with acceleration working well and the performance is great. There are some acceleration issues with flatpak qt6 based applications. Flatpak qt5/gtk4 and native qt5/qt6/gtk4 are all accelerated without issues.


# Compatibility

The FLX1 is a halium based device so it is limiting to what OS/DE you can run on it. Currently FuriOS is the only supported OS, but there exists a WIP Ubuntu Touch port. You wont be able to run any of the other mainline OS though like arch and postmarketos. For desktop environments (DE) you are also limited to Phosh in FuriOS and Lomiri in the Ubuntu Touch port. GTK based applications seem to function the best while some QT based applications have issues such as acceleration and/or failing to launch like angelfish.


# Android

Android support is amazing with lots of sensors passed through to the container, listed below. While Waydroid was used a base, it has been heavily modified to improve the experience and has deviated massively from upstream waydroid so I will just adress it as Android Container. You should be able to run most android applications without any issues except the usually culprits like some bank applications. Video playback works and I can confirm Grayjay works perfectly except the volume control guesture. Android also integrated perfectly with the rest of the OS with all your android applications showing up in the app drawer. There is a gnome software plugin so you can search and install android apps through gnome software store as if it was a native application removing the need to open fdroid. There's a android section in the phosh settings that exposes a lot of android settings to the user as shown below.

{{ resize_image(path="/images/misc/furios/android_settings.png", width=480, alt="FuriOS Android Settings") }}

## Sensors passed to Android

| Sensor              | Passed through |
|---------------------|----------------|
| GPS                 | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Cameras             | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Microphone          | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Bluetooth           | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Modem               | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| NFC                 | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Fingerprint Sensor  | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Accelerometer       | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Geomagnetic         | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Orientation         | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Gyroscope           | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Light               | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Pressure            | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Proximity           | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Gravity             | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Linear Acceleration | {{ img(src="/icons/cross.svg" alt="No")}}      | 
| Rotation Vector     | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Step Counter        | {{ img(src="/icons/cross.svg" alt="No")}}      |


{{ img(src="/icons/exclamation.svg" alt="Maybe")}} Means currently WIP


# Docking

The FLX1 docking is in a weird position as the hardware does not support usb dp-alt mode but they are still able to utilize evdi to get video rendering externally. They are also wireless solution like what UT has with Miracast that can be implemented in the future.This is still not available yet though so only time will tell how well it works and how universal these options are.


# Web Browsing

Web browsing works really well. Firefox is a custom build that they maintain internal with improvements to performance and scaling to make it more mobile friendly. Due to it being a custom build it is possible for it to fall behind a few releases due to diffs in new releases but so far they are on top of it and the changes are amazing. Benchmarking results with [speedometer 3.0](https://browserbench.org/Speedometer3.0/) are below but I would recommend sticking with firefox. Angelfish does not launch at all.

| Browser   | Score               | Version | Toolkit  | Install |
|-----------|---------------------|---------|----------|---------|
| Firefox   | 2.77 &plusmn; 0.060 | 135.0.1 | Gecko    | Repo    |
| Angelfish | N/A                 | 24.12.3 | Chromium | Flatpak |
| Epiphany  | 1.46 &plusmn; 0.030 | 47.3.1  | WebKit   | Flatpak |


# Media Playback

Below is a table of different video codecs and their playback performance. Based on the results you should be using MPV as much as possible as it has the best performance and compatability. The hardware has support for decoding h264/h265/vp9 and they are working on adding in the software support necessary.

### Player Information

| Player  | Version | Method  |
|---------|---------|---------|
| MPV     | 0.39.0  | Repo    |
| Clapper | 0.6.1   | Flatpak |
| Livi    | 0.3.1   | Flatpak |

### H.264/AVC

| Resolution | FPS | Player  | Realtime Playback | Hardware Acceleration |
|------------|-----|---------|-------------------|-----------------------|
| 1080p      | 30  | MPV     | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 1080p      | 30  | Clapper | {{ img(src="/icons/cross.svg" alt="No")}}      | {{ img(src="/icons/cross.svg" alt="No")}} |
| 1080p      | 30  | Livi    | {{ img(src="/icons/cross.svg" alt="No")}}      | {{ img(src="/icons/cross.svg" alt="No")}} |
| 720p       | 30  | MPV     | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 720p       | 30  | Clapper | {{ img(src="/icons/cross.svg" alt="No")}}      | {{ img(src="/icons/cross.svg" alt="No")}} |
| 720p       | 30  | Livi    | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/cross.svg" alt="No")}} |

### H.265/HEVC

| Resolution | FPS | Player  | Realtime Playback | Hardware Acceleration |
|------------|-----|---------|-------------------|-----------------------|
| 1080p      | 30  | MPV     | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 1080p      | 30  | Clapper | {{ img(src="/icons/cross.svg" alt="No")}}      | {{ img(src="/icons/cross.svg" alt="No")}} |
| 1080p      | 30  | Livi    | {{ img(src="/icons/cross.svg" alt="No")}}      | {{ img(src="/icons/cross.svg" alt="No")}} |
| 720p       | 30  | MPV     | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 720p       | 30  | Clapper | {{ img(src="/icons/cross.svg" alt="No")}}      | {{ img(src="/icons/cross.svg" alt="No")}} |
| 720p       | 30  | Livi    | {{ img(src="/icons/cross.svg" alt="No")}}      | {{ img(src="/icons/cross.svg" alt="No")}} |

### AV1

| Resolution | FPS | Player  | Realtime Playback | Hardware Acceleration |
|------------|-----|---------|-------------------|-----------------------|
| 1080p      | 30  | MPV     | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 1080p      | 30  | Clapper | {{ img(src="/icons/cross.svg" alt="No")}}      | {{ img(src="/icons/cross.svg" alt="No")}} |
| 1080p      | 30  | Livi    | {{ img(src="/icons/cross.svg" alt="No")}}      | {{ img(src="/icons/cross.svg" alt="No")}} |
| 720p       | 30  | MPV     | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 720p       | 30  | Clapper | {{ img(src="/icons/cross.svg" alt="No")}}      | {{ img(src="/icons/cross.svg" alt="No")}} |
| 720p       | 30  | Livi    | {{ img(src="/icons/exclamation.svg" alt="Maybe")}} | {{ img(src="/icons/cross.svg" alt="No")}} |

### VP9

| Resolution | FPS | Player  | Realtime Playback | Hardware Acceleration |
|------------|-----|---------|-------------------|-----------------------|
| 1080p      | 30  | MPV     | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 1080p      | 30  | Clapper | {{ img(src="/icons/cross.svg" alt="No")}}      | {{ img(src="/icons/cross.svg" alt="No")}} |
| 1080p      | 30  | Livi    | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 720p       | 30  | MPV     | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 720p       | 30  | Clapper | {{ img(src="/icons/cross.svg" alt="No")}}      | {{ img(src="/icons/cross.svg" alt="No")}} |
| 720p       | 30  | Livi    | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/cross.svg" alt="No")}} |


{{ img(src="/icons/exclamation.svg" alt="Maybe")}} Close to real-time playback, few dropped frames in heavy scenes only


# Camera

The phone does not support libcamera and megapixels like mainline linux phones. Instead it has it's own camera stack and exposes the cameras out via v4l, gstreamer, qcamera and pipewire as of April 20, 2025 (update 13.0.9). This allows it to be used universally by other applications for video chatting such as through firefox. The camera quality is really good and the processing is instant as it's using the isp. The camera application also opens up almost instantly allowing you to quickly capture a moment. It is also capable of taking video with audio in sync. The phone has 3 camera sensors and all them are supported and exposed. There is no advance mode to manually control WB, ISO, codec, etc. It does have tap to adjust though and the auto focus/wb/iso works really well.

| Library    |  Supported                                     | 
|------------|------------------------------------------------|
| Libcamera  | {{ img(src="/icons/cross.svg" alt="No")}}      |
| Megapixels | {{ img(src="/icons/cross.svg" alt="No")}}      |
| v4l2       | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Gstreamer  | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Qcamera    | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |
| Pipewire   | {{ img(src="/icons/checkmark.svg" alt="Yes")}} |

## Example

| Temp   | Kelvin | Led   |
|--------|--------|-------|
| Normal | 5000k  | B35AM |
| Low    | 2500k  | 519A 3500K dedome  |

| Light  | Description |
|--------|-------------|
| Medium | Convoy S21B 3rd click pointed at ceiling |
| Low    | Emisar DW4 Minimum brightness. Ceiling for superman. Direct from distance for color checker |

## Superman Normal Temp Medium Light

| FLX1 | Pixel 6| iPhone 12 |
|------|--------|-----------|
| {{ resize_image(path="/images/camera/flx1/flx1_superman_b35am_5000k_medium_light.jpg", width=360, alt="FLX1 Superman B35AM 5000k Medium Light") }} | {{ resize_image(path="/images/camera/pixel_6/pixel_6_superman_b35am_5000k_medium_light.jpg", width=360, alt="Pixel 6 Superman B35AM 5000k Medium Light") }} | {{ resize_image(path="/images/camera/iphone_12/iphone_12_superman_b35am_5000k_medium_light.png", width=360, alt="iPhone 12 Superman B35AM 5000k Medium Light") }} |

## Superman Low Temp Low Light

| FLX1 | Pixel 6 (6 sec) | iPhone 12 (3 sec) |
|------|-----------------|-------------------|
| {{ resize_image(path="/images/camera/flx1/flx1_superman_519a_2500k_low_light.jpg", width=360, alt="FLX1 Superman 519A 2500k Low Light") }} | {{ resize_image(path="/images/camera/pixel_6/pixel_6_superman_519a_2500k_low_light.jpg", width=360, alt="Pixel 6 Superman 519A 2500k Low Light") }} | {{ resize_image(path="/images/camera/iphone_12/iphone_12_superman_519a_2500k_low_light.png", width=360, alt="iPhone 12 Superman 519A 2500k Low Light") }} |

## Color Normal Temp Medium Light

| FLX1 | Pixel 6 | iPhone 12 |
|------|---------|-----------|
| {{ resize_image(path="/images/camera/flx1/flx1_colorchecker_b35am_5000k_medium_light.jpg", width=360, alt="FLX1 Color Checker B35AM 5000k Medium Light") }} | {{ resize_image(path="/images/camera/pixel_6/pixel_6_colorchecker_b35am_5000k_medium_light.jpg", width=360, alt="Pixel 6 Color Checker B35AM 5000k Medium Light") }} | {{ resize_image(path="/images/camera/iphone_12/iphone_12_colorchecker_b35am_5000k_medium_light.png", width=360, alt="iPhone 12 Color Checker B35AM 5000k Medium Light") }} |

## Color Low Temp Low Light

| FLX1 | Pixel 6 | iPhone 12 (3 seconds) |
|------|---------------------|------------------------|
| {{ resize_image(path="/images/camera/flx1/flx1_colorchecker_519a_2500k_low_light.jpg", width=360, alt="FLX1 Color Checker 519A 2500k Low Light") }} | {{ resize_image(path="/images/camera/pixel_6/pixel_6_colorchecker_519a_2500k_low_light.jpg", width=360, alt="Pixel 6 Color Checker 519A 2500k Low Light") }} | {{ resize_image(path="/images/camera/iphone_12/iphone_12_colorchecker_519a_2500k_low_light.png", width=360, alt="iPhone 12 Color Checker 519A 2500k Low Light") }} |


# Battery Life

The phone has amazing battery life with the screen on and on standby. Standby is also different from the mainline devices as it does not use deep sleep. Instead it uses a low power mode that still allows network activity. This allows you to ssh in at anytime and continue to receive notifications from web based apps.

Testing was done using the following settings:

- Screen brightness set to 50%
- Screen timeout disabled
- Measured from 100% battery to device shutdown except for standby
- Without android unless specified
- With sim unless specified

| Method                  | Battery Life |
|-------------------------|--------------|
| Screen on               |    |
| Screen on + Android     |       |
| Screen on without sim   |    |
| mpv 720p Video Playback |    |
| Stress cpu              |  |
| Standby                 |     |
| Standby without sim     |  |
| Standby + Android       |     |


# Support

Support from FuriLabs has been outstanding. They are all constantly in the telegram group so when issues are discovered by endusers and they mention it in the chat they are able to immediately replicate it on their side so they can troubleshoot and fix it. They also have a great system to allow users to test fixes similar to Ubuntu Touch where there is a new repository for each fix that the user can install and uninstall. While UT requires the user to use the terminal to install said repository the FuriLabs folks have instead decided to create a GUI so even users that are terminal shy can test fixes. Overall getting ahold of them and getting software support from them is amazing but I have yet to interact with them when it comes to hardware defects so I can't comment on their warranty experience.


# Conclusion

This is a great device for the price, performance and support. It is constantly getting new improvements and updates are usually released monthly. The phone is great to use and the battery life is amazing. The camera is good and better than all mainline linux phones. The only downside is the lack of software support for other OSes and DEs but that is expected with a halium devices. The docking situation is a bummer but will hopefully improve in the future. Even with those caveats it is still a great device to use and I would 100% recommend it to anyone looking for a linux phone that is usable.
