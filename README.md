# NVIDIA Jetson Nano Module With 16GB EMMC

Nvidia Jetson Nano/Xavier project Code

Hardware:
- [NVIDIA Jetson Nano Module (B01), Production-Ready AI System On Module (SOM), With 16GB EMMC](https://www.waveshare.com/jetson-nano-module.htm)
- [JETSON-IO-BASE-A - Carrier Board for Jetson Nano](https://www.waveshare.com/wiki/JETSON-NANO-DEV-KIT)
- [IMX219-83 Stereo Camera](https://www.waveshare.com/imx219-83-Stereo-camera.htm)

Software:
- [Nvidia SDK Manager on x86-64 Ubuntu OS](https://docs.nvidia.com/sdk-manager/install-with-sdkm-jetson/index.html)
- JetPack 4.6.0 flashed onto EMMC

System Installation:

- After flashing JetPack [expand storage](https://www.waveshare.com/wiki/JETSON-NANO-DEV-KIT#Boot_USB_Flash_Drive_.28copy_eMMC_on_the_system.29)

-  Never prompt the current user for a password when that user uses sudo:

        echo "$USER ALL=(ALL:ALL) NOPASSWD: ALL" | sudo tee "/etc/sudoers.d/dont-prompt-$USER-for-sudo-password"
        
        - Install Dependencies:

        sudo apt update -y && \

        sudo apt install nano python-pip python3-pip python3-venv python3-setuptools libgdm-dev libnss3-dev libssl-dev \
        libsqlite3-dev libreadline-dev libbz2-dev libdb-dev libdb++-dev libgdbm-dev libgdbm-dev libffi-dev -y
        
        sudo -H pip3 install -U jetson-stats

        sudo nvpmodel -m 0

        sudo jetson_clocks

- Build Python 3.8.3

        wget https://www.python.org/ftp/python/3.8.3/Python-3.8.3.tar.xz -O ~/Python-3.8.3.tar.xz && tar \
        -xvf ~/Python-3.8.3.tar.xz && mkdir build-python-3.8.3 && cd $_ \
        && ../Python-3.8.3/configure --enable-optimizations && make -j$(nproc) && sudo -H make altinstall
        
        sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.6 2 && \
        sudo update-alternatives --install /usr/bin/python3 python3 /usr/local/bin/python3.8 1
        
        
- [Build OpenCV-Contrib 4.5.3](https://github.com/Qengineering/Install-OpenCV-Jetson-Nano)
- https://github.com/mdegans/nano_build_opencv
    
        wget https://github.com/Qengineering/Install-OpenCV-Jetson-Nano/raw/main/OpenCV-4-5-3.sh \
        sudo chmod 755 ./OpenCV-4-5-3.sh && ./OpenCV-4-5-3.sh

       
- Create Python3.8 Virtual Environment

        /usr/local/bin/python3.8 -m venv ~/.py3.8.3
        echo "alias activate='source ~/.py3.8.3/bin/activate'" >> ~/.bashrc && source ~/.bashrc
        activate
        # Link Python3.6 cv2 module to Python3.8 site-packages
        ln -s /usr/lib/python3.6/dist-packages/cv2/python-3.6/cv2.cpython-36m-aarch64-linux-gnu.so \
        ~/.py3.8.3/lib/python3.8/site-packages/cv2.so
        # Install dependencies for opencv
        pip install --upgrade pip
        pip install -U numpy 
        # Install drivers for PTZ
        pip install adafruit-circuitpython-servokit
        
        
[Deploy object detection and classification with realtime vision DNN libraries using TensorRT. ](https://github.com/dusty-nv/jetson-inference)

[Setup VNC Server for remote headless operation.](https://computingforgeeks.com/how-to-install-vnc-server-on-ubuntu/)

[Fix Copy and Paste issues with Ubuntu and VNC Server.](https://superuser.com/questions/1081489/how-to-enable-text-copy-and-paste-for-vnc)


