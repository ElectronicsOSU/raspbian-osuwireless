## How to connect a Raspberry Pi (3 or Zero W) running Raspbian to osuwireless

Make a file named wpa_supplicant.conf on the root of the SD card's boot partition with the following content (replace name.# and something-secret with your OSU username and password, keep the quotes).


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


#### Screenshot on Windows, should look similar in macOS or whatever operating system you use

<p align="center">
<img src="https://raw.githubusercontent.com/ElectronicsOSU/raspbian-osuwireless/master/screenshot.png" width="75%" height="75%">
</p>




