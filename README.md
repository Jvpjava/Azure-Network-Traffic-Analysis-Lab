# Azure-Network-Traffic-Analysis-Lab
Azure networking lab analyzing ICMP, SSH, DNS, DHCP, and RDP traffic using Wireshark.

<img src="images/windows-azure-cloud.png" width="700">

## Overview

This project demonstrates how to observe and analyze network traffic using **Wireshark** inside a cloud environment hosted on **Microsoft Azure**. Virtual machines were created inside the same virtual network to generate traffic and analyze different network protocols.

The goal of the lab was to understand how protocols such as **ICMP, SSH, DHCP, DNS, and RDP** behave on a network and how firewall rules affect connectivity.

---

# Technologies Used

* Microsoft Azure
* Windows 10 Virtual Machine
* Ubuntu Linux Virtual Machine
* Wireshark
* Remote Desktop Protocol (RDP)
* PowerShell / Command Prompt

---

# Environment Setup

The lab environment was built using Microsoft Azure.

Infrastructure components:

* **Resource Group**
* **Virtual Network (VNet)**
* **Subnet**
* **Windows 10 Virtual Machine**
* **Ubuntu Linux Virtual Machine**

Both virtual machines were placed inside the **same virtual network and subnet** to allow communication between them. 

---

# Step 1 — Creating Virtual Machines

The first step was deploying cloud infrastructure in Azure.

Actions performed:

1. Created a **Resource Group** in Azure.
2. Created a **Windows 10 Virtual Machine**.
3. Created an **Ubuntu Linux Virtual Machine**.
4. Ensured both VMs were connected to the **same Virtual Network and Subnet**. 

This allowed the machines to communicate with each other using private IP addresses.

<img src="images/1. Resource-Group.jpg" width="700">
<img src="images/2. VM's.jpg" width="700">

---

# Step 2 — Capturing Network Traffic with Wireshark

After connecting to the Windows VM using **Remote Desktop**, Wireshark was installed to monitor traffic.

Steps performed:

1. Connected to the Windows VM using **Remote Desktop Protocol (RDP)**.
2. Installed **Wireshark** on the Windows VM.
3. Started packet capture to observe live network traffic. 

Wireshark was used to analyze different types of network packets generated during the lab.

<img src="images/3. RDP.jpg" width="700">
<img src="images/4. Download.jpg" width="700">
<img src="images/5. WireShark Packet Capture.jpg" width="700">


---

# Step 3 — Observing ICMP Traffic

To generate ICMP traffic:

1. Retrieved the **private IP address of the Ubuntu VM**.
2. Sent ping requests from the Windows VM to the Ubuntu VM.
3. Filtered Wireshark using the **ICMP protocol filter**.
4. Observed ping request and reply packets.

This demonstrated how ICMP is used for **connectivity testing and network diagnostics**. 

<img src="images/6. ICMP Traffic Wireshark.jpg" width="700">
<img src="images/7. PS Ping Wireshark Monitor.jpg" width="700">
<img src="images/7. PS Ping.png" width="700">


---

# Step 4 — Configuring a Firewall (Network Security Group)

A firewall rule was applied to control traffic between the machines.

Actions performed:

1. Initiated a continuous ping from Windows VM to Ubuntu VM.
2. Modified the **Network Security Group (NSG)** attached to the Ubuntu VM.
3. Blocked inbound **ICMP traffic**.
4. Observed the ping requests begin to fail.
5. Re-enabled ICMP traffic and confirmed connectivity returned. 

This demonstrated how firewall rules affect network communication.

<img src="images/8. Firewall PS Ping.jpg" width="700">
<img src="images/9. Firewall Blocks ICMP traffic.jpg" width="700">
<img src="images/10. Wireshark Monitors firewall blocking ICMP Traffic.jpg" width="700">
<img src="images/11. Re-enable ICMP Traffic - ping the server.jpg" width="700">

---

# Step 5 — Observing SSH Traffic

Next, secure remote access traffic was generated.

Steps performed:

1. Started packet capture in Wireshark.
2. Filtered for **SSH traffic**.
3. Connected to the Ubuntu VM using SSH from the Windows VM.
4. Ran commands inside the Linux terminal.

This allowed observation of encrypted SSH traffic packets. 

<img src="images/12. SSH into the ubuntu server through windows vm.jpg" width="700">
<img src="images/13. Monitor ssh traffic from windows vm to ubuntu server.jpg" width="700">

---

# Step 6 — Observing DHCP Traffic

To observe DHCP activity:

1. Filtered Wireshark for **DHCP packets**.
2. Ran the command:

```
ipconfig /renew
```

This forced the system to request a new IP address and generated DHCP traffic visible in Wireshark. 

<img src="images/14. Observing dhcp traffic.png" width="700">

---

# Step 7 — Observing DNS Traffic

DNS traffic was analyzed by performing domain lookups.

Command used:

```
nslookup google.com
nslookup disney.com
```

Wireshark showed DNS queries and responses resolving domain names to IP addresses. 

<img src="images/15. Observing dns traffic.png" width="700">
<img src="images/15. Observing dns traffic 2.png" width="700">

---

# Step 8 — Observing RDP Traffic

Wireshark was used to filter traffic using:

```
tcp.port == 3389
```

This displayed continuous Remote Desktop traffic between systems because RDP constantly streams screen updates and user input. 

<img src="images/16. Observing RDP Traffic 1.png" width="700">

---

# Skills Demonstrated

* Cloud infrastructure deployment
* Virtual machine networking
* Packet analysis with Wireshark
* Firewall configuration using Network Security Groups
* Network protocol analysis (ICMP, SSH, DHCP, DNS, RDP)
* Remote administration using RDP and SSH

---

---



