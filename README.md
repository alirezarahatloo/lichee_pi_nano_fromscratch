# lichee_pi_nano

## U-BOOT

 1-git clone -b nano-v2018.01 --depth 1 https://github.com/Lichee-Pi/u-boot.git 
 
 2-source ./licheepi.sh 
 
 3-make licheepi_nano_defconfig
 
 4-cat /proc/partitions
 
 5-sudo fdisk -u=sectors /dev/sdx
 
 6-In fdisk:  "d" (Key in "d", hit enter. Do it repeatedly until all partitions deleted).
 
 7-In fdisk: "n", "p", "1" (Key in "n", enter, "p", enter, "1", enter)
When it asked for the first partition, type in 2048. Press enter, and enter again to select as default.
 8-In fdisk: "w" (Key in "w", hit enter)
 
 9-Yes! The 2048 blocks partition on sdd has been created for the u-boot to reside inside.
 
 10-Now you have the partitions created, the remaining blocks that is not occupied/reserved with the bootloader in the SD-card is created. Example here is   the sdd1:  

11-sudo mkfs.vfat /dev/sdd1

12-sudo dd if=u-boot-sunxi-with-spl.bin of=/dev/sdd bs=1024 seek=8

13-sync

## KERNEL
1-git clone -b nano-5.2-tf --depth 1 https://github.com/Lichee -Pi/linux.git

2-source ./licheepi.sh

3-make licheepi_nano_defconfig

4-copy zImge and dtb file to sd card


## boot.src

1-convert boot.cmd to boot.src with below command

$ mkimage -C none -A arm -T script -d boot.cmd boot.scr

2- copy boot.src to sd card

## busybox

git clone https://github.com/mirror/busybox.git

cd busybox

make defconfig

make menuconfig

star ----> settings -----> build static binary (no shared libs)

star ----> settings -----> Destination Path for 'make install'

export CROSS_COMPILE=

export PATH=

make 

make install 

copy bincsbin usr directory and linuxrc in sd card.

mkdir proc in  mmcblk0p1 

mkdir sys  in  mmcblk0p1

Put the SD in lichee pi nano and wait.

when you reach command line linux you must run below command:

1-mount -t proc  nodev /proc/

2-mount -t sysfs nodev /sys/

3-mount -o remount,rw / 

we can create /etc/init.d/rcS and add 1,2,3 and chmod +x rcS



