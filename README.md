<h1>Azure Virtual Machines & Wireshark Network Analysis</h1>

<h2>Project Summary</h2>
<p>
  This lab shows how I created Windows and Linux virtual machines in Microsoft Azure, 
  configured Network Security Groups (NSGs), and captured various types of network traffic 
  (ICMP, SSH, DHCP, DNS, RDP/TLS) using Wireshark. By walking through these steps,
  I gained hands-on experience with cloud deployment, secure connectivity, and real-time packet analysis.
</p>

<ul>
  <li><strong>Environments:</strong>
    <ul>
      <li>Azure Portal: Resource Groups, VMs</li>
      <li>Windows 10 VM (RDP access, Wireshark installed)</li>
      <li>Linux (Ubuntu 22.04) VM (SSH connections)</li>
    </ul>
  </li>
  <li><strong>Technologies:</strong>
    <ul>
      <li>NSGs, Virtual Networks</li>
      <li>Wireshark for traffic capture</li>
      <li>RDP (port 3389), SSH (port 22)</li>
      <li>ICMP, DHCP, DNS, TLS</li>
    </ul>
  </li>
</ul>

<hr />

<h2>Steps & Screenshots</h2>
<ol>
  <li>
    <strong>Create an Azure Resource Group</strong><br />
    I logged into the Azure portal and created a new Resource Group named <code>RG-Network-Activities</code>.
    <br /><br />
    <p align="center">
      <img src="https://i.imgur.com/0J3aNzz.png" alt="Resource Group Creation" width="600" />
      <br />
      <em>Figure 1.1 – Creating a Resource Group in Azure.</em>
    </p>
  </li>
  <br />

  <li>
    <strong>Deploy a Windows 10 VM</strong><br />
    Next, I deployed a Windows 10 VM in the same region. 
    <ul>
      <li>Chose the appropriate size (e.g., Standard B1s)</li>
      <li>Enabled RDP (port 3389) under inbound rules</li>
    </ul>
    <p align="center">
      <img src="https://i.imgur.com/twwJSC4.png" alt="Windows VM creation" width="600" />
      <br />
      <em>Figure 1.2 – Windows VM basics.</em>
    </p>
    After deployment, I noted the Public IP for later remote access.
  </li>
  <br />

  <li>
    <strong>Deploy a Linux (Ubuntu) VM</strong><br />
    I created a separate Ubuntu 22.04 VM to test cross-platform connectivity:
    <ul>
      <li>Enabled SSH (port 22) under inbound rules</li>
      <li>Chose a lightweight size (e.g., Standard B1s) for cost efficiency</li>
    </ul>
    <p align="center">
      <img src="https://i.imgur.com/SrHc7KH.png" alt="Ubuntu VM creation" width="600" />
      <img src="https://i.imgur.com/I80wgDG.png" alt="Ubuntu VM creation" width="600" />
      <br />
      <em>Figure 1.3 – Linux VM in the same resource group.</em>
    </p>
  </li>
  <br />

  <li>
    <strong>Configure Network Security Groups (NSGs)</strong><br />
    Under each VM’s <em>Networking</em> blade, I refined inbound rules to allow or block specific traffic:
    <ul>
      <li>Confirmed RDP (3389) for Windows VM</li>
      <li>Confirmed SSH (22) for Linux VM</li>
      <li>Optionally allowed/blocked ICMP by adding a custom rule</li>
    </ul>
    <p align="center">
      <img src="https://i.imgur.com/rNs9PkR.png" alt="Network Security Groups" width="600" />
      <br />
      <em>Figure 1.4 – Reviewing inbound rules in NSG.</em>
    </p>
  </li>
  <br />

  <li>
    <strong>RDP into Windows VM & Install Wireshark</strong><br />
    From my local machine, I used Remote Desktop to log into the Windows VM. Then I downloaded 
    and installed Wireshark. This is crucial for capturing real-time network traffic.
    <br /><br />
    <p align="center">
      <img src="https://i.imgur.com/uQN35ca.png" alt="RDP Connection" width="600" />
      <br />
      <em>Figure 1.5 – Remoting into the Windows VM.</em>
      <br /><br />
      <img src="https://i.imgur.com/7kYHzoq.png" alt="Wireshark Installation" width="600" />
      <br />
      <em>Figure 1.6 – Installing Wireshark.</em>
    </p>
  </li>
  <br />

  <li>
    <strong>ICMP (Ping) Traffic Capture</strong><br />
    I opened Wireshark on the Windows VM, started a capture on the main network interface, 
    then pinged both the Linux VM and <code>google.com</code>. 
    <br /><br />
    <p align="center">
      <img src="https://i.imgur.com/tMkfAKi.png" alt="ICMP Capture" width="600" />
      <br />
      <em>Figure 1.7 – Observing ICMP echo requests and replies.</em>
    </p>
  </li>
  <br />

  <li>
    <strong>SSH to Linux VM & Analyze Encryption</strong><br />
    Next, from the Windows VM’s PowerShell, I ran <code>ssh user@<em>LinuxVM_IP</em></code>. 
    Wireshark shows encrypted SSH packets on port 22.
    <br /><br />
    <p align="center">
      <img src="https://i.imgur.com/8oqwJLK.png" alt="SSH in Wireshark" width="600" />
      <br />
      <em>Figure 1.8 – SSH traffic captured as encrypted packets.</em>
    </p>
  </li>
  <br />

  <li>
    <strong>DHCP & DNS Analysis</strong><br />
    I renewed the IP lease using <code>ipconfig /renew</code> on the Windows VM to see DHCP discover/offer/ack traffic. 
    Then I ran <code>nslookup</code> to capture DNS queries and responses.
    <br /><br />
    <p align="center">
      <img src="https://i.imgur.com/PNShEwL.png" alt="DHCP Flow" width="600" />
      <br />
      <em>Figure 1.9 – DHCP handshake sequence in Wireshark.</em>
      <br /><br />
      <img src="https://i.imgur.com/1HmASlm.png" alt="DNS Queries" width="600" />
      <br />
      <em>Figure 1.10 – DNS queries and responses.</em>
    </p>
  </li>
  <br />

  <li>
    <strong>RDP/TLS Traffic</strong><br />
    Finally, I filtered Wireshark by <code>tcp.port == 3389</code> to examine the encrypted RDP session. 
    This confirmed RDP is encapsulated via TLS for security.
    <br /><br />
    <p align="center">
      <img src="https://i.imgur.com/EtskZte.png" alt="RDP TLS" width="600" />
      <br />
      <em>Figure 1.11 – Encrypted RDP session traffic in Wireshark.</em>
    </p>
  </li>
</ol>

<hr />

<h2>Conclusion</h2>
<p>
  By provisioning two Azure VMs (Windows and Linux), tweaking NSG rules, and using Wireshark, 
  I gained practical insight into how different protocols—ICMP, SSH, DHCP, DNS, and RDP—look on the wire. 
  This lab illustrates the importance of secure connectivity, network observability, and 
  best practices for cloud-based infrastructure.
</p>
