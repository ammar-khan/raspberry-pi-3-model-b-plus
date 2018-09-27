# Configure Static IP

## How to configure Static IP on Raspberry Pi 3 Model B+

#### Prerequisite(s):
> _Note: write down IP addresses and names returned by following commands_
##### a) Raspberry Pi IP Address
```console
ip -4 addr show | grep global
```

##### b) Gateway IP Address
```console
pi@raspberry:~ $ sudo ip route | grep default | awk '{print $3}'
```

##### c) DNS IP Address
```console
pi@raspberry:~ $ sudo cat /etc/resolv.conf
```

##### d) Interfaces Name
```console
pi@raspberry:~ $ sudo ls /sys/class/net/
```

---
#### Configure Static IP Address
---
```console
pi@raspberry:~ $ sudo nano /etc/dhcpcd.conf
```

> _Change following lines_

```
eth0 
static ip_address = 192.168.1.100 / 24 
static routers = 192.168.1.1 
static domain_name_servers = 192.168.1.1 

wlan0 interface 
static ip_address = 192.168.1.100 / 24 
static routers = 192.168.1.1 
static domain_name_servers = 192.168.1.1
```

`Ctrl+X` -> `Y` -> `Enter`
