# nvidia-jetson
Nvidia Jetson Nano/Xavier project Code

Hardware:
- [NVIDIA Jetson Nano Module (B01), Production-Ready AI System On Module (SOM), With 16GB EMMC](https://www.waveshare.com/jetson-nano-module.htm)
- [JETSON-IO-BASE-A - Carrier Board for Jetson Nano](https://www.waveshare.com/wiki/JETSON-NANO-DEV-KIT)
- [IMX219-83 Stereo Camera](https://www.waveshare.com/imx219-83-Stereo-camera.htm)

Software:
- [Nvidia SDK Manager on x86-64 Ubuntu OS](https://docs.nvidia.com/sdk-manager/install-with-sdkm-jetson/index.html)
- JetPack 4.6.3 flashed onto EMMC

System Installation:

After flashing JetPack with SDK Manager, to [setup external storage](https://www.waveshare.com/wiki/JETSON-NANO-DEV-KIT#Boot_USB_Flash_Drive_.28copy_eMMC_on_the_system.29), connect the USB flash drive to the Jetson Nano, check the device number of the USB flash drive, such as sda, open the Jetson Nano terminal and ...

[Link to Waveshare wiki JETSON-NANO-DEV-KIT](https://www.waveshare.com/wiki/JETSON-NANO-DEV-KIT#USB_Flash_Drive_And_TF_Card_Booting_Principle)

Build Python3.8 on Jetson

`wget https://www.python.org/ftp/python/3.8.3/Python-3.8.3.tar.xz -O ~/Downloads/Python-3.8.3.tar.xz && 
tar -xvf ~/Downloads/Python-3.8.3.tar.xz -C ~/Downloads`

`mkdir build-python-3.8.3 && cd $_`

`../Python-3.8.3/configure --enable-optimizations`

`make -j$(nproc)`

`sudo -H make altinstall`

[Build OpenCV Contributor version 4.7.0](https://github.com/mdegans/nano_build_opencv)

[Deploy object detection and classification with realtime vision DNN libraries using TensorRT. ](https://github.com/dusty-nv/jetson-inference)

[Setup VNC Server for remote headless operation.](https://computingforgeeks.com/how-to-install-vnc-server-on-ubuntu/)

[Fix Copy and Paste issues with Ubuntu and VNC Server.](https://superuser.com/questions/1081489/how-to-enable-text-copy-and-paste-for-vnc)


