<p align="center">
<img src="https://i.imgur.com/Xa3FX3j.jpeg" alt="Wireshark Logo"/>
</p>

<h1>Filtering Network Traffic and Performing Network Activites Using CLI Tools (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Wireshark
- Microsoft Remote Desktop (MAC)
- PowerShell

<h2>Operating Systems Used </h2>

- Linux (Umbuntu)
- Windows 10 

<h2>Creating Resources Steps</h2>
<img src="https://i.imgur.com/QTTbVyp.jpeg" alt="azure virtural machines"/>

- Step 1: Create Window 10 Virtual Machine (VM) making sure that is housed in your previously created resource group (use auto populated Virtual Network (Vnet) and Subnet
- Step 2: Create Linux Ubuntu VM, *select previously created Resource Group and Vnet
- Step 3: Observe you VM in the network watcher 

<h2>Observing ICMP Traffic</h2>

<p>
<img src="https://i.imgur.com/x8RD0qk.jpeg" height="80%" width="80%" alt="Using Wireshark to filter for ICMP traffic"/>
</p>
<p>
To analyze network connectivity between a Windows 10 Virtual Machine (VM) and an Ubuntu VM, I first connected to the Windows 10 VM via Remote Desktop. Once connected, I installed Wireshark within the Windows 10 VM. After opening Wireshark, I filtered the traffic to display only ICMP packets. Next, I retrieved the private IP address of the Ubuntu VM and attempted to ping it from the Windows 10 VM, observing the ping requests and replies in Wireshark. Subsequently, I initiated a perpetual ping from the Windows 10 VM to the Ubuntu VM.
</p>
<br>
<br>

<h2>Configuring Inbound Rules in Azure</h2><p>
<img src="https://i.imgur.com/hChy0Hi.jpeg" height="80%" width="80%" alt="Configure Outboud Rules In VM2"/>
<img src="https://i.imgur.com/QHeSUFP.jpeg" height="80%" width="80%" alt="ICMP Traffic Timed Out"/>  
</p>
<p>
 Afterward, I accessed the Network Security Group associated with the Ubuntu VM and disabled incoming ICMP traffic. Upon returning to the Windows 10 VM, I observed the changes in ICMP traffic in Wireshark and the command line ping activity. Once connectivity was verified, I re-enabled ICMP traffic for the Network Security Group. Lastly, I stopped the perpetual ping activity to conclude the analysis by using ctrl + c.
</p>
<br />

<h2>Observing SSH Traffic</h2>
<p>
<img src="https://i.imgur.com/q7I4xtL.jpeg" height="80%" width="80%" alt="SSH Traffic on Wireshark"/>
</p>
<p>
To analyze SSH traffic in Wireshark, I first filtered for SSH traffic. On my Windows 10 VM, initiated an SSH connection to my Ubuntu VM using its private IP address. Once connected, I entered commands such as the username and password in the Linux SSH session. I observed the SSH traffic in Wireshark, which showed the data exchange between the two machines. Finally, I exited the SSH connection by typing 'exit' and pressing [Enter].
</p>
<br />

<h2>Using DHCP to Issue a New IP Adress</h2>
<p>
<img src="https://i.imgur.com/8YBC3N9.jpeg" height="80%" width="80%" alt="Wireshark filter for DHCP traffic"/>
</p>
<p>
To analyze DHCP traffic in Wireshark, first, I filtered for DHCP traffic. From my Windows 10 VM, I then attempt to issued my VM a new IP address using the command `ipconfig /renew`. Finally, I observed the DHCP traffic that appears in Wireshark, indicating the communication involved in obtaining a new IP address.
</p>
<br />

<h2>Observing DNS Traffic</h2>
<p>
<img src="https://i.imgur.com/DIF0Utj.jpeg" height="80%" width="80%" alt="Image displaying DNS traffic"/>
</p>
<p>
In Wireshark, the traffic was filtered to display only DNS traffic. On the Windows 10 virtual machine, the `nslookup` command was used to find the IP addresses for google.com and disney.com. The DNS traffic generated by these queries was then observed in Wireshark.
</p>
<br />

<h2>Observing RDP Traffic</h2>
<p>
<img src="https://i.imgur.com/91MbfPX.jpeg" width="80%" alt="Image showing RDP traffic from remote connection"/>
</p>
<p>
In Wireshark, I set the filter to display only RDP traffic using the command `tcp.port == 3389`. The immediate, non-stop spam of traffic was observed. This continuous traffic was due to the RDP protocol constantly transmitting a live stream from one computer to another, resulting in a steady flow of data being shown regardless of specific user activity.
</p>
<br />

<h2>Lab Cleanup!</h2>
<p>
<img src="https://i.imgur.com/91MbfPX.jpeg" width="80%" alt="Image of an empty resource group in azure"/>
</p>
<p>
After executing all of the commands I made sure to close all of the applications and most importantly delete all of the resource groups created during the lab so I did not waste any resources in Azure. 
</p>
<br />
