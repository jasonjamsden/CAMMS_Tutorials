# Tutorial for connecting the Keithley Source Measure Unit to Ubuntu 20.04 over USB.

The Source Measure Unit **Keithley 2461** and **Ubuntu 20.04** operating systems are used in this tutorial, but it may also be applicable to other Keithley Source Measure Unit machines from the 24XX family which have USB connection capabilities avaialble. For this tutorial we need an additional software in order to function relative to the LAN connection which does not need additional drivers.

![USB-0](images/USB-0.jpg "USB-0")

# Step 1: Cable connection
This section describes how to set up the USB communications on your computer. The Keithley 2461 USB port is located at the back of the device, connect the one end. 

![USB-1](images/USB-1.jpg "USB-1")

To communicate from a computer to the instrument you need a USB cable with a USB Type B connector end and a USB type A connector end. You need a separate USB cable for each instrument you plan to connect to the computer at the same time using the USB interface. To connect an instrument to a computer using USB:

- Connect the Type A end of the cable to the computer.
- Connect the Type B end of the cable to the instrument.
- Turn on the instrument power. When the computer detects the new USB connection, the Found New Hardware Wizard starts.
- If the “Can Windows connect to Windows Update to search for software?” dialog box opens, select No, and then select Next.
- On the “USB Test and Measurement device” dialog box, select Next, and then select Finish.


# Tutorial for connecting the Keithley Source Measure Unit to Ubuntu 20.04 over USB.

The Source Measure Unit **Keithley 2461** and **Ubuntu 20.04** operating systems are used in this tutorial, but it may also be applicable to other Keithley Source Measure Unit machines from the 24XX family which have USB connection capabilities avaialble. For this tutorial we need an additional software in order to function relative to the LAN connection which does not need additional drivers.

![USB-0](images/USB-0.jpg "USB-0")

# Step 1: Cable connection
This section describes how to set up the USB communications on your computer. The Keithley 2461 USB port is located at the back of the device, connect the one end. 

![USB-1](images/USB-1.jpg "USB-1")

To communicate from a computer to the instrument you need a USB cable with a USB Type B connector end and a USB type A connector end. You need a separate USB cable for each instrument you plan to connect to the computer at the same time using the USB interface. To connect an instrument to a computer using USB:

- Connect the Type A end of the cable to the computer.
- Connect the Type B end of the cable to the instrument.
- Turn on the instrument power. When the computer detects the new USB connection, the Found New Hardware Wizard starts.
- If the “Can Windows connect to Windows Update to search for software?” dialog box opens, select No, and then select Next.
- On the “USB Test and Measurement device” dialog box, select Next, and then select Finish.

# Step 2: USB Status

When you connect the cables, It’s time to check the connection status. By opening and Terminal and executing the command ```lsusb``` you should see the name with an output with a similar format, which contains the Name, and basic information of the Keithley Source Measure Unit. 

![USB-2](images/USB-2.jpg "USB-2")

By executing the command ```lsusb -v``` you should see detailed information about all the USB devices and detailed information about Keithley Source Measure Unit. 

![USB-3](images/USB-3.jpg "USB-3")

For the instrument to communicate with the Computer, we must use a driver, which requires to be able to read a resource string in the following format to receive and send data from the Ubuntu to the Keithley Source Measure Unit: ```USB0::0x05e6::0x2461::[serial number]::INSTR```.
Where: 
- 0x05e6: The Keithley vendorID 
- 0x2461: The instrument model number 
- [serial-number]: The serial number of the instrument
- INSTR: Use the USB TMC protocol
 As presented in the above image by executing the command ```lsusb -v```.

# Step 3: Permissions

Usually in Ubuntu in order for the driver to see, read, and write on the device, we need to give the Keithley Source Measure Unit permission from the root. 

![USB-4](images/USB-4.jpg "USB-4")

By going to the directory ```/dev/bus/usb``` and by selecting the BUS number, which in our case is ```002``` we see the connected devices on this BUS. By executing the command ```ls -al``` we see the permissions that each connected device on this BUS has. 

![USB-5](images/USB-5.jpg "USB-5")

