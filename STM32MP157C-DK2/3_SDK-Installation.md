# Install the SDK for the STM32MP15x

This stage explains how to install the SDK. The SDK for OpenSTLinux distribution provides a standalone cross-development toolchain and libraries tailored to the contents of the specific image flashed onto the board.

# Step 1-a: Host computer package installation
`$> sudo apt-get update` 

`$> sudo apt-get install gawk wget git diffstat unzip texinfo gcc build-essential chrpath socat cpio python3 python3-pip python3-pexpect xz-utils debianutils iputils-ping python3-git python3-jinja2 libegl1-mesa libsdl1.2-dev pylint3 xterm python3-subunit mesa-common-dev zstd liblz4-tool`  

`$> sudo apt-get install make xsltproc docbook-utils fop dblatex xmlto`  

`$> sudo apt-get install libmpc-dev libgmp-dev`  

`$> sudo apt-get install build-essential libncurses-dev libyaml-dev libssl-dev`  

# Step 1-b: Set python3 as the default python

`$> sudo apt install python-is-python3`

# Step 1-c: Install at host computer repo package

`$> export REPO=$(mktemp /tmp/repo.XXXXXXXXX)`  

`$> curl -o ${REPO} https://storage.googleapis.com/git-repo-downloads/repo`  

`$> gpg --recv-key 8BB9AD793E8E6153AF0F9A4416530D5E920F5C65`  

`$> gpg --edit-key 8BB9AD793E8E6153AF0F9A4416530D5E920F5C65`

`gpg> trust`

`Your decision> 5` and `Your decision> y`

Exit gpg: `Ctrl C`  

`$> curl -s https://storage.googleapis.com/git-repo-downloads/repo.asc | gpg --verify - ${REPO} && sudo install -m 755 ${REPO} /bin/repo`

Check if repo is installed:  

`$> repo version`

Expect a report similar to this one:

`<repo not installed>
repo launcher version 2.15
(from /bin/repo)`

`$> sudo apt-get update`

- Based on: https://source.android.com/docs/setup/download#installing-repo  

# Step 1-d - Useful tools:

`$> sudo apt-get install coreutils bsdmainutils sed curl bc lrzsz corkscrew cvs subversion mercurial nfs-common nfs-kernel-server libarchive-zip-perl dos2unix texi2html diffstat libxml2-utils`

Additional configurations:
Additional configurations have to be installed to support up to 16 partitions per MMC. By default, on Linux® systems, a maximum of 8 partitions are allowed on MMC. All Packages (Starter Package, ...) need more than 10 partitions for the storage device. In order to extend the number of partitions per device to 16, the following options must be added to modprobe:

`$> sudo mv /tmp/mmc_block.conf /etc/modprobe.d/mmc_block.conf`

`$> sudo mv /tmp/mmc_block.conf /etc/modprobe.d/mmc_block.conf`


# Step 2 - Download the SDK

Download SDK: https://www.st.com/en/embedded-software/stm32mp1dev.html

Create to your home directory a directory: STM32MPU_workspace/tmp

Move the SDK you dowloaded to this STM32MPU_workspace/tmp directory

And go to this directory and extract the tar.xz file you downloaded:

`$> tar xvf SDK-x86_64-stm32mp1-openstlinux-5.15-yocto-kirkstone-mp1-v22.06.15.tar.xz`  

Create your STM32MP1 Developer Package SDK directory on your host computer:

`$> mkdir -p ~/STM32MPU_workspace/STM32MP1-Ecosystem-v4.0.0/Developer-Package/SDK`

Change the permissions of the SDK installation script so that it is executable:

`$> chmod +x ~/STM32MPU_workspace/tmp/stm32mp1-openstlinux-5.15-yocto-kirkstone-mp1-v22.06.15/sdk/st-image-weston-openstlinux-weston-stm32mp1-x86_64-toolchain-4.0.1-openstlinux-5.15-yocto-kirkstone-mp1-v22.06.15.sh`

Execute the SDK installation script:

`$> cd ~/STM32MPU_workspace/tmp/stm32mp1-openstlinux-5.15-yocto-kirkstone-mp1-v22.06.15/sdk/`

`$> ./st-image-weston-openstlinux-weston-stm32mp1-x86_64-toolchain-4.0.1-openstlinux-5.15-yocto-kirkstone-mp1-v22.06.15.sh -d ~/STM32MPU_workspace/STM32MP1-Ecosystem-v4.0.0/Developer-Package/SDK`

The following log is output when the installation is successful:

ST OpenSTLinux - Weston - (A Yocto Project Based Distro) SDK installer version 4.0.1-openstlinux-5.15-yocto-kirkstone-mp1-v22.06.15===================================================================================================================================
You are about to install the SDK to "/opt/st/stm32mp1/4.0.1-openstlinux-5.15-yocto-kirkstone-mp1-v22.06.15". Proceed [Y/n]? Y
Extracting SDK............................................................................................................................................................................................................................done
Setting it up...done
SDK has been successfully set up and is ready to be used.
Each time you wish to use the SDK in a new shell session, you need to source the environment setup script e.g.
 $ ./opt/st/stm32mp1/4.0.1-openstlinux-5.15-yocto-kirkstone-mp1-v22.06.15/environment-setup-cortexa7t2hf-neon-vfpv4-ostl-linux-gnueabi


# Step 3 - Start the SDK up 

`$> cd /opt/st/stm32mp1/4.0.1-openstlinux-5.15-yocto-kirkstone-mp1-v22.06.15/`

`$> source environment-setup-cortexa7t2hf-neon-vfpv4-ostl-linux-gnueabi`

The following checks ensure that the environment is correctly set up:

- Check the target architecture

`$> echo $ARCH`

arm

- Check the toolchain binary prefix for the target tools

`$> echo $CROSS_COMPILE `

arm-ostl-linux-gnueabi-

- Check the C compiler version:

`$>$CC --version`

arm-ostl-linux-gnueabi-gcc (GCC) 11.2.0
Copyright (C) 2021 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

- Check that the SDK version is the expected one (e.g.):

`$> echo $OECORE_SDK_VERSION`

4.0.1-openstlinux-5.15-yocto-kirkstone-mp1-v22.06.15


# References
- https://wiki.st.com/stm32mpu/wiki/Getting_started/STM32MP1_boards/STM32MP157x-DK2/Develop_on_Arm%C2%AE_Cortex%C2%AE-A7/Install_the_SDK
