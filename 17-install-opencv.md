# Install OpenCV

## How to Install OpenCV on Raspberry Pi 3 Model B+

#### Prerequisite(s):
- [Enable Swap Space on your Raspberry Pi 3 Model B+](./06-configure-swap-space.md)
- [Install and Configure Python and PIP on your Raspberry Pi 3 Model B+](./15-install-python-pip.md)
- [Install and Configure Python Virtual Environment on your Raspberry Pi 3 Model B+](./16-install-python-virtual-environment.md)

#### Update
---
```console
pi@raspberry:~ $ sudo apt -y install libjpeg-dev \
	libtiff5-dev \
	libjasper-dev \
	libpng12-dev \
	libavcodec-dev \
	libavformat-dev \
	libswscale-dev \
	libv4l-dev \
	libxvidcore-dev \
	libx264-dev

pi@raspberry:~ $ sudo pip install opencv-python
pi@raspberry:~ $ sudo pip install opencv-contrib-python
```

> _Note: Go to Step 8 and you are done!_

---
#### 1 - Install OpenCV Prerequisite
---
```console
pi@raspberry:~ $ sudo apt-get update
pi@raspberry:~ $ sudo apt-get upgrade
pi@raspberry:~ $ sudo rpi-update

pi@raspberry:~ $ sudo reboot
```

```console
pi@raspberry:~ $ sudo apt-get install -y build-essential cmake pkg-config \
	ffmpeg \
	git \
	libjpeg-dev libtiff5-dev libjasper-dev libpng12-dev \
	libavcodec-dev libavformat-dev libswscale-dev libv4l-dev \
	libxvidcore-dev libx264-dev \
	libgtk2.0-dev libgtk-3-dev \
	libcanberra-gtk* \
	libatlas-base-dev gfortran \
	python2.7-dev python3-dev
  
pi@raspberry:~ $ sudo reboot
```

---
#### 2 - Download OpenCV
---
```console
pi@raspberry:~ $ cd ~
pi@raspberry:~ $ sudo wget -O opencv.zip https://github.com/opencv/opencv/archive/3.4.3.zip
pi@raspberry:~ $ sudo unzip opencv.zip
pi@raspberry:~ $ sudo rm -rf opencv.zip

pi@raspberry:~ $ sudo wget -O opencv_contrib.zip https://github.com/opencv/opencv_contrib/archive/3.4.3.zip
pi@raspberry:~ $ sudo unzip opencv_contrib.zip
pi@raspberry:~ $ sudo rm -rf opencv_contrib.zip

pi@raspberry:~ $ sudo reboot
```
```console
pi@raspberry:~ $ sudo pip3 install numpy
```

---
#### 3 - Create or Activate Python Virtual Environment
---
```console
pi@raspberry:~ $ sudo mkvirtualenv my-env -p python3
pi@raspberry:~ $ sudo workon my-env
```

---
#### 4 - Compile OpenCV
---
```console
(my-env) pi@raspberry:~ $ cd opencv-3.4.3
(my-env) pi@raspberry:~ $ sudo mkdir build
(my-env) pi@raspberry:~ $ cd build
(my-env) pi@raspberry:~ $ sudo cmake \
	-D CMAKE_BUILD_TYPE=RELEASE \
	-D CMAKE_INSTALL_PREFIX=/usr/local \
	-D OPENCV_EXTRA_MODULES_PATH=~/opencv_contrib-3.4.3/modules \
	-D BUILD_EXAMPLES=OFF \
	-D INSTALL_C_EXAMPLES=OFF \
	-D INSTALL_PYTHON_EXAMPLES=OFF \
	-D BUILD_NEW_PYTHON_SUPPORT=ON \
	-D ENABLE_NEON=ON \
	-D ENABLE_VFPV3=ON \
	-D BUILD_TESTS=OFF ..

(my-env) pi@raspberry:~ $ sudo reboot
```

---
#### 5 - Make OpenCV
---
```console
pi@raspberry:~ $ sudo workon my-env
(my-env) pi@raspberry:~ $ cd opencv-3.4.3/build
(my-env) pi@raspberry:~ $ sudo make -j4 #make with 4 threads - takes 2 hours min
```

---
#### 6 - Install OpenCV Make
---
```console
(my-env) pi@raspberry:~ $ sudo make install
(my-env) pi@raspberry:~ $ sudo ldconfig
```

---
#### 7 - Initialise OpenCV and Link in Virtual Environment
---
```console
(my-env) pi@raspberry:~ $ cd /usr/local/lib/python3.5/dist-packages/
(my-env) pi@raspberry:~ $ sudo cp cv2.cpython-35m-arm-linux-gnueabihf.so cv2.so  
(my-env) pi@raspberry:~ $ cd ~/.virtualenvs/my-env/lib/python3.5/site-packages/
(my-env) pi@raspberry:~ $ sudo ln -s /usr/local/lib/python3.5/dist-packages/cv2.so cv2.so #sym-link binding

(my-env)pi@raspberry:~ $ sudo pip install -U numpy
```

> _If above mentioned packages path does not exist then_

```console
(my-env) pi@raspberry:~ $ python
```
```python
>>> import sys
>>> site_packages = next(p for p in sys.path if 'site-packages' in p)
>>> print(site_packages)
'PRINT SITE PACKAGES PATH'
>>>
```
`Ctrl+D`
```console
(my-env) pi@raspberry:~ $ sudo reboot
```

---
#### 8 - Verify OpenCV Working Correctly
---
```console
pi@raspberry:~ $ workon my-env
(my-env) pi@raspberry:~ $ source ~/.profile
(my-env) pi@raspberry:~ $ python
```
```python
>>> import cv2
>>> cv2.__version__
'3.3.0'
>>>
```
`Ctrl+D`

---
#### Remove OpenCV
---

```console
(my-env) pi@raspberry:~ $ sudo apt-get remove -y ffmpeg
(my-env) pi@raspberry:~ $ sudo apt-get --purge remove libav-tools
(my-env) pi@raspberry:~ $ sudo apt-get --purge autoremove

(my-env) pi@raspberry:~ $ sudo pkg-config --modversion opencv
(my-env) pi@raspberry:~ $ sudo dpkg -l libopencv*
(my-env) pi@raspberry:~ $ sudo apt-get purge libopencv*
(my-env) pi@raspberry:~ $ sudo dpkg -r opencv
(my-env) pi@raspberry:~ $ sudo apt-get remove python-opencv

(my-env) pi@raspberry:~ $ cd opencv-3.4.3/build/
(my-env) pi@raspberry:~ $ sudo make uninstall
(my-env) pi@raspberry:~ $ sudo apt-get autoremove \
	opencv-doc \
	opencv-data \
	libopencv-dev \
	libopencv2.4-java \
	libopencv2.4-jni \
	python-opencv \
	libopencv-core2.4 \
	libopencv-gpu2.4 \
	libopencv-ts2.4 \
	libopencv-photo2.4 \
	libopencv-contrib2.4 \
	libopencv-imgproc2.4 \
	libopencv-superres2.4 \
	libopencv-stitching2.4 \
	libopencv-ocl2.4 \
	libopencv-legacy2.4 \
	libopencv-ml2.4 \
	libopencv-video2.4 \
	libopencv-videostab2.4 \
	libopencv-objdetect2.4 \
	libopencv-calib3d2.4 
(my-env) pi@raspberry:~ $ sudo dpkg --get-selections | grep -v deinstall | grep opencv
```
