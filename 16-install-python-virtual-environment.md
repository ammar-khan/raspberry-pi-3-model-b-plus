# Install Python Virtual Environment

## How to Install Python Virtual Environment on Raspberry Pi 3 Model B+

#### Prerequisite(s):
- [Install and Configure Python and PIP on your Raspberry Pi 3 Model B+](./15-install-python-pip.md)

#### 1 - Install Python Virtual Environement
---
```console
pi@raspberry:~ $ sudo wget https://bootstrap.pypa.io/get-pip.py
pi@raspberry:~ $ sudo python get-pip.py
pi@raspberry:~ $ sudo python3 get-pip.py
pi@raspberry:~ $ sudo pip install virtualenv virtualenvwrapper
pi@raspberry:~ $ sudo rm -rf ~/.cache/pip
```
---
#### 2 - Configure Python Virtual Environement
---
```console
pi@raspberry:~ $ sudo nano ~/.profile
```
> _Append following line_
```
# Python virtualenv and virtualenvwrapper
export WORKON_HOME=$HOME/.virtualenvs
export VIRTUALENVWRAPPER_PYTHON=/usr/bin/python3
source /usr/local/bin/virtualenvwrapper.sh
```
`Ctrl+X` -> `Y` -> `Enter`

---
#### 3 - Initialise Python Virtual Environement
---
```console
pi@raspberry:~ $ source ~/.profile
```

---
#### 4 - Create Python Virtual Environement
---
```console
pi@raspberry:~ $ sudo mkvirtualenv ENVIRONMENT-NAME
```
```console
pi@raspberry:~ $ sudo mkvirtualenv ENVIRONMENT-NAME -p python2 #With python2
```
```console
pi@raspberry:~ $ sudo mkvirtualenv ENVIRONMENT-NAME -p python3 #With python3
```

---
#### 5 - Load Python Virtual Environment
---
```console
pi@raspberry:~ $ sudo workon ENVIRONMENT-NAME
(ENVIRONMENT-NAME)pi@raspberry:~ $
```

---
#### Deactivate Python Virtual Environment
---
```console
(ENVIRONMENT-NAME)pi@raspberry:~ $ deactivate
pi@raspberry:~ $
```

---
#### Remove Python Virtual Environment
---
```console
pi@raspberry:~ $ sudo rmvirtualenv ENVIRONMENT-NAME
pi@raspberry:~ $ sudo rm -rf ENVIRONMENT-NAME/
```
 
