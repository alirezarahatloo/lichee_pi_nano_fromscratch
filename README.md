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

## KEREL
1-git clone -b nano-5.2-tf --depth 1 https://github.com/Lichee -Pi/linux.git
2-source ./licheepi.sh
3-make licheepi_nano_defconfig
4-
