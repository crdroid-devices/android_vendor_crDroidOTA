# crDroid OTA repo
In order for a device to be officially supported by crDroid, OTA information needs to be added.
Please refer to the following "Readme" to get started"

## 1. Introduction ##
In order for a device to be OTA compliant, there are a few things to know. 

### 1.1 XML structure ###
```
    <manufacturer id="Motorola">
        <Ocean>
            <maintainer>David Rondeau (Rondeau79)</maintainer>
            <devicename>Moto G7 Power</devicename>
            <filename>crDroid-9.0-20191125-ocean-v5.0</filename>
            <buildtype>Weekly</buildtype>
            <download><https://bit.ly/2KUoxVq</download>
            <changelog>https://raw.githubusercontent.com/crdroidandroid/android/</changelog>
            <gapps>https://opengapps.org</gapps>
            <forumhttps://forum.xda-developers.com/g7-power/development/rom-t4005739></forum>
            <firmware>FirmwareLink</firmware>
            <modem>ModemLink</modem>
            <bootloader>BootloaderLink</bootloader>
            <recovery>RecoveryLink</recovery>
            <paypal>PaypalLink</paypal>
            <telegram>TelegramLink</telegram>
        </Ocean>
    </Motorola>
```

### 1.2 Mandatory XML tags ###
* **Manufacturer** - Add under existing manufacturer (create manufacturer if required)
* **DeviceCode** - Device code name
* **MaintainerName** - Maintainer name followed by prefered name in parenthesis
* **DeviceName** - Device name (not code name)
* **FileName** - Latest crdroid build name (OTA code parses date to check for new version - don't include file extension .zip)
* **BuildType** - Nightly/Weekly/Final
* **DownloadLink** - Official download folder url (from AFH) masked by bit.ly shortlinks
* **ChangelogLink** - Changelog url (GitHub)
* **GappsLink** - Google apps url (preferred: opengapps url)
* **ForumLink** - Forum url for discussions and support (preferred: xda url)

*All mandatory XML tags need to be there. Please leave blank in case some do not apply to you.*

### 1.3 Optional XML tags ###
* **FirmwareLink** - link for needed firmware
* **ModemLink** - link for needed modem
* **BootloaderLink** - link for needed bootloader
* **RecoveryLink** - link for recommended recovery
* **PaypalLink** - paypal url (for donations)
* **TelegramLink** - telegram url (if you offer support via telegram - can be a group link or telegram.me link)

## 2 Guidelines ##
* Check if manufacturer is already existing
* Check if published link is official
* Check if XML is intact
* Check if no extra / missing spaces  

## 3. How to ##
### 3.1 Initial support ###
After you contacted [Gabriel on Telegram](https://telegram.me/gwolf2u), and have the approval, follow the below steps.
1. Fork this repo to your own GitHub 
2. Make proper changes accoring to the [XML structure](https://github.com/crdroidandroid/android_vendor_crDroidOTA/blob/9.0/README.md#xml-structure) 
3. Submit a pull request to this repo (this way we validate that you understood the requirements and if all is good you'll be granted direct push access to this repo)

### 3.2 Update build ###
1. Clone this repo locally
```
git clone https://github.com/crdroidandroid/android_vendor_crDroidOTA -b 9.0
```
Change to the directory where you cloned this repo (android_vendor_crDroidOTA) and fetch updates from repo.
```
cd android_vendor_crDroidOTA
git fetch --all
git pull
```
2. Open file named **update.xml** and make changes based on the [XML structure](https://github.com/crdroidandroid/android_vendor_crDroidOTA#xml-structure). You can also add your **changelog_<device_codename>.txt** file if you have it.
3. Now with the files updated, commit your update to this repo.
```
git add *
git commit #(this opens up your prefered text editor, so write a nice description like "<device codename>: update build")
git push #you may be prompted for your github username and password
```

## 4. Notice: ##  
Due to the fact the XML does not accept "&" in tags, there is a need to shortlink your download links
