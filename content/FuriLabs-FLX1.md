+++
title = "Furilabs FLX1"
description = "Information about the Furilabs FLX1, its features and limitations."
date = 2024-09-06
draft = true

[taxonomies]
tags = ["Phones", "Furilabs", "Halium"]
[extra]
keywords = "Phones, Markdown, Furilabs, Halium"
toc = true
series = "Phones"
+++

- Performance: 4/5
- VoLTE Calls: Supported
- GPS and aGPS: GPS works well even without aGPS. aGPS can be enabled in the settings
- Affordability: Great price for the hardware and support provided
- Compatibility: 3/5
- Camera Support:
    * Libcamera: Not supported
    * Megapixels: Not supported
    * v4l2: Supported
- Battery Life: 5/5

# Setup information
- OS: FuriOS 13.0.3
- Kerenl: 4.19.191
- DE: Phosh

# Performance

The FLX1 is a fast phone in general. The Mediatek Dimensity 900 is a fast SOC especially compared to the pinephone/pinephone pro/librem 5 devices. It comes with 6GB of RAM , which is more than enough for most tasks but can be limiting. Web browsing and media playback are fast and smooth. Android container is fully supported so acceleration works well and the performance is great. There are some acceleration issues with flatpak qt6 based applications, so they are set to software rendering. Flatpak qt5/gtk4 and native qt5/qt6/gtk4 are all accelerated without issues.

# Compatibility

The FLX1 is a halium based device so it is limiting to what OS/DE you can run on it. Currently FuriOS is the only supported OS, but someone can create a port for UT. You wont be able to run any of the other mainline OS though like arch and postmarketos. For desktop environments (DE) you are also limited to Phosh and Lomiri. Plasma mobile has a fork that someone was able to get it working on droidian devices but it is not officially supported.

Android support is amazing with lots of sensors passed through to the container. You should be able to run most android applications but video playback is currently broken. Android also integrated perfectly with the rest of the OS. All your android applications show up in the app drawer while android is running. Theres a android section in the phosh settings that exposes a lot of android settings to the user. 

{{ resize_image(path="/images/misc/furios/android_settings.png", width=480, alt="FuriOS Android Settings") }}

# Docking

The FLX1 isn't currently able to output video via the usb c port due to the lack of hardware support. They are currently working on a wireless solution like what UT has with Miracast. This would limit you to only using Miracast compatible devices such as the Nexdock Wireless or using a Miracast dongle. This is still not available yet though so only time will tell how well it works.

# Web Browsing

Web browsing works really well and I haven't ran into any issues with firefox yet. Firefox is a custom build that they maintain internal with improvements to performance and scaling to make it more mobile friendly. Due to it being a custom build it is possible for it to fall behind a few releases due to issues in new releases but so far they are on top of it and the changes are amazing. Based on benchmarking results with [speedometer 3.0](https://browserbench.org/Speedometer3.0/) either firefox or epiphany work but I would recommend firefox. Angelfish doesn't work at all.

| Browser | Score | Version | Toolkit | Method |
|---------|-------|---------|---------|--------|
| Firefox | 2.28 &plusmn; 0.17 | 128.0.3 | Gecko   | Repo |
| Angelfish | N/A | 24.08.0 | Chromium | Flatpak |
| Epiphany | 2.12 &plusmn; 0.054 | 46.3 | WebKit | Flatpak |

# Media Playback

Below is a table of different video codecs and their playback performance. Based on the results you should be using MPV as much as possible as it has the best performance and compatability. The hardware has support for decoding h264/h265/vp9 and they are working on adding in the software support necessary.

### Player Information

| Player | Version | Method |
|--------|---------|--------|
| MPV    | 0.38.0  | Repo |
| Clapper | 0.6.1  | Flatpak |
| Livi | 0.2.0  | Flatpak |

### H.264/AVC