We need to change these permissions and give full access to the Keithley Source Measure Unit. By going to the directory   ```/etc/udev/rules.d ``` we may write a new rule. By executing the command ```sudo vim 99-param.rules``` we create a new file in which we write the following rule: ```SUBSYSTEM==“usb”, ATTRS{idVendor}==“05e6”, ATTRS{idProduct}==“2461”, GROUP=“root”, MODE=“777”``` and the System Reboot.

![USB-6](images/USB-6.jpg "USB-6")

# Step 4: Establish the connection

From the Rohde&Scharz Company download the R&S VISA for Ubuntu driver: https://www.rohde-schwarz.com/us/driver-pages/remote-control/3-visa-and-tools_231388.html
Execute the ```.deb``` program.

![USB-7](images/USB-7.jpg "USB-7")

Open the RsVisa Configure application from the Application Finder of Ubuntu and press the plus icon.
In the VISA Resource String manually insert the string  ```USB0::0x05e6::0x2461::::INSTR``` and press the search icon.

![USB-8](images/USB-8.jpg "USB-8")

Then a pop-up window will appear with the same string you inserted, in case it doesn’t appear click the refresh icon at the bottom-left corner of the window. Press the string and then select and OK.

![USB-9](images/USB-9.jpg "USB-9")

And with that connection is established between Keithley Source Measure Unit and Ubuntu. Now we need a program to communicate with the device.

# Step 5 (A): Communicate with the instrument (NI-VISA)

For the instrument to communicate with the Computer, we must use a driver, which in our case is the NI-VISA. 

![USB-10](images/USB-10.jpg "USB-10")

We need to install NI-VISA. Download and extract the files from the NI Linux Device Drivers doc: https://www.ni.com/en-us/support/downloads/drivers/download.ni-linux-device-drivers.html

Following the guidelines from the Install NI Driver Software on Linux: https://www.ni.com/en-us/support/documentation/supplemental/18/downloading-and-installing-ni-driver-software-on-linux-desktop.html execute the following commands:

```sudo apt update```  
```sudo apt dist-upgrade```  
System Reboot    
```sudo touch /usr/src/linux-headers-$(uname -r)/include/config/modversions.h```  
Install the 4 files from the extracted folder with ```.deb``` suffix:   
```sudo apt install ./ni-software-2020-bionic_20.1.0.49152-0+f0_all.deb```    
```sudo apt update```    
Install the NI-VISA packages: ``` sudo apt install ni-visa*  ```  
```sudo dkms autoinstall```  
System Reboot   
After the installation, by executing the command ```visaconf``` or ```NIvisaic``` the NI visa window opens and we should see the USB-connected device ```USB0::0x05e6::0x2461::::INSTR```. You may send queries towards the device.  

![USB-11](images/USB-11.jpg "USB-11")

# Step 5 (A): Communicate with the instrument (Python)

NI-VISA is one way to communicate with the device. Nevertheless, we may communicate with the device by using Python, and **WITHOUT using NI-VSA**.   

Initially install python and pip with the following command ```sudo apt-get install python3-dev python3-distutils python3-pip python3-setuptools``` 
Then install the VISA packages in python: ```pip3 install pyvisa``` and ```pip3 install pyvisa-py```
By creating a script:   
``` 
import pyvisa
rm = pyvisa.ResourceManager()
m.list_resources()
```  
We receive a list of connected devices and in our case ```USB0::0x05e6::0x2461::::INSTR```

![USB-12](images/USB-12.jpg "USB-12")



For the instrument to communicate with the Computer, we must use a driver, which in our case is the NI-VISA. 


# NOTES

Every time the connection between Ubuntu and Keithley Source Measure Unit get lost use the RsVisa Configure and manually eatable the connection as in step 4.



# Refs & Links
Image Ubuntu: 
Article: https://download.tek.com/manual/2461-901-01_A_Nov_2015_Ref.pdf    
Article: https://www.xmodulo.com/change-usb-device-permission-linux.html    
Article: https://www.cl.cam.ac.uk/~osc22/tutorials/gpib_usb_linux.html    
Article: https://pyvisa.readthedocs.io/en/latest/    