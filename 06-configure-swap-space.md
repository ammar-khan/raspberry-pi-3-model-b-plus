# Configure Swap Space

## How to configure Swap Space on Raspberry Pi 3 Model B+

> _Note: Raspbian OS shipped with `100MB` swap space_

---
#### Increase Swap Space
---
```console
pi@raspberry:~ $ sudo nano /etc/dphys-swapfile
```
> _Look for `CONF_SWAPSIZE` and change it to `1024`_

```console
pi@raspberry:~ $ sudo /etc/init.d/dphys-swapfile stop
pi@raspberry:~ $ sudo /etc/init.d/dphys-swapfile start
pi@raspberry:~ $ free -m
```
---
#### Turn Off Swap Space
---
```console
pi@raspberry:~ $ sudo dphys-swapfile swapoff
```

---
#### Remove Swap Space Completely
---
```console
pi@raspberry:~ $ sudo dphys-swapfile swapoff
pi@raspberry:~ $ sudo dphys-swapfile uninstall
pi@raspberry:~ $ sudo update-rc.d dphys-swapfile remove
```
