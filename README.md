<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Create Resource Groups and Virtual Machines
- Install & Run Wireshark
- Observe ICMP Traffic
- Observe SSH Traffic
- Observe DHCP Traffic
- Observe RDP Traffic

<h2>Actions and Observations</h2>

<h3>Create Resource Groups and Virtual Machines</h3>

<p>
<img src="https://i.imgur.com/3oh2QG5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In Microsoft Azure, create a resource group and two virtual machines. Creating the VM will also allow you to create a new virtual network aka (Vnet). Create a Windows client virtual machine and an Linux (Ubuntu) server. Use the same Vnet that was created for your Windows VM.
</p>
<br />

<h3>Install and Run Wireshark</h3>

<p>
<img src="https://i.imgur.com/YmO6jE2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go into your Windows Virtual Machine and open an internet browser and search "download Wireshark" and download it from the actual website.
Wireshark is a network protocol analyzer. It is used to troubleshoot networks, analysis, software & protocol development, and education.  It is the most widely used network analyzer. 
</p>
<br />

<p>
<img src="https://i.imgur.com/k5yORMd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
On the website, click on Windows Installer to download-->Click Open File from the Downloads window on your browser-->Click next on the setup dialog box and advance next to install all of the prerequisite programs required to install Wireshark.
</p>
<br />

<p>
<img src="https://i.imgur.com/Pzwu5hh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open Wireshark and click on the blue fin icon located right under the file menu.  Once you click  on that icon, Wireshark will start analyzing all network traffic on the virtual machine.
</p>
<br />

<h3>Observe ICMP Traffic</h3>
<p>
<img src="https://i.imgur.com/fpgRTct.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Use the Remote Destkop Windows 10 Virtual Machine. Use Wireshark to filter traffic for ICMP by typing it in the filter bar and click on the blue arrow button to the right to start the filter.
</p>
<br />

<p>
<img src="https://i.imgur.com/exO4wSd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Retrieve the private IP address of the Linux (Ubuntu) virtual machine and attepmt to ping it in the Windows 10 virtual machine.
</p>
<br />

<p>
<img src="https://i.imgur.com/V2StxGH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From the Windows 10 virtual machine open Powershell and attempt to ping the private IP address of VM 2 server and observe the requests and replies within Wireshark.
</p>
<br />

<p>
<img src="https://i.imgur.com/95bUvyI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From the Windows 10 virtual machine, open PowerShell and attempt to ping www.google.com and observe the traffic in Wireshark. 

From the PowerShell, you can see the packets of data sent and the statics at the bottom.  

From Wireshark, you can see the packets of data replied through google.com and the data being sent.
</p>
<br />

<p>
<img src="https://i.imgur.com/NHRm8z7.pngg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From the Windows 10 virtual machine. Send a non-stop ping request in Windows Powershell buy typing ping -t www.google.com. 

It will receive non-stop packet requests until you cancel it.  To cancel the ping request go to PowerShell and hit ctrl+C.
</p>
<br />

<p>
<img src="https://i.imgur.com/UiJhzQd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In the Microsoft Azure portal open Network Security Group on your VM2  to initiate a perpetual/non-stop ping from your Windows 10 virtual machine to your Ubuntu VM.
</p>
<br />

<p>
<img src="https://i.imgur.com/CzsSguE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In your Windows 10 virtual machine, observe the ICMP traffic in WireShark and the command line Ping activity.
</p>
<br />

<p>
<img src="https://i.imgur.com/bI7IifN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In Microsoft Azure network security group settings. Select your deny ICMP settings and allow ICMP traffic to resume. 
</p>
<br />

<p>
<img src="https://i.imgur.com/rh0KlQ4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In your Windows 10 virtual machine, ping your Ubuntu server VM2 private IP address and observe the packets of data resume. 
</p>
<br />

<h3>Observe SSH Traffic</h3>

<p>
<img src="https://i.imgur.com/3UMSqJ6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In your Windows 10 virtual machine connect to your Unbuntu (VM2) virtual machine using SSH via Powershell.  
Use the command SSH your VM2 username@VM2 private address and hit enter. 
Type your password and hit enter.
</p>
<br />

<p>
<img src="https://i.imgur.com/uqsE3hg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From your Window 10 virtual machine (VM1) type in commands (ld, uname -a, pwd, and ls lasth) and observe the output in PowerShell and data packets in WireShark. 

To logout out of the server, type "exit" in the command line in PowerShell and hit enter.
</p>
<br />

<h3>Observe DHCP Traffic</h3>

<p>
<img src="https://i.imgur.com/PGWImY3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From your  Windows 10 virtual machine. Filter DHCP traffic in the search bar on WireShark.  On PowerShell renew your IP address lease by typing in the command line ipconfig /renew. *Your virtual machine will get assigned a new IP address. Observe the DHCP traffic in WireShark echo request. 

*Note your VM may disconnect when getting assigned a new IP address.
</p>
<br />

<h3>Observe DNS Traffic</h3>

<p>
<img src="https://i.imgur.com/gubhgzc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From Windows 10 virtual machine. Filter out DNS network traffic in Wireshark by typing DNS in the search bar. From Windows PowerShell give command line "nslookup www.google.com" Observe Google's IP address and DNS returned in PowerShell. Observe the IP address and DNS returned in the data packets in WireShark
</p>
<br />

<h3>Observe RDP Traffic</h3>

<p>
<img src="https://i.imgur.com/YeQbDTP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From your Windows 10 virtual machine. Go to WireShark and type RDP in the search bar to filter only RDP traffic.  Click on the blue arrow to the right to activate the filter.
Observe the network traffic in WireShark. 
</p>
<br />



