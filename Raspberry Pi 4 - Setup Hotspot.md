# Raspberry Pi 4 - Setup Hotspot

Use the following link to configure the hotspot on the Pi **BUT** use the **hostapd.conf** configuration on this page.

 https://www.raspberrypi.org/documentation/configuration/wireless/access-point.md
 
 Saved a copy of the foregoing web page in the following PDF file: "Raspberry Pi 4 - Setup Hotspot.pdf"
 
### The following 5G Config for HOSTAPD works
#### For Raspberry Pi 4 (Raspbian Buster)
#### /etc/hostapd/hostapd.conf

```
ssid=YOUR_SSID
wpa_passphrase=YOUR_PASSPHRASE

country_code=US

interface=wlan0
driver=nl80211

wpa=2
wpa_key_mgmt=WPA-PSK
rsn_pairwise=CCMP

macaddr_acl=0

logger_syslog=0
logger_syslog_level=4
logger_stdout=-1
logger_stdout_level=0

hw_mode=a
wmm_enabled=1

# N
ieee80211n=1
require_ht=1
ht_capab=[MAX-AMSDU-3839][HT40+][SHORT-GI-20][SHORT-GI-40][DSSS_CCK-40]

# AC
ieee80211ac=1
require_vht=1
ieee80211d=0
ieee80211h=0
vht_capab=[MAX-AMSDU-3839][SHORT-GI-80]
vht_oper_chwidth=1
channel=36
vht_oper_centr_freq_seg0_idx=42
```
