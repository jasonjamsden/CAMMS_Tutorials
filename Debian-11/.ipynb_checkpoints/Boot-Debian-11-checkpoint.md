# Tutorial for Debian 11 Installation

![debian](images/debian.jpg "debian")


### 1. USB Format/Erase

It is critical to erase the usage and formal it appropriately before flashing the USB with the Debian 11 image:
- Format type: **ExFAT**.
- Scheme type: **GUID Partition Map**.

![debian format](images/debian-format.jpg "debian format")


### 2. Download Debian 11 Image

The **AMD** image is required for **intel** processors, which are the processors we have in the laboratory. Download this picture by clicking on the link below: 
- https://www.debian.org/distrib/netinst


### 3. Flash Image to USB

You may quickly flash the USB with the Debian 11 image using the balenaEtcher tool, which is available for Windows, Mac, and Ubuntu.

![debian flash](images/debian-flash.jpg "debian flash")


### 4. BIOS bootable USB 

Check that the PC on which you want to install Debian 11 has the USB as its primary boot option.

![debian bios](images/debian-bios.jpg "debian bios")


### 5. Installation 

Insert the USB and start the installation. 

Follow from now **step-by-step** on the guidelines provided in the following link:

https://www.linuxtechi.com/how-to-install-debian-11-bullseye/

