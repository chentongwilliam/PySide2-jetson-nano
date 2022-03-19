# PySide2-5.9-jetson-nano (easy way but old version)

see [PySide2InstallForJetson](https://github.com/hiroyuki-s1/PySide2InstallForJetson)
```bash
sudo apt-get install qt5-default
pip3 install PySide2-5.9.0a1-5.9.5-cp36-cp36m-linux_aarch64.whl
```



# PySide2-5.15.3-jetson-nano (new version but difficult)
OS: jetpack 4.6.1
PySide2: 5.15.3


## Install Qt5
see (https://forums.developer.nvidia.com/t/pyside2-qt-for-python-installation-on-jetson-xavier/160796/5)

(about 12 hours)
### Install xcb lib
```bash
sudo apt-get install '^libxcb.*-dev' libx11-xcb-dev libglu1-mesa-dev libxrender-dev libxi-dev libxkbcommon-dev libxkbcommon-x11-dev
```
### Download Qt Source
```bash
wget http://master.qt.io/archive/qt/5.15/5.15.3/single/qt-everywhere-src-5.15.3.tar.xz
```
### Configure and install Qt5 (here I used whole qt):
```bash
tar -xpf qt-everywhere-src-5.15.3.tar.xz
cd qt-everywhere-src-5.15.3/
```
(must enable xcb here manually)
```bash
./configure -xcb
```
Choose “o” to install Qt open source version.
```bash
make -j4
sudo make install
```
Now we have Qt5 under /usr/local/Qt-5.15.3


## Install PySide2
### Install PySide2 from whl
```bash
git clone https://github.com/chentongwilliam/PySide2-jetson-nano.git
pip3 install shiboken2-5.15.2.1-5.15.3-cp36-cp36m-linux_aarch64.whl
pip3 install shiboken2_generator-5.15.2.1-5.15.3-cp36-cp36m-linux_aarch64.whl
pip3 install PySide2-5.15.2.1-5.15.3-cp36-cp36m-linux_aarch64.whl
```
### Or Install PySide2 from Source
before install PySide2, first we have to deal with some requirements:
General requirements: Python: 3.5+, Qt: 5.12+, libclang: version10, CMake:3.1+, llvm: version10(clang10)

Here I personally suggest use synaptic to manage library:
```bash
sudo apt-get install synaptic
synaptic
```
Then install the correct version(10) of libclang and llvm via synaptic.

download and build PySide2:
```bash
git clone http://code.qt.io/pyside/pyside-setup.git
cd pyside-setup/
git checkout 5.15.3
```

Finally, to install PySide2:

```bash
sudo python3 setup.py install --qmake=/usr/local/Qt-5.15.2/bin/qmake
```

copy fonts
```bash
sudo mkdir /usr/local/Qt-5.15.3/lib/fonts
sudo chmod 777 /usr/local/Qt-5.15.3/lib/fonts
```
then copy all fonts you like (for example all fonts in /usr/share/fonts/truetype/ubuntu/) to /usr/local/Qt-5.15.3/lib/fonts

