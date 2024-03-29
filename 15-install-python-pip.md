# Install Python and PIP

## How to Install Python and PIP on Raspberry Pi 3 Model B+

#### 1 - Install Python and PIP
---
> _Note: Python2 and Python3 are pre installed on Raspbian OS_

> _Note: PIP and PIP3 are pre installed on Raspbian OS_

---
#### 2 - Verify Pre Installed Python
---
```console
pi@raspberry:~ $ sudo dpkg --get-selections | grep python3
```

---
#### 3 - Install PIP (Python Package Manager)
---

```console
pi@raspberry:~ $ sudo apt-get install -y python3-pip
```

---
#### 4 - Verify Installed PIP
---

```console
pi@raspberry:~ $ sudo pip3 list
```

---
#### 5 - Upgrade PIP
---

```console
pi@raspberry:~ $ sudo pip install --upgrade pip
pi@raspberry:~ $ sudo -H pip3 install --upgrade pip
pi@raspberry:~ $ sudo -H pip2 install --upgrade pip
pi@raspberry:~ $ sudo pip install --upgrade setuptools pip
pi@raspberry:~ $ sudo pip3 install --upgrade setuptools pip
```
 
---
#### 6 - Set Default Python
---
```
cd ~
nano .bashrc
```

At the bottom of that document, add the following lines:

Copy following lines

```
alias python=python3
alias pip=pip3
```

Run command

```
source .bashrc
```
