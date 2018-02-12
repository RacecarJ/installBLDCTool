# installBLDCTool
The BLDC-Tool is used to flash firmware and configuration files to a hardware compatible Vedder Electronic Speed Controller (VESC). The VESC is an open source Brushless DC Motor Controller (BLDC). See:

http://vedder.se/2015/01/vesc-open-source-esc/

This repository contains scripts to build the BLDC-Tool on a NVIDIA Jetson TX development kit running L4T 28.1, and a script for building a desktop x86 Linux Ubuntu 14.04 version. The x86 Ubuntu machine is typically used to flash the Jetson using JetPack. The tool may be used by either platform to program the VESC. 

<h3>Jetson TX Development Kit</h3>
Install the BLDC-Tool on the NVIDIA Jetson TX development Kit. The BLDC-Tool is for use with VESC compatible 4.12 hardware.

To run the script:
<blockquote>
./installBLDCToolJetson.sh
</blockquote>

These scripts will install the bldc-tool for Vedder Electronic Speed Controller (<b>VESC</b>) and compatible hardware, version 4.12. This type of hardware is sometimes referred to as BLDC controller. The VESC is used in the RACECAR/J project.

The VESC is an open source hardware and software brushless motor controller.

Running the install script builds the bldc-tool, a Qt Gui to interact with the BLDC controller.
Before building the tool, the required prerequisites are installed. 

<em><b>Note:</em</b> The version of libqt5serialport5-dev is 5.5. There is an issue which causes the Bldc-Tool to segment fault when the VESC reboots after being flashed using that version. The work around is to use version 5.6. The scripts builds qtserialport from source and installs it in order to address this issue.</em>

Next the bldc-tool is compiled from source.

Note that this is the tool that can configure and load firmware on the VESC, not the actual firmware that runs on the VESC. The firmware is in a separate repository. See: https://github.com/racecarj/bldc-tool

The last step in the script installs VESC firmware and VESC configuration files in the directory ~/vesc-firmware for use with the RACECAR/J configuration. The VESC firmware is located in:

~/vesc-firmware/firmware/VESC_servoout.bin

The firmware includes support for using the PWM output to control the steering servo.

The Configuration files are in the VESC-Configuration directory. There are two different configurations:
<ul>
<li>VESC_30k_erpm.xml</li>
<li>FOCBOX_hw_30k_erpm.xml</li>
</ul>

The VESC_30k_erpm.xml configuration is for VESC 4.12 compatible hardware. For Enertion Boards VESC-X/FOCBOX hardware, there is FOCBOX_hw_30k_erpm.xml

<em><b>Note:</b> Compiled versions of the firmware are also contained in the bldc-tool repository in the 'firmwares' directory.</em>

<h3>Desktop Linux Host</h3>
For Linux Ubuntu 14.04 running on an x86 machines (typically used to flash a Jetson using JetPack), there is an installation script which installs the prerequisites, downloads and builds the BLDC-Tool. This script:

<blockquote>
./installBLDCToolHost.sh</blockquote>

The last step in the script installs VESC firmware and VESC configuration files in the directory ~/vesc-firmware for use with the RACECAR/J configuration. The VESC firmware is located in:

~/vesc-firmware/firmware/VESC_servoout.bin

The firmware includes support for using the PWM output to control the steering servo.

The Configuration files are in the VESC-Configuration directory. There are two different configurations:
<ul>
<li>VESC_30k_erpm.xml</li>
<li>FOCBOX_hw_30k_erpm.xml</li>
</ul>

The VESC_30k_erpm.xml configuration is for VESC 4.12 compatible hardware. For Enertion Boards VESC-X/FOCBOX hardware, there is FOCBOX_hw_30k_erpm.xml

<em><b>Note:</b> Compiled versions of the firmware are also contained in the bldc-tool repository in the 'firmwares' directory.</em>





