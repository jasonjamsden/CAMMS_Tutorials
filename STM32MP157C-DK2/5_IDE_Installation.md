# Install IDE

# Step 1: STM32CubeIDE Installation

- From the following STM32CubeIDE website: https://www.st.com/en/development-tools/stm32cubeide.html#getsoftware-scroll download the latest software on your Host Computer. As Host Computer for the purposes of the STM32MP15 Microprocessor we name the computer which we will connect with your STM32MP15 Microprocessor and communicate via this computer to the device.

- Then go to this zip file you downloaded and uncompress it in order to get the STM32CubeIDE installers (it doesn’t matter where you save this folder, in the next step you will select in which folder, in particular, this STM32CubeProgrammer will be installed).  

`unzip en.st-stm32cubeide_1.10.1_12716_20220707_0928_amd64.deb_bundle.sh.zip`

- Open a terminal in this directory and execute the Linux installer which the following command:  

`chmod +x st-stm32cubeide_1.10.1_12716_20220707_0928_amd64.deb_bundle.sh`  

`./st-stm32cubeide_1.10.1_12716_20220707_0928_amd64.deb_bundle.sh`

- If you go to your GUI applications now you will see STM32 IDE program.

# Step 2: Install STM32CubeMP1 package

- Download the STM32CubeMP1 from: https://www.st.com/en/embedded-software/stm32cubemp1.html#get-software/STM32Cube_FW_MP1_V1.6.0.zip
- Move this file to the "STM32MPU_workspace/STM32MP1-Ecosystem-v4.0.0/Developer-Package" directory 
- Uncompress the archive file to get the STM32CubeMP1 Package

# Step 3: Modify, rebuild and reload a firmware
- It proposes to customize the STM32MP1 Cube Package application example "OpenAMP_TTY_Echo" using STM32CubeIDE.



# References
- https://wiki.st.com/stm32mpu/wiki/Getting_started/STM32MP1_boards/STM32MP157x-DK2/Develop_on_Arm%C2%AE_Cortex%C2%AE-M4/Install_the_IDE
