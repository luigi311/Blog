+++
title = "Migrate to Mobile Linux Guide"
description = "Guide on how to migrate to mobile linux"
date = 2024-10-05
draft = false

[taxonomies]
tags = ["Mobile Linux", "Android", "IOS", "Guide"]
[extra]
keywords = "Mobile Linux, Android, IOS, Guide"
toc = true
series = "Mobile Linux"
+++

This is a guide on how to migrate from Android/IOS to Mobile Linux. Sections are broken down by Desktop Enviornment since that has an affect on what you have access to and what apps are expecting.

# Phosh / Gnome Mobile

## Contacts

App: [Contacts by The GNOME Project](https://flathub.org/apps/org.gnome.Contacts)

### Google / Nextcloud / WebDAV

##### UNTESTED #####

- Mobile Linux Phone
    1. Open Settings
    2. Tap on Online Accounts
    3. Tap on service provider and fill in information
    4. Open Contacts app and it should start populating

### Manual Import

- Mobile Linux Phone
    1. Open the Contacts app
    2. Tap the menu icon on the top right corner
    3. Tap on "Import From File..."
    4. Locate the contact vcf file you transfered and tap on it so its highlighted
    5. Tap on Import on the top right corner
    6. Tap on Import on the top right corner again
    7. All your contacts should be imported now


---


## Calendar

App: [Calendar by The GNOME Project](https://flathub.org/apps/org.gnome.Calendar)

### Google / Nextcloud / WebDAV

##### UNTESTED #####

- Mobile Linux Phone
    1. Open Settings
    2. Tap on Online Accounts
    3. Tap on service provider and fill in information
    4. Open the Calendar App and it should start populating the events


### Manual Import

- Mobile Linux Phone
    1. Open Calendar app
    2. Tap on the "Calendars" 
    3. Tap on "Manage Calendars..." from the drop down menu
    4. Tap on "Add Calendar..."
    5. Provide a name and color for your new calendar
    6. Tap on "Open a File"
    7. Tap on the transfered ics calendar file
    8. Tap on Open on the top right corner
    9. All your calendar events should be imported now


---


## Email

App: [Geary by Geary Development Team](https://flathub.org/apps/org.gnome.Geary)

### Google / Microsoft / IMAP / SMTP

- Mobile Linux Phone
    1. Open Settings
    2. Tap on Online Accounts
    3. Tap on service provider and fill in information
    4. Open Geary and it should detect your email account and start syncing

---

# Manual Exports

## Contacts

### Android

- Android Phone
    1. Open Contacts app
    2. Tap on Organize tab on the bottom right corner
    3. Scroll to the bottom and tap on "Export to file"
    4. Select a folder and name and tap on SAVE
    5. Transfer the new contacts vcf file to your mobile linux device

### IOS

- iPhone
    1. Open Contacts app
    2. Tap on Lists in the top left corner
    3. Press and Hold the group that you want
    4. Tap on Export in the popup menu
    5. Select the desired fields or tap "Select All Fields" at the bottom
    6. Tap on Done in the top right corner
    7. Save the contact card file somewhere
    8. Transfer the new contact vcf file to your mobile linux device


---


## Calendar

### Android

There is no way to export your local only calendar from the google calendar app. You will need to sync it to your google account so you can export it from the web calendar.

- Android Phone
    1. Sync your calendar with your google account

- Computer
    1. Open the website [https://calendar.google.com](https://calendar.google.com)
    2. Click the Settings gear icon on the top right corner
    3. Click on Settings
    4. Click on "Import & Export" on the left menu
    5. Click on the "Export" button
    6. Extract the Zip file that gets downloaded to your machine
    7. Transfer the ics calendar file that you just extracted to your mobile linux device


### IOS

##### UNTESTED #####

Like android there is no way to export the calendar out of an iPhone locally. I have no way to verify but I did find a workaround online by utilizing icloud. [Workaround discussion](https://discussions.apple.com/thread/8370609?sortBy=rank)

- iPhone
    1. Sync your calendar with your iCloud account

- Computer
    1. Open the website [https://www.icloud.com/](https://www.icloud.com/)
    2. Login to your iCloud account
    3. Click on the Calendar icon
    4. In the left panel click on Share Calendar button
    5. On the popup tick the "Public Calendar" option and copy the url
    6. Paste the url into the browser and change webcal to http in the url
    7. Rename the downloaded file to calendar.ics
    8. Transfer the new calendar.ics file to your mobile linux device
