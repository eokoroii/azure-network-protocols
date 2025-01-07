<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
For this practice, I explored network traffic to and from Azure Virtual Machines using Wireshark and experimented with Network Security Groups (NSGs) to manage traffic flow. This hands-on lab gave me valuable insight into configuring cloud-based virtual machines and analyzing their network interactions. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop Connection (RDP)
- Command-Line Tools (Bash, PowerShell)
- Network Protocols (SSH, RDP, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

1. Set up Azure Virtual Machines (Windows and Linux).
2. Configure Network Security Groups (NSGs) to define inbound and outbound rules.
3. Connect to the Windows Virtual Machine via RDP and the Linux Virtual Machine via SSH.
4. Install Wireshark on the Windows Virtual Machine to observe and analyze network traffic.
5. Test and analyze network traffic using tools and protocols (ping, DNS requests, HTTP traffic, etc.).
6. Document findings and refine NSG rules to enhance security.

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Wireshark Traffic Capture"/>
</p>
<p>
I captured traffic using Wireshark on the Windows Virtual Machine. The tool provided insights into various protocols, including ICMP, DNS, and HTTP. For instance, I initiated a ping command from the Windows VM to the Linux VM and observed the ICMP packets traveling between the two machines. This demonstrated the communication flow within the Azure network.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="NSG Configuration"/>
</p>
<p>
To secure the environment, I configured NSG rules to allow only necessary traffic. For example, I permitted SSH traffic (port 22) to the Linux VM and RDP traffic (port 3389) to the Windows VM while blocking all other inbound traffic. This setup ensured that only authorized access was granted, reducing potential attack surfaces.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Traffic Analysis"/>
</p>
<p>
Using Wireshark, I analyzed HTTP traffic by accessing a web server hosted on the Linux VM. I observed the TCP handshake process and inspected the packets to verify the data flow. This exercise enhanced my understanding of web traffic and how it can be monitored for security and troubleshooting purposes.
</p>
<br />

<h2>Conclusion</h2>
This lab was an excellent opportunity to gain practical experience with cloud-based virtual machines, network traffic analysis, and security configuration using NSGs. By observing traffic in Wireshark and refining NSG rules, I developed a deeper understanding of managing and securing network environments in Azure. These skills are crucial for IT professionals working with cloud infrastructure and network security.

