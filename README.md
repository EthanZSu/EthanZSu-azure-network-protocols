# EthanZSu-azure-network-protocols

<p align="center">
<img src="https://i.imgur.com/7Go3II0.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups and Observing Network Protocols Between Azure Virtual Machines</h1>
This tutorial experiments with Network Security Groups & uses Wireshark to observe network traffic between Azure Virtual Machines (VMs). <br />


<h2>???Video Demonstration</h2>

- ### [YouTube: Azure Virtual Machines, Wireshark, and Network Security Groups](https://www.youtube.com)

<h2>Technologies Used</h2>

- Microsoft Azure (Virtual Machines)
- Remote Desktop
- Command-Line Tools
- Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>Overview of Main Steps</h2>

- Step 1: Make a resource group.
- Step 2: Make a Windows 10 virtual machine & a Linux virtual machine.
- Step 3: Install Wireshark onto the Windows 10 virtual machine.
- Step 4: Conduct a Network Security Group ping test between both virtual machines.
- Step 5: Initiate and Observe internet protocol traffic in the virtual machines.

<h2>Actions and Observations</h2>

<p>
<img src="https://github.com/EthanZSu/EthanZSu-azure-network-protocols/assets/168872181/6c31fed9-4ab9-4795-816f-13edd6838d8e" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
First, a new resource group must be made where the virtual machines will be placed  in.
  <br />
In the top search bar search: resource group and then in top left click "create".
  <br />
  <br />
Name the new resource group.
  <br />
Also select which subscription account to place the resource group under.
  <br />
And pick which geographic region you want the resource group in.
  <br />
  <br />
Then create the resource group.
</p>
<br />



<p>
<img src="https://github.com/EthanZSu/EthanZSu-azure-network-protocols/assets/168872181/8c1adcb6-557f-4cd4-8a9a-786b3b190ebb" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In the top search bar search: virtual machines, then click "create", then "Azure Virtual Machine".
  <br />
  <br />
For the 1st virtual machine: Select a subsciption account, the resource group just made, & the geographic region you want the VM in.
  <br />
Name this 1st VM.
  <br />
The above redundancy & security settings will suffice.
  <br />
