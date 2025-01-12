<p align="center">
  <img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Azure Virtual Machines & Wireshark Network Analysis Lab</h1>

<h2>Project Summary</h2>
<p>
  This lab demonstrates how I created Windows and Linux virtual machines in Microsoft Azure, 
  configured Network Security Groups (NSGs), and captured various types of network traffic 
  (ICMP, SSH, DHCP, DNS, RDP/TLS) using Wireshark. These hands-on tasks helped me understand 
  cloud-based infrastructure and secure data transmission in real time.
</p>

<ul>
  <li><strong>Languages Used:</strong> PowerShell (ping, ipconfig), Bash (ls, whoami)</li>
  <li><strong>Environments:</strong> 
    <ul>
      <li>Azure Portal (Resource Groups, VMs)</li>
      <li>Windows 10 VM (RDP access, Wireshark)</li>
      <li>Linux (Ubuntu 22.04) VM (SSH connections)</li>
    </ul>
  </li>
  <li><strong>Technologies/Services:</strong>
    <ul>
      <li>Azure Resource Groups & Virtual Networks</li>
      <li>Azure Virtual Machines (Windows & Linux)</li>
      <li>Wireshark for packet capture</li>
      <li>RDP (Remote Desktop Protocol)</li>
      <li>SSH (Secure Shell)</li>
    </ul>
  </li>
</ul>

<hr />

<h2>Steps & Screenshots</h2>
<ol>
  <li>
    <strong>Create an Azure Resource Group</strong><br />
    I used the Azure portal to create a new Resource Group named <code>RG-Network-Activities</code> in East US 2. 
    Organizing resources under one group makes it easier to manage and monitor costs.
    <br /><br />
      <p align="center">
      <img src="https://i.imgur.com/KvGt4XR.png" alt="Resource Group Creation" width="600" />
      </p>
  </li>
  <br />

  <li>
    <strong>Deploy Windows & Linux VMs</strong><br />
    I deployed a Windows 10 VM and an Ubuntu 22.04 VM within the same resource group to simulate a real-world, multi-OS environment. 
    This setup allowed me to test cross-platform network connectivity.
    <br /><br />
    <p align="center">
    <img src="https://i.imgur.com/7odeCMv.png" alt="Azure VM List" width="600" />
    </p>
  </li>
  <br />

  <li>
    <strong>Remote Desktop to Windows VM & Wireshark Setup</strong><br />
    After connecting via RDP, I installed Wireshark on the Windows VM to capture and analyze inbound and outbound traffic. 
    This helped me visualize how different protocols operate in real time.
    <br /><br />
    <p align="center">
    <img src="https://i.imgur.com/t0oOwF7.png" alt="RDP Connection" width="600" />
    <br />
    <img src="https://i.imgur.com/zrmdYWL.png" alt="Wireshark Installation" width="600" />
    </p>
  </li>
  <br />

  <li>
    <strong>Testing Connectivity (ICMP)</strong><br />
    To confirm basic connectivity, I pinged the Linux VM and external sites like google.com. 
    Wireshark’s ICMP capture allowed me to confirm successful packet exchanges.
    <br /><br />
    <p align="center">
    <img src="https://i.imgur.com/mynoe4s.png" alt="ICMP Traffic in Wireshark" width="600" />
    </p>
  </li>
  <br />

  <li>
    <strong>Configuring NSG Rules</strong><br />
    I fine-tuned the inbound rules on each VM to either permit or block ICMP and SSH. 
    Observing blocked pings (ICMP) in Wireshark highlighted the impact of network security settings.
    <br /><br />
    <p align="center">
    <img src="https://i.imgur.com/3Y9AuVN.png" alt="NSG Rules" width="600" />
    <br />
    <img src="https://i.imgur.com/e9mDlct.png" alt="ICMP Blocked" width="600" />
    </p>
  </li>
  <br />

  <li>
    <strong>SSH into Linux VM</strong><br />
    From the Windows VM, I used PowerShell to SSH into the Linux VM, capturing the encrypted session in Wireshark. 
    This demonstrated how SSH secures data in transit.
    <br /><br />
    <p align="center">
    <img src="https://i.imgur.com/bqv7iIo.png" alt="SSH Capture in Wireshark" width="600" />
    </p>
  </li>
  <br />

  <li>
    <strong>DHCP & DNS Analysis</strong><br />
    I ran <code>ipconfig /renew</code> on the Windows VM to visualize the DHCP request and response cycle, 
    then performed <code>nslookup</code> to observe DNS queries and answers in Wireshark.
    <br /><br />
    <p align="center">
    <img src="https://i.imgur.com/XcZA6qd.png" alt="DHCP in Wireshark" width="600" />
    <br />
    <img src="https://i.imgur.com/SLbSrRv.png" alt="DNS in Wireshark" width="600" />
    </p>
  </li>
  <br />

  <li>
    <strong>Analyzing RDP/TLS Traffic</strong><br />
    Lastly, I filtered Wireshark by port 3389 to examine the encrypted RDP traffic, 
    confirming that remote desktop sessions are secured with TLS.
    <br /><br />
    <p align="center"> 
    <img src="https://i.imgur.com/Q0uOA3q.png" alt="RDP/TLS in Wireshark" width="600" />
    </p>
  </li>
</ol>

<hr />

<h2>Conclusion</h2>
<p>
  Through this lab, I gained valuable insights into deploying Azure Virtual Machines, setting up Network Security Groups, 
  and analyzing traffic with Wireshark. Observing how protocols like ICMP, SSH, DHCP, DNS, and RDP behave in a cloud 
  environment has strengthened my understanding of both networking and security best practices.
</p>
