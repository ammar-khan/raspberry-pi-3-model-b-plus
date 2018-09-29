# Install Dlib

## How to Install Dlib Library on Raspberry Pi 3 Model B+

#### Prerequisite(s):
- [Enable Swap Space on your Raspberry Pi 3 Model B+](./06-configure-swap-space.md)
- [Install and Configure Python and PIP on your Raspberry Pi 3 Model B+](./15-install-python-pip.md)
- [Install and Configure Python Virtual Environment on your Raspberry Pi 3 Model B+](./16-install-python-virtual-environment.md)

#### 1 - Create and Initialise Python Virtual Environment
---
```console
pi@raspberry:~ $ sudo mkvirtualenv my-env -p python3
pi@raspberry:~ $ sudo workon my-env
```

---
#### 2 - Install Dlib Prerequisite
---
```console
(my-env)pi@raspberry:~ $ sudo apt-get update
(my-env)pi@raspberry:~ $ sudo apt-get upgrade
(my-env)pi@raspberry:~ $ sudo apt-get install -y build-essential \
    cmake \
    gfortran \
    git \
    wget \
    curl \
    graphicsmagick \
    libgraphicsmagick1-dev \
    libatlas-dev \
    libavcodec-dev \
    libavformat-dev \
    libboost-all-dev \
    libgtk-3-dev \
    libjpeg-dev \
    liblapack-dev \
    libswscale-dev \
    pkg-config \
    python3-dev \
    python3-numpy \
    python3-pip \
    zip
    
(my-env)pi@raspberry:~ $ sudo apt-get clean
```

```console
(my-env)pi@raspberry:~ $ sudo pip3 install numpy
(my-env)pi@raspberry:~ $ sudo pip3 install scipy
(my-env)pi@raspberry:~ $ sudo pip3 install scikit-image

(my-env)pi@raspberry:~ $ sudo reboot
```

---
#### 3 - Install Dlib
---
```console
pi@raspberry:~ $ sudo workon my-env
(my-env)pi@raspberry:~ $ sudo git clone https://github.com/davisking/dlib.git
(my-env)pi@raspberry:~ $ cd dlib
(my-env)pi@raspberry:~ $ sudo python3 setup.py install --clean --compiler-flags "-mfpu=neon"
(my-env)pi@raspberry:~ $ sudo pip install dlib

(my-env)pi@raspberry:~ $ sudo pip3 install face_recognition #OPTIONAL
```

---
#### 4 - Verify Dlib Working Correctly
---
```console
(my-env)pi@raspberry:~ $ python
```
```python
>>> import dlib
>>> dlib.__version__
'19.5.1'
>>>
```
`Ctrl+D`
