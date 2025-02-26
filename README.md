<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />




<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Computer)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Create a Resource Group
- Create a Windows 10 Virtual Machine (VM)
- Create a Linux (Ubuntu) VM
- Ensure both VMs are in the same Virtual Network / Subnet
- If using Mac, install Microsoft Remote Desktop
- Use Remote Desktop to connect to your Windows 10 Virtual Machine
- Within your Windows 10 Virtual Machine, Install Wireshark
- Open Wireshark and start packet capture
- Within Wireshark, filter for ICMP traffic only
- Retrieve the private IP address of the Ubuntu VM (linux-vm) and attempt to ping it from within the Windows 10 VM
- From The Windows 10 VM, open command line or PowerShell and attempt to ping a public website (such as www.google.com) and observe the traffic in WireShark
- Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM
- (Observe SSH Traffic)
- (Observe DHCP Traffic)
- (Observe DNS Traffic)
- (Observe RDP Traffic)

<h2>Actions and Observations</h2>
<h3>Step 1: Create a Resource Group</h3>

![01](https://github.com/user-attachments/assets/c3a27f88-bd59-4221-b53b-c95aa7e570c4)

<h3>Step 2: Create a Windows 10 Virtual Machine (VM)</h3>
<p>While creating the VM, select the previously created Resource Group</p>

![02](https://github.com/user-attachments/assets/5bf1a2b0-9ec8-44ba-b538-addde375d187)

<p>While creating the VM, allow it to create a new Virtual Network (Vnet) and Subnet</p>

![03](https://github.com/user-attachments/assets/8e9d496b-7238-4bdf-8394-794eead4e305)

<h3>Step 3: Create a Linux (Ubuntu) VM)</h3>
<p>While creating the VM, select the previously created Resource Group and Virtual Network—the Virtual Network MUST BE THE SAME.</p>
<p>Authentication type: Username/Password</p>

![04](https://github.com/user-attachments/assets/4daf8eb0-d982-49c4-9fab-9380eab3557b)



