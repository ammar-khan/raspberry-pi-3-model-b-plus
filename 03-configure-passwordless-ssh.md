# Configure Passwordless SSH

## How to connect to Raspberry Pi 3 Model B+ without password


#### Prerequisite(s):
- [Enable SSH on your Raspberry Pi 3 Model B+](./01-getting-started.md)
- [Understand how to connect to your Raspberry Pi 3 Model B+ using SSH](./02-configure-ssh.md)

> _Note: We are using word `USER-NAME` in following commands please change it with your operating system's user name_

---
#### 1 - Check for existing SSH keys
---

##### On Linux & Mac OS

```console
$ ls ~/.ssh
```

##### On Windows OS

```
C:\Users\USER-NAME\.ssh> dir
```

> _Note: If you see files named `id_rsa.pub` or `id_dsa.pub` you have keys set up already,
so you can skip the generating keys step (or delete these files with rm `id*` or `del id*` and make new keys)._

---
#### 2(a) - Use existing SSH Key (recommended if SSH key exist)
---
> To use existing pub key open id_rsa.pub or id_dsa.pub in editor and copy its contents.

##### On Linux & Mac OS

```console
$ nano ~/.ssh/id_rsa.pub
```

##### On Windows OS

```
C:\> Notepad "C:\Users\USER-NAME\.ssh\id_rsa.pub"
```
`Ctrl + A` -> `Ctrl + C`

---
#### 2(b) - Generate New SSH Key
---

##### On Linux & Mac OS

```console
$ ssh-keygen
```
> Note: _Upon entering this command, you'll be asked where to save the key.
We suggest you save it in the default location `/home/USER-NAME/.ssh/id_rsa` by just hitting Enter._

##### On Windows OS

```
C:\> ssh-keygen
```
> Note: _Upon entering this command, you'll be asked where to save the key.
We suggest you save it in the default location `C:\Users\USER-NAME\.ssh\id_rsa` by just hitting Enter._

---
#### 3 - Copy your public key to your Raspberry Pi
---

##### On Linux & Mac OS

```console
$ cat ~/.ssh/id_rsa.pub | ssh pi@192.168.1.111 'mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys'
```
Connect to Raspberry Pi using SSH without password
```console
$ ssh pi@192.168.1.111
```

##### On Windows OS

```
C:\> Notepad "C:\Users\USER-NAME\.ssh\id_rsa.pub"
```
Select All and Copy: `Ctrl + A` -> `Ctrl + C`

```
C:\> ssh pi@192.168.1.111
pi@192.168.1.111's password:
```
```console
pi@raspberry:~ $ mkdir .ssh
pi@raspberry:~ $ cd .ssh/
pi@raspberry:~ $ echo [PASTE-KEY-CONTENTS-HERE] >> authorized_keys
pi@raspberry:~ $ exit
```
Close Terminal and Open Again to connect to Raspberry Pi using SSH without password
```
C:\> ssh pi@192.168.1.111
```


