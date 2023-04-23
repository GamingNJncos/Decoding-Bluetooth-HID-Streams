**Decoding-Bluetooth-HID-Streams**

**Background:**
There are various ways in windows to capture BT traffic. Many are a pain however the instructions provided here are hands down the best around

https://github.com/darthcloud/BlueRetro/wiki/Bluetooth-HCI-trace-with-Win10

Before proceeding following the above directions will help you get everything you need installed.  I've included it below for clarity as a "step", however it's really the keys to the kingdom. The goal here is to provide start to finish HID Decoding for ease of use


**Step 1**: 
Make sure the controller or device is *not* paired with the PC First


**Step 2**:
Download and install the neccesary applications from this guide
https://github.com/darthcloud/BlueRetro/wiki/Bluetooth-HCI-trace-with-Win10

For Brevity here's a copy pasta
 - Software to install
 - Download and install latest version of Wireshark:
 - You don't need to install any of the optional drivers when prompted
 - https://www.wireshark.org/#download
 - Download and install latest version of Microsoft Bluetooth Test Platform:
- https://learn.microsoft.com/en-us/windows-hardware/drivers/bluetooth/testing-btp-setup-package


**Step 3: Start Capturing**
[Windows Key]+R or start>run
C:\BTP\v1.14.0\x86\btvs.exe -Mode Wireshark


**Step 4**: In the pop up window from the above command (not wireshark) Click "Full Packet Logging"
![BTVS](https://i.imgur.com/t27w91v.jpeg)

**Step 5**: In Windows Pair with your device 

**Step 6**:In Wireshark filter with "usbhid" no qoutes

**Step 7**: Click on Packet(s) and Expland Bluetooth Atribbute Protocl > HID Report
![HID Report 1](https://i.imgur.com/Ypb0K31.jpeg)

**Step 8: Copy the data from the HID Report**
In the other pane with packet contents find and expand "Bluetooth Atrribute Protocol"
Right Click Value > Copy > As Hex stream
![Copy Hex Stream](https://i.imgur.com/8wULkem.jpeg)

**Step 9: Decode the copied hexstream here:**
http://eleccelerator.com/usbdescreqparser/
-Paste the contents in the top window
-Click "I don't know" 
![Paste hex stream](https://i.imgur.com/AyYLLPd.jpeg)

**Step 10: View Decoded Data**
![Decoded Data](https://i.imgur.com/JV7gx3m.jpeg)

Compare this to the view in wireshark of the same packet contents and its easy to spot why decoding this way is a bit more legible 

![Wireshark Decoded](https://i.imgur.com/IP6XjNb.jpeg)


**Various Pointers Bluteooth/BLE controller dev**

**Configuration Profiles**
Use configuration profiles to make Wireshark a bit easier to review BT details
![Configuration Profiles](https://i.imgur.com/JVUuGcA.jpeg)
![Configuration Profiles 2](https://i.imgur.com/QYNDyfj.jpeg)

Look at Packet Rates in Wireshark
For things like battery utilization or odd bugs, knowing what is or is not being transmitted and how often is hugely helpful

Go to Statistics > IO Graph to get a visual depiction of packet rate, errors, and even graphing filtered packets
![IO1](https://i.imgur.com/Rv4AxBw.jpeg)

![IO2](https://i.imgur.com/p9G5ljB.jpeg)
