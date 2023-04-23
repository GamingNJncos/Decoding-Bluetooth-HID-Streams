# Decoding-Bluetooth-HID-Streams

##Background:
There are various ways in windows to capture BT traffic. Many are a pain however the instructions provided here are hands down the best around

https://github.com/darthcloud/BlueRetro/wiki/Bluetooth-HCI-trace-with-Win10

Before proceeding following the above directions will help you get everything you need installed.  I've included it below for clarity as a "step", however it's really the keys to the kingdom. The goal here is to provide start to finish HID Decoding for ease of use


##Step 1: 
Make sure the controller or device is *not* paired with the PC First


##Step 2:
Download and install the neccesary applications from this guide
https://github.com/darthcloud/BlueRetro/wiki/Bluetooth-HCI-trace-with-Win10

For Brevity here's a copy pasta
 - Software to install
 - Download and install latest version of Wireshark:
 - You don't need to install any of the optional drivers when prompted
 - https://www.wireshark.org/#download
 - Download and install latest version of Microsoft Bluetooth Test Platform:
- https://learn.microsoft.com/en-us/windows-hardware/drivers/bluetooth/testing-btp-setup-package


##Step 3:Start Capturing
[Windows Key]+R or start>run
C:\BTP\v1.14.0\x86\btvs.exe -Mode Wireshark


##Step 4: In the pop up window from the above command (not wireshark) Click "Full Packet Logging"
![BTVS](https://imgur.com/a/3hvhHpE)

##Step 5: In Windows Pair with your device 

##Step 6:In Wireshark filter with "usbhid" no qoutes

##Step 7: Click on Packet(s) and Expland Bluetooth Atribbute Protocl > HID Report
![HID Report 1](https://imgur.com/a/ivdF1To)

##Step 8: Copy the data from the HID Report
In the other pane with packet contents find and expand "Bluetooth Atrribute Protocol"
Right Click Value > Copy > As Hex stream
![Copy Hex Stream](https://imgur.com/a/9Wx3JSc)

##Step 9: Decode the copied hexstream here:
http://eleccelerator.com/usbdescreqparser/
-Paste the contents in the top window
-Click "I don't know" 
![Paste hex stream](https://imgur.com/a/Uy5MQlt)

##Step 10: View Decoded Data
![Decoded Data](https://imgur.com/a/SoWKf3Q)

Compare this to the view in wireshark of the same packet contents and its easy to spot why decoding this way is a bit more legible 

![Wireshark Decoded](https://imgur.com/a/96xEjCn)


##Various Pointers Bluteooth/BLE controller dev

Configuration Profiles
Use configuration profiles to make Wireshark a bit easier to review BT details
![Configuration Profiles](https://imgur.com/a/WlFd9xH)
![Configuration Profiles 2](https://imgur.com/a/JIN1hlU)

Look at Packet Rates in Wireshark
For things like battery utilization or odd bugs, knowing what is or is not being transmitted and how often is hugely helpful
Statistics > IO Graph
![IO1](https://imgur.com/a/t8OKZT4)
![IO2](https://imgur.com/a/tDdjPzW)
