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



- Based on: https://source.android.com/docs/setup/download#installing-repo  

# References
- https://wiki.st.com/stm32mpu/wiki/Getting_started/STM32MP1_boards/STM32MP157x-DK2/Develop_on_Arm%C2%AE_Cortex%C2%AE-A7/Install_the_SDK
