lpGBT install
=============

```
sudo yum install doxygen
sudo yum install libusb-devel
sudo yum install libconfuse-dev (for ftdi-eeprom)
sudo yum install swig python-dev (for python bindings)
sudo yum install libboost-all-dev (for C++ binding and unit test)
sudo yum install build-essential python-pip python-smbus
```

## Clone the git repository
```
mkdir libftdi
cd libftdi
git clone git://developer.intra2net.com/libftdi
```

If you are building the release tar ball, just extract the source tar ball.

## Build the git source and install
```
cd libftdi
mkdir build
cd build
cmake -DCMAKE_INSTALL_PREFIX="/usr/" -DPYTHON_INCLUDE_DIR="/usr/include/python2.7" -DPYTHON_LIBRARIES="/usr/lib/python2.7/" ../ 
make
sudo make install
```

## Install this library
```
git clone --single-branch --branch lpGBT https://github.com/swertz/Adafruit_Python_GPIO.git
cd Adafruit_Python_GPIO
sudo python setup.py install
```

## Add udev rule and add yourself to group
```
sudo echo SUBSYSTEM=="usb", ATTR{idProduct}=="6014", ATTR{idVendor}=="0403", MODE:="06660", GROUP:="dialout" > /etc/udev/rules.d/52-xilinx-ftdi-usb.rules
sudo usermod -a -G dialout $USER
```


!!!Deprecation Warning!!!
===================
This library has been deprecated in favor of [our python3 Blinka library](https://github.com/adafruit/Adafruit_Blinka). We have replaced all of the libraries that use this repo with CircuitPython libraries that are Python3 compatible, and support a [wide variety of single board/linux computers](https://circuitpython.org/blinka)!

Visit https://circuitpython.org/blinka for more information

CircuitPython has [support for almost 200 different drivers](https://circuitpython.readthedocs.io/projects/bundle/en/latest/drivers.html), and a  as well as [FT232H support for Mac/Win/Linux](https://learn.adafruit.com/circuitpython-on-any-computer-with-ft232h)!

!!!Deprecation Warning!!!
===================

Adafruit Python GPIO Library
============================

Library to provide a cross-platform GPIO interface on the Raspberry Pi and Beaglebone Black using the [RPi.GPIO](https://pypi.python.org/pypi/RPi.GPIO) and [Adafruit_BBIO](https://pypi.python.org/pypi/Adafruit_BBIO) libraries.

The library is currently in an early stage, but you can see how its used in the [Adafruit Nokia LCD library](https://github.com/adafruit/Adafruit_Nokia_LCD) to write Python code that is easily portable between the Raspberry Pi and Beaglebone Black.

Note that you typically don't need to install this library directly as other libraries will depend on it in their setup and automatically install it.  However if you do need to manually install do so by running these commands:

- On a Debian-based Linux like Raspbian, Ubuntu, etc. in a terminal execute:
  
  ```
  sudo apt-get update
  sudo apt-get install build-essential python-pip python-dev python-smbus git
  git clone https://github.com/adafruit/Adafruit_Python_GPIO.git
  cd Adafruit_Python_GPIO
  sudo python setup.py install
  ```

- On Mac OSX, first install PIP by [downloading the python script here](https://bootstrap.pypa.io/get-pip.py) and execute it with `python get-pip.py` in a terminal, then install the [git source control system](http://git-scm.com/downloads).  Then in a terminal execute:
  
  ```
  git clone https://github.com/adafruit/Adafruit_Python_GPIO.git
  cd Adafruit_Python_GPIO
  sudo python setup.py install
  ```

- On Windows, first install the [latest Python 2.7 version](https://www.python.org/downloads/windows/), then install PIP by [downloading the python script here](https://bootstrap.pypa.io/get-pip.py) and execute it with `python get-pip.py` in a terminal, and finally install the [git source control system](http://git-scm.com/downloads).  Then in a git bash prompt execute:
  
  ```
  git clone https://github.com/adafruit/Adafruit_Python_GPIO.git
  cd Adafruit_Python_GPIO
  python setup.py install
  ```

Contributing
------------

For information on contributing, such as how to run tests, etc. please see the [project wiki](https://github.com/adafruit/Adafruit_Python_GPIO/wiki/Running-Tests) on GitHub.
