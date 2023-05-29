# nvidia-jetson
Nvidia Jetson Nano/Xavier project Code

Hardware:
- NVIDIA Jetson Nano Module (B01), Production-Ready AI System On Module (SOM), With 16GB EMMC
- JETSON-IO-BASE-A - Carrier Board for Jetson Nano
- IMX219-83 Stereo Camera

Software:
- Nvidia SDK Manager on x86-64 Ubuntu OS
- JetPack 4.6.3 

System Installation:

After flashing EMMC with JetPack via SDK. Need to setup external storage to prevent running out of storage. Connect the USB flash drive to the Jetson Nano, check the device number of the USB flash drive, such as sda, open the Jetson Nano terminal and enter.

`ls /dev/sd*`

Format the USB flash drive.

`sudo mkfs.ext4 /dev/sda`

Modify the startup path.

`sudo vi /boot/extlinux/extlinux.conf`

Find the statement `APPEND ${cbootargs} quiet root=/dev/mmcblk0p1 rw rootwait rootfstype=ext4 console=ttyS0,115200n8 console=tty0`, modify mmcblk0p1 to sda.

Mount the USB flash drive.

`sudo mount /dev/sda /mnt`

Copy the system to the USB flash drive (the process has no information to print, please wait patiently).

`sudo cp -ax / /mnt`

After the copy is completed, uninstall the USB flash drive (not unplug the USB flash drive).

`sudo umount /mnt/`

Restart the system.

`sudo reboot`
