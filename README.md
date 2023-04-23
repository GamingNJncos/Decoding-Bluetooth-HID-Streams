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
C:\BTP\v1.14.0\x86\btvs.exe -Mode Wireshark


##Step 4: In the pop up window from the above command (not wireshark) Click "Full Packet Logging"


##Step 5: In Wireshark filter with "usbhid" no qoutes

##Step 6: Click on Packet(s) and copy the value
In the other pane with packet contents find and expand "Bluetooth Atrribute Protocol"
Right Click Value > Copy > As Hex stream


##Step 7: Decode the copied hexstream here:
http://eleccelerator.com/usbdescreqparser/
-Paste the contents in the top window
-Click "I don't know"


##Various Pointers for troubleshooting custom Bluteooth/BLE controller dev


Look at Packet Rates in Wireshark
Statistics > IO Graph
