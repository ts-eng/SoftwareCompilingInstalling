# libusb-1.0

```
cd libusb
tar xvf libusb-1.0.26.tar.gz
mkdir build && cd build
sh ../libusb-1.0.26/autogen.sh \
CC=aarch64-linux-gnu-gcc-9 \
CXX=aarch64-linux-gnu-g++-9 \
--prefix=$(pwd)/../install \
--host=x86_64 \
--target=aarch64
```
