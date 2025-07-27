## Kernel build for pi zero 2W.
### Cross-compile the 64 bit kernel

sudo apt install bc bison flex libssl-dev make libc6-dev libncurses5-dev  crossbuild-essential-arm64

``` bash
git clone --depth=1 --branch rpi-6.12.y_20241206_2 https://github.com/raspberrypi/linux   pi2W_krn_rpi-6.12.y_20241206_2
cd pi2W_krn_rpi-6.12.y_20241206_2

export KERNEL=kernel8
make ARCH=arm64 CROSS_COMPILE=aarch64-linux-gnu- bcm2711_defconfig
make ARCH=arm64 CROSS_COMPILE=aarch64-linux-gnu- Image modules dtbs

sudo env PATH=$PATH make -j12 ARCH=arm64 CROSS_COMPILE=aarch64-linux-gnu- INSTALL_MOD_PATH=mnt/root modules_install

```