The image (VM's operating system) will be Windows 10 Pro, ver. 22H2
  <br />
VM architecture x64 will suffice.
</p>
<br />



<p>
<img src="https://github.com/EthanZSu/EthanZSu-azure-network-protocols/assets/168872181/29c94b50-3323-4cd5-8cb1-0155d9b5374a" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Select size "2 vcpus" (2 virtual CPU's).
  <br />
Set up administrator account info for the VM: the username & password.
  <br />
Public inbound ports must allow selected ports, and allow RDP 3389 (for remote desktop to the VM).
  <br />
Scroll down & confirm you have the appropriate Windows 10/11 license.
</p>
<br />



<p>
<img src="https://github.com/EthanZSu/EthanZSu-azure-network-protocols/assets/168872181/05628e00-4509-44f8-b883-f91b1bb2397c" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
At the bottom click Next:Disks, then at the bottom again, click Next:Networking.
  <br />
  <br />
For this 1st VM, the virtual network, subnet, & public IP will be automatically made.
  <br />
For the NIC network security group select "basic".
  <br />
Public inbound ports must allow selected ports, and allow RDP 3389 (for remote desktop to the VM).
  <br />
Scrolling down, enable accelerated networking & select no load balancing.
  <br />
  <br />
Finally, Create this 1st VM.
  <br />
Note that Azure may take 5 minutes to deploy the VM.
</p>
<br />



<p>
<img src="https://github.com/EthanZSu/EthanZSu-azure-network-protocols/assets/168872181/fac7bc91-962a-4eb1-8841-48925ad1dd57" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
You must wait ~5 minutes before making the 2nd VM (so the 2nd VM can be placed in the same network as the 1st).
  <br />
In the top search bar search: virtual machines, then in top left click "create", then "Azure Virtual Machine".
  <br />
  <br />
For this 2nd virtual machine: the subsciption account, resource group, & the geographic region should match the 1st VM's.
  <br />
Name this 2st VM.
  <br />
The above redundancy & security settings will suffice.
  <br />
The image (VM's operating system) will be Ubuntu Server 20.04
  <br />
VM architecture x64 will suffice.
</p>
<br />



<p>
<img src="https://github.com/EthanZSu/EthanZSu-azure-network-protocols/assets/168872181/e0193885-d8d3-4c77-82c5-de369e06e15a" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Select size "2 vcpus" (2 virtual CPU's).
  <br />
Select authentication type: password.
  <br />
Set up administrator account info for the VM: the username & password.
  <br />
Public inbound ports must allow selected ports, and allow SSH 22 (for typing a remote command line to the VM).
</p>
<br />



<p>
<img src="https://github.com/EthanZSu/EthanZSu-azure-network-protocols/assets/168872181/9e8e0693-636f-420e-aaa5-267d2e9f8f39" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
At the bottom click Next:Disks, then at the bottom again, click Next:Networking.
  <br />
  <br />
For the 2nd VM, the virtual network must match the 1st VM's.
  <br />
The subnet, & public IP will be automatically made.
  <br />
For the NIC network security group select "basic".
  <br />
Public inbound ports must allow selected ports, and allow SSH 22 (for typing a remote command line to the VM).
  <br />
Scrolling down, enable accelerated networking & select no load balancing.
  <br />
  <br />
Finally, Create this 2nd VM.
  <br />
Note that Azure may take 5 minutes to deploy the VM.
<p>
  <br />


<p>
<img src="https://github.com/EthanZSu/EthanZSu-azure-network-protocols/assets/168872181/69629cdd-0cd4-41a3-bee8-35401aae7f1c" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In your Windows computer bottom search bar type: Remote Desktop Connection.
  <br />
In the top center search bar search: Virtual Machines.
  <br />
Select the Windows VM.
  <br />
Copy the Public IP address on the right side into the Remote Desktop Connection & Connect.
  <br />
Enter the administrator account credentials for the VM: the username & password.
</p>
<br />



<p>
<img src="https://github.com/EthanZSu/EthanZSu-azure-network-protocols/assets/168872181/6badce6b-9266-484e-bcda-c518839ca625" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Click "yes" on the pop-up.
</p>
<br />



<p>
<img src="https://github.com/EthanZSu/EthanZSu-azure-network-protocols/assets/168872181/e5f17491-cd13-4f1f-aae8-e10d06d17f00" height="150%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In the event you see this pop-up "mtsc.exe - Entry Point Not Found",
  <br />
Drag the pop-up to the top right corner & quickly exit it & the remote desktop window.
  <br />
If the pop-up is still there, simply click "OK".
  <br />
  <br />
You must then repeat the steps from the previous 2 pictures to use Remote Dektop to access your Windows VM. 
</p>
<br />



<p>
<img src="https://github.com/EthanZSu/EthanZSu-azure-network-protocols/assets/168872181/53752c9d-3d12-406a-8bd4-afd176f117e7" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Select "No" to all the privacy setting (as none of those features will be needed).
<br />
Then accept.
<br />
On the right click "yes" to the network pop-up "do you want... your PC to be discoverable by other... devices on this network?"
</p>
<br />



<p>
<img src="https://github.com/EthanZSu/EthanZSu-azure-network-protocols/assets/168872181/f719dad4-a1e0-4cff-9a3f-64eec8d693f8" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
If there is any Windows promotional pop-up, exit it.
  <br />
Decline all Windows offers to sign in & bring your data (because this project is temporary & requires none of that sign-up).

</p>
<br />



<p>
<img src="https://github.com/EthanZSu/EthanZSu-azure-network-protocols/assets/168872181/48fdecf6-a66c-4371-aa08-832fb3aea4bc" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open Microsoft Edge web browser.
  <br />
In the top search bar search "wireshark download" & go to the wireshark.org site.
</p>
<br />



<p>
<img src="https://github.com/EthanZSu/EthanZSu-azure-network-protocols/assets/168872181/ee17dc94-c4e3-4261-8579-51b28a08098b" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Download Windows x64 Installer from the latest Stable Release Version.
  <br />
Once it's finished downloading, open the file.
  <br /> 
Minimize the window.
</p>
<br />



<p>
<img src="https://github.com/EthanZSu/EthanZSu-azure-network-protocols/assets/168872181/6ebd9af3-10ca-47f8-af9f-a6172dbcaf26" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Select "Next", "Noted", keep selecting "Next", then "Install"
</p>
<br />



<p>
<img src="https://github.com/EthanZSu/EthanZSu-azure-network-protocols/assets/168872181/4444c361-097e-4f3c-acb0-1da59e2b1281" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Select "I Agree", "Install", "Next", "Finish", "Next", "Finish".
</p>
<br />



<p>
<img src="https://github.com/EthanZSu/EthanZSu-azure-network-protocols/assets/168872181/e2c49c58-f3a8-4c54-8ffa-39e398584583" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Exit the web browser windows.
  <br />
In the bottom taskbar search "wireshark".
</p>
<br />



<p>
<img src="https://github.com/EthanZSu/EthanZSu-azure-network-protocols/assets/168872181/e02d8fc5-641e-45f5-80d1-85c31af3a71b" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Click "Ethernet" & you will see the contant traffic between the Windows VM & the Internet.
</p>
<br />



<p>
<img src="https://github.com/EthanZSu/EthanZSu-azure-network-protocols/assets/168872181/f9eda5ed-fbf0-4a78-a198-4e86a443b6f3" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In Wireshark, at the top filter for "icmp".
  <br />
  <br />
Back to Azure, search for "virtual machines", select  your Linux VM, scroll down & copy the private IP on the right side.
  <br />
In Remote Desktop, from your taskbar open Windows Powershell.
  <br />
In Powershell type: ping, then paste your Linux VM private IP, & hit ENTER.
  <br />
  <br />
WARNING: if the ping "times out",  you maybe pinged with the Linux Public IP instead of the Private IP.
  <br />
WARNING: if the ping doesn't work, you maybe didn't wait long enough before making the Linux VM 
  (so the Linux VM may not be on the same virtual network as the Windows VM).
  <br />
  <br />
In Wireshark, you see the traffic between both VM's as the Windows VM pings, & the Linux replies.
  <br />
In Powerhell, you see the Windows VM received 4 replies from the Linux VM.
</p>
<br />



<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />



<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />



<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
