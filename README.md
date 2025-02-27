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

![03](https://github.com/user-attachments/assets/a420a3b8-cd7d-45cb-9506-8b402fe5b1c5)

<h3>Step 3: Create a Linux (Ubuntu) VM)</h3>
<p>While creating the VM, select the previously created Resource Group and Virtual Network—the Virtual Network MUST BE THE SAME.</p>
<p>Authentication type: Username/Password</p>

![04](https://github.com/user-attachments/assets/4daf8eb0-d982-49c4-9fab-9380eab3557b)

<h2>(Observe ICMP Traffic)</h2>

<h3>Step 4: If using Mac, install Microsoft Remote Desktop</h3>

<h3>Step 5: Use Remote Desktop to connect to your Windows 10 Virtual Machine</h3>

![05](https://github.com/user-attachments/assets/4c609a2f-4d5a-4b17-991b-61df212cbb1d)

<h3>Step 6: Within your Windows 10 Virtual Machine, Install Wireshark</h3>

![06](https://github.com/user-attachments/assets/8a7ce2d0-7f78-40e2-9fc4-7c96a08ca211)

<h3>Step 7: Open Wireshark and start packet capture</h3>

![07](https://github.com/user-attachments/assets/64baade2-e201-4d62-adc8-72ef7e860435)

<h3>Step 8: Within Wireshark, filter for ICMP traffic only</h3>

![08](https://github.com/user-attachments/assets/b62849f2-a9d1-4cb8-bb0b-20ce1ea3ef38)

<h3>Step 9: Retrieve the private IP address of the Ubuntu VM (linux-vm) and attempt to ping it from within the Windows 10 VM</h3>

![09](https://github.com/user-attachments/assets/e55e6519-ee39-4f28-987d-56cb97fffae9)

<p>Observe ping requests and replies within WireShark</p>

![10](https://github.com/user-attachments/assets/e7cea454-3493-4831-b756-196d0047e797)

<h3>Step 10: From The Windows 10 VM, open command line or PowerShell and attempt to ping a public website (such as www.google.com) and observe the traffic in WireShark</h3>

![11](https://github.com/user-attachments/assets/706fd04f-54b0-438b-94ef-a072f07cae45)

<h2>(Configuring a Firewall [Network Security Group])</h2>

<h3>Step 11: Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM</h3>

![12](https://github.com/user-attachments/assets/b6dc3b9d-5369-4939-a9d3-75747c163628)

<p>Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic</p>

![13](https://github.com/user-attachments/assets/c5febff1-cc44-4446-bf5f-66e88cccf10d)

<p>Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity</p>

![14](https://github.com/user-attachments/assets/8fb9e365-ff62-4cc8-a19b-dbd9a2e6fed9)

![15](https://github.com/user-attachments/assets/9d0590b8-4027-4a31-b103-cf3824102312)

<p>Re-enable ICMP traffic for the Network Security Group your Ubuntu VM is</p>

![16](https://github.com/user-attachments/assets/57151060-73b8-42e2-b646-e8f0cc70c561)


<p>Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line, Ping activity (should start working)</p>

![17](https://github.com/user-attachments/assets/0fb6be8a-6053-4e2c-8ab7-d07cdd644871)

![18](https://github.com/user-attachments/assets/d19a72e2-6860-4abf-8bac-33e9bfb4f5ed)

<p>Press Control + C to stop the ping activity</p>

<h2>(Observe SSH Traffic)</h2>

<h3>Step 12: Back in Wireshark, start a packet capture up</h3>

<h3>Step 13: Filter for SSH traffic only</h3>

![19](https://github.com/user-attachments/assets/853c004f-41b7-4f5a-9864-bfe72e1dc5ba)

<h3>Step 14: From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address)</h3>

<h3>Step 15: Open PowerShell, and type: ssh [username for linux vm]@[private IP address]</h3>

<p>Type commands (username, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark</p>

![{DAF75C29-1F4C-4B77-A11C-D3B38C0049B0}](https://github.com/user-attachments/assets/f4f680c4-b35a-42f6-b51c-c304892000fd)

<p>Exit the SSH connection by typing ‘exit’ and pressing [Enter]</p>

<h2>(Observe DHCP Traffic)</h2>

<h3>Step 16: Back in Wireshark, filter for DHCP traffic only</h3>

<h3>Step 17: From your Windows 10 VM, attempt to issue your VM a new IP address from the command line</h3>

<p>Open PowerShell as admin and run: ipconfig /renew</p>

![21](https://github.com/user-attachments/assets/b33d186c-0524-436f-ab5e-7c3f524bf708)

<p>Observe the DHCP traffic appearing in WireShark</p>

<h2>(Observe DNS Traffic)</h2>

<h3>Step 18: Back in Wireshark, filter for DNS traffic only</h3>

<p>From your Windows 10 VM within a command line, use nslookup to see what google.com and disney.com’s IP addresses are</p>

![22](https://github.com/user-attachments/assets/5688ca02-0141-4dc7-9830-3e1a15447a3d)

<h2>(Observe RDP Traffic)</h2>

<h3>Step: 19: Back in Wireshark, filter for RDP traffic only (tcp.port == 3389)</h3>

<h2>Lab Cleanup</h2>

<h3>Close your Remote Desktop connection</h3>
<h3>Delete the Resource Group(s) created at the beginning of this lab</h3>
<h3>Verify Resource Group Deletion</h3>


