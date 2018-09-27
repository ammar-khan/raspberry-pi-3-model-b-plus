# Setting Up Docker

## How to setup Docker on Raspberry Pi 3 Model B+

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
pi@raspberry:~ $ sudo curl -sSL get.docker.com | sh
```

---
#### 3 - Add User pi to docker User Group
---
```console
pi@raspberry:~ $ sudo usermod -aG docker pi
```

---
#### 4 - Verify Docker Installation
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
pi@raspberry:~ $ sudo rm -rf /var/lib/docker #Removes all data 
```
