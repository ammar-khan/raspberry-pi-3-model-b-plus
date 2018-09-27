# Manage Users

How to Manage Users on Raspberry Pi 3 Model B+

---
#### Current User
---
```console
pi@raspberry:~ $ whoami
```

---
#### Switch to Another User
---
```console
pi@raspberry:~ $ sudo su - USER-NAME
password:
USER-NAME@raspberry:~ $ exit
pi@raspberry:~ $
```

---
#### Switch to Root User
---
```console
pi@raspberry:~ $ sudo su -
root@raspberry:~ $
```

---
#### Create New User
---
```console
pi@raspberry:~ $ sudo su -
root@raspberry:~ $ adduser NEW-USER-NAME
```

---
#### Add User to Super User Group
---
```console
pi@raspberry:~ $ sudo su -
root@raspberry:~ $ usermod -aG sudo USER-NAME
```

---
#### Delete User
---
```console
deluser –force –remove-home –remove-all-files USER-NAME
```

---
#### List All Users
---
```console
cd /home
ls
```
