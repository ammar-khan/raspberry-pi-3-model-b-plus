# Setting Up Docker

## How to setup Docker on Raspberry Pi 3 Model B+

#### Prerequisite(s):
```console
pi@raspberry:~ $ sudo apt-get install apt-transport-https ca-certificates software-properties-common -y
```

#### 1 - Configure Linux Configuration Group
---

```console
pi@raspberry:~ $ sudo nano /boot/cmdline.txt
```

> _Append following line_

```
cgroup_enable=memory cgroup_memory=1 cgroup_enable=cpuset swapaccount=1
```

`Ctrl+X` -> `Y` -> `Enter`

```console
pi@raspberry:~ $ sudo reboot
pi@raspberry:~ $ sudo cat /proc/cgroups
```

---
#### 2 - Install Docker
---

```console
pi@raspberry:~ $ sudo curl -fsSL get.docker.com -o get-docker.sh && sh get-docker.sh
```

---
#### 3 - Add User pi to docker User Group
---
```console
pi@raspberry:~ $ sudo usermod -aG docker pi
```

---
#### 4 - Import Docker PGP Key
---
```console
pi@raspberry:~ $ sudo curl https://download.docker.com/linux/raspbian/gpg
```

---
#### 5 - Setting up Docker Repository
---
```console
pi@raspberry:~ $ sudo nano /etc/apt/sources.list
```
> _Append following line_
```
deb https://download.docker.com/linux/raspbian/ stretch stable
```
`Ctrl+X` -> `Y` -> `Enter`

---
#### 6 - Apply Patch
---
```console
pi@raspberry:~ $ sudo apt-get update
pi@raspberry:~ $ sudo apt-get upgrade
```

---
#### 7 - Start Docker Service
---
```console
pi@raspberry:~ $ sudo systemctl start docker.service
```

---
#### 8 - Verify Docker Installation
---

```console
pi@raspberry:~ $ sudo docker info
```

---
#### Remove Docker
---
```console
pi@raspberry:~ $ sudo apt-get remove --auto-remove docker #Removes docker and dependencies
pi@raspberry:~ $ sudo apt-get purge docker-ce #For newer versions 
pi@raspberry:~ $ sudo dpkg -l | grep docker
pi@raspberry:~ $ sudo sudo dpkg --purge docker-ce
pi@raspberry:~ $ sudo sudo dpkg --purge docker-ce-cli
pi@raspberry:~ $ sudo rm -rf /var/lib/docker #Removes all data 
```