| Resolution | FPS | Player | Realtime Playback | Hardware Acceleration |
|------------|-----|--------|-------------------|-----------------------|
| 1080p      | 30  | MPV | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 1080p      | 30  | Clapper | {{ img(src="/icons/cross.svg" alt="No")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 1080p      | 30  | Livi | {{ img(src="/icons/cross.svg" alt="No")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 720p       | 30  | MPV    | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 720p       | 30  | Clapper | {{ img(src="/icons/cross.svg" alt="No")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 720p       | 30  | Livi | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/cross.svg" alt="No")}} |

### H.265/HEVC

| Resolution | FPS | Player | Realtime Playback | Hardware Acceleration |
|------------|-----|--------|-------------------|-----------------------|
| 1080p      | 30  | MPV    | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 1080p      | 30  | Clapper | {{ img(src="/icons/cross.svg" alt="No")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 1080p      | 30  | Livi | {{ img(src="/icons/cross.svg" alt="No")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 720p       | 30  | MPV    | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 720p       | 30  | Clapper | {{ img(src="/icons/cross.svg" alt="No")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 720p       | 30  | Livi | {{ img(src="/icons/cross.svg" alt="No")}} | {{ img(src="/icons/cross.svg" alt="No")}} |

### AV1

| Resolution | FPS | Player | Realtime Playback | Hardware Acceleration |
|------------|-----|--------|-------------------|-----------------------|
| 1080p      | 30  | MPV    | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 1080p      | 30  | Clapper | {{ img(src="/icons/cross.svg" alt="No")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 1080p      | 30  | Livi | {{ img(src="/icons/cross.svg" alt="No")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 720p       | 30  | MPV    | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 720p       | 30  | Clapper | {{ img(src="/icons/cross.svg" alt="No")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 720p       | 30  | Livi | {{ img(src="/icons/exclamation.svg" alt="Maybe")}} | {{ img(src="/icons/cross.svg" alt="No")}} |

### VP9

| Resolution | FPS | Player | Realtime Playback | Hardware Acceleration |
|------------|-----|--------|-------------------|-----------------------|
| 1080p      | 30  | MPV    | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 1080p      | 30  | Clapper | {{ img(src="/icons/cross.svg" alt="No")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 1080p      | 30  | Livi | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 720p       | 30  | MPV    | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 720p       | 30  | Clapper | {{ img(src="/icons/cross.svg" alt="No")}} | {{ img(src="/icons/cross.svg" alt="No")}} |
| 720p       | 30  | Livi | {{ img(src="/icons/checkmark.svg" alt="Yes")}} | {{ img(src="/icons/cross.svg" alt="No")}} |


{{ img(src="/icons/exclamation.svg" alt="Maybe")}} Close to real-time playback, few dropped frames in heavy scenes only


# Camera

The phone does not support libcamera or megapixels like other linux phones. Instead it has it's own camera stack that exposes the camera as a v4l2 device. This allows it to be used by other applications for video chatting such as through firefox. The camera quality is really good and the processing is instant. The camera application also opens up instantly allowing you to quickly capture a moment. It is also capable of taking video with audio in sync. The phone has 3 camera sensors and all them are supported and exposed. There is no advance mode to manually control WB, ISO, codec, etc. It does have tap to adjust though and the auto focus/wb/iso works really well. Work is still being done to improve the camera quality and the camera application just went through a major rewrite/redesign.

| Temperature | Kelvin | Led   |
|-------------|--------|-------|
| High        | 5000k  | B35AM |
| Low         | 2500k  | 519A  |

## Superman High Temperature High Light

## Superman High Temperature Low Light

## Superman Low Temperature High Light

| FLX1 | Pixel 6|
|------|--------|
| {{ resize_image(path="/images/camera/flx1/superman_519a_2500k_high_light.jpg", width=480, alt="FLX1 Superman 519A Dedommed 2500k High Light") }} | {{ resize_image(path="/images/camera/pixel_6/superman_519a_2500k_high_light.jpg", width=480, alt="Pixel 6 Superman 519A Dedommed 2500k High Light") }} |

## Superman Low Temperature Low Light

| FLX1 | Pixel 6|
|------|--------|
| {{ resize_image(path="/images/camera/flx1/superman_519a_2500k_low_light.jpg", width=480, alt="FLX1 Superman 519A Dedommed 2500k Low Light") }} | {{ resize_image(path="/images/camera/pixel_6/superman_519a_2500k_low_light.jpg", width=480, alt="Pixel 6 Superman 519A Dedommed 2500k Low Light") }} |

## Colorchecker High Temperature High Light
FLX1

Pixel 6

## Colorchecker High Temperature Low Light
FLX1

Pixel 6

## Colorchecker Low Temperature High Light

| FLX1 | Pixel 6|
|------|--------|
| {{ resize_image(path="/images/camera/flx1/colorchecker_519a_2500k_high_light.jpg", width=480, alt="FLX1 Colorchecker 519A Dedommed 2500k High Light") }} | {{ resize_image(path="/images/camera/pixel_6/colorchecker_519a_2500k_high_light.jpg", width=480, alt="Pixel 6 Colorchecker 519A Dedommed 2500k High Light") }} |

## Colorchecker Low Temperature Low Light

| FLX1 | Pixel 6|
|------|--------|
| {{ resize_image(path="/images/camera/flx1/colorchecker_519a_2500k_low_light.jpg", width=480, alt="FLX1 Colorchecker 519A Dedommed 2500k Low Light") }} | {{ resize_image(path="/images/camera/pixel_6/colorchecker_519a_2500k_low_light.jpg", width=480, alt="Pixel 6 Colorchecker 519A Dedommed 2500k Low Light") }} |

# Battery Life

The phone has great battery life with the screen on and on standby. Standby is also different from the mainline devices as it does not use deep sleep. Instead it uses a low power mode that still allow network activity. This allows you to ssh in at anytime and continue to receive notifications from web based apps.

Testing was done using the following settings:

- Screen brightness set to 50%
- Screen timeout disabled
- Measured from 100% battery to device shutdown
- With and without android running in the background

| Method | Battery Life |
|--------|--------------|
| Screen on | |
| Screen on + Android | 10 hours | 
| Livi 720p Video Playback | |
| mpv 720p Video Playback | |
| Stress cpu | |
| Stress cpu + Android | 5.38 hours |
| Standby | |
| Standby + Android |  |

# Conclusion

This is a great device for the price, performance and support. It is constantly getting new improvements and updates are usually released monthly. The phone is great to use and the battery life is amazing. The camera is good enough and better than the mainline linux devices. The only downside is the lack of support for other OSes and DEs but that is expected with a halium devices. The docking situation is a bummer but will hopefully improve in the future. Even with those caveats it is still a great device to use and I would recommend it to anyone looking for a linux phone.