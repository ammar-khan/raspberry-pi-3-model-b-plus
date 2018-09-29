# Install TensorFlow

## How to Install TensorFlow Library on Raspberry Pi 3 Model B+

> _Note: Raspbian is now [officially supported](https://www.tensorflow.org/install/) by TensorFlow community_

#### Prerequisite(s):
- [Enable Swap Space on your Raspberry Pi 3 Model B+](./06-configure-swap-space.md)
- [Install and Configure Python and PIP on your Raspberry Pi 3 Model B+](./15-install-python-pip.md)
- [Install and Configure Python Virtual Environment on your Raspberry Pi 3 Model B+](./16-install-python-virtual-environment.md)

---
#### 1 - Install TensorFlow Prerequisite
---
> _Note: as of 29/09/2018, TensorFlow community only provide wheel file for TensorFlow v1.9.0, which is built on Python3.4_

> _`https://www.piwheels.org/simple/tensorflow/tensorflow-1.9.0-cp34-none-linux_armv7l.whl`_

```console
pi@raspberry:~ $ sudo apt-get install -y python3.4
```
#### 2 - Create and Initialise Python Virtual Environment
---
```console
pi@raspberry:~ $ sudo mkvirtualenv tensorflow-env -p python3.4
pi@raspberry:~ $ sudo workon tensorflow-env
```

---
#### 3 - Install TensorFlow
---
```console
pi@raspberry:~ $ sudo workon tensorflow-env
(tensorflow-env)pi@raspberry:~ $ sudo apt install libatlas-base-dev
(tensorflow-env)pi@raspberry:~ $ sudo pip install --upgrade --ignore-installed tensorflow
```

---
#### 4 - Verify TensorFlow Working Correctly
---
```console
(tensorflow-env)pi@raspberry:~ $ python
```
```python
>>> import tensorflow
>>> tensorflow.__version__
'1.9.0'
>>>
```
`Ctrl+D`

---
#### Remove TensorFlow
---
```console
(tensorflow-env)pi@raspberry:~ $ sudo pip uninstall tensorflow
```
