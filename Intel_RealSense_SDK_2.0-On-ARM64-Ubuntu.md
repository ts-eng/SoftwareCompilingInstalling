参考[NVIDIA Jetson installation](https://dev.intelrealsense.com/docs/nvidia-jetson-tx2-installation)和[libuvc_installation.sh](https://github.com/IntelRealSense/librealsense/blob/master/scripts/libuvc_installation.sh)
```
sudo apt-get update
sudo apt-get install aptitude
sudo aptitude install libssl-dev
sudo apt-get install git cmake libssl-dev freeglut3-dev libusb-1.0-0-dev pkg-config libgtk-3-dev unzip -y
cd librealsense-2.52.1
sudo cp config/99-realsense-libusb.rules /etc/udev/rules.d/
cd ..
sudo udevadm control --reload-rules && sudo udevadm trigger
mkdir build && cd build
cmake -DBUILD_EXAMPLES=true \
-DCMAKE_BUILD_TYPE=release \
-DFORCE_LIBUVC=true \
-DCMAKE_INSTALL_PREFIX=$(pwd)/../install \
../librealsense-2.52.1
make -j4
sudo make install
```
