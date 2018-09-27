# Setting Up Docker Daemon

## How to setup Docker Daemon on Raspberry Pi 3 Model B+

#### Prerequisite(s):
- [Install and Configure Docker on your Raspberry Pi 3 Model B+](./11-setting-up-docker.md)

#### 1 - Initialise Docker Daemon
---

```console
pi@swarm-manager:~ $ sudo mkdir /etc/systemd/system/docker.service.d/
pi@swarm-manager:~ $ sudo cat /etc/systemd/system/docker.service.d/options.conf
[Service]
ExecStart=
ExecStart=/usr/bin/dockerd -H fd:// --bip 172.20.0.1/24 --dns 192.168.1.1 --dns ::1 --ipv6 --fixed-cidr-v6="192:168:1:101::/64"
```
---
#### 2 - Configuration(s)
---
> _To download only one file at a time during container build, default is 3_

```console
pi@swarm-manager:~ $ dockerd --max-concurrent-downloads 1
```
