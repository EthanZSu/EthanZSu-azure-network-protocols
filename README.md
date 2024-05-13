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
For this 2st virtual machine: the subsciption account, resource group, & the geographic region should match the 1st VM's.
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
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
