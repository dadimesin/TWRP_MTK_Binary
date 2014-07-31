Tutorial porting TWRP
=====================

- Make New folder as working folder, ex. /home/<username>/twrp/

mkdir /home/<username>/twrp/

- Syn & clone repository :

Binary
git clone https://github.com/dadimesin/TWRP_MTK_Binary.git

Porting tools (Bruno Martins Script)
git clone https://github.com/bgcngm/mtk-tools.git

- Pull recovery.img from device

command using terminal emulator :
dd if=/dev/recovery of=/mnt/sdcard/recovery

- Put recovery to working folder, ex. /home/<username>/twrp/

cd twrp

- Unpack recovery using the Bruno Martins Script

./unpack-MT65xx.pl recovery

- Compare partition in the 2500/etc/recovery.fstab with partition on your device

example :
system    /dev/block/mmcblk0p4   to be   /dev/block/mmcblk0p?
cache     /dev/block/mmcblk0p5   to be   /dev/block/mmcblk0p?
data      /dev/block/mmcblk0p6   to be   /dev/block/mmcblk0p?
emmc      /dev/block/mmcblk0p7   to be   /dev/block/mmcblk0p?

- Using gui from Teamwin if different resolutions

https://github.com/TeamWin/Team-Win-Recovery-Project/tree/jb-wip/gui/devices

- Repack recovery

./repack-MT65xx.pl -recovery recovery-kernel.img recovery-ramdisk recovery-twrp

- Move recovery-twrp to sdcard

- Push recovery-twrp

command using terminal emulator :
dd if=/mnt/sdcard/recovery-twrp of=/dev/recovery
