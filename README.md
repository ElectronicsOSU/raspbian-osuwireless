## How to connect a Raspberry Pi (3 or Zero W) running Raspbian to osuwireless

Disclaimer: I do not recommend using osuwireless for anything that requires extremely low latency or connecting to other devices on a local network. For example, if you're creating something like a Wi-Fi controlled toy car ([click here to see one that I made, perhaps it will inspire you](https://imgur.com/AfEjlAA)), consider using hostapd to create your own Wi-Fi network instead of connecting to a busy network such as osuwireless. To learn how to use hostapd, I recommend following this guide by Adafruit:

https://cdn-learn.adafruit.com/downloads/pdf/setting-up-a-raspberry-pi-as-a-wifi-access-point.pdf

If someone wants me to make an easier to follow guide for hostapd pester me and I'll do it... :P

### After reading the above, here's how you connect to osuwireless

Make a file named wpa_supplicant.conf on the root of the SD card's boot partition with the following content...

(replace name.# and something-secret with your OSU username and password, keep the quotes):


```
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

eapol_version=1
ap_scan=1
fast_reauth=1
network={
  ssid="osuwireless"
  scan_ssid=1
  key_mgmt=WPA-EAP
  eap=PEAP
  identity="name.#"
  password="something-secret"
  phase1="peaplabel=0"
  phase2="auth=MSCHAPV2"
}
```


#### If you're using a text editor like Notepad, don't forget to change the file extension from .txt to .conf when you save!

<p align="center">
<img src="https://raw.githubusercontent.com/ElectronicsOSU/raspbian-osuwireless/master/save_as_screenshot.png" width="25%" height="25%">
</p>


#### Screenshot on Windows (should look similar in macOS or whatever operating system you use)

<p align="center">
<img src="https://raw.githubusercontent.com/ElectronicsOSU/raspbian-osuwireless/master/screenshot.png" width="75%" height="75%">
</p>

## I hope you make something cool!

### Have questions? You can contact me at mitchell.1367{at}osu.edu



