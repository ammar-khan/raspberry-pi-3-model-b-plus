# Setting Up Wi Fi

## How to setup wi-fi on Raspberry Pi 3 Model B+

#### Easy Setup (recommended):

- [Enable Wi-fi on your Raspberry Pi 3 Model B+](./01-getting-started.md)

---
#### Manual Setup
---
```console
pi@raspberry:~ $ sudo apt-get install wpasupplicant
pi@raspberry:~ $ sudo nano /etc/wpa_supplicant/wpa_supplicant.conf
```

> _Paste following lines_

```sh
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
country=AU

network={
        ssid="YOUR-WIFI-SSID"
        psk="YOUR-WIFI-PASSPHRASE"
	key_mgmt=WPA-PSK
}
```

`Ctrl+X` -> `Y` -> `Enter`
 
