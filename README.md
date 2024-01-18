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

- Inspect DNS A-Records on the server (hostname to IP address mappings)
- Create some of our own A-records on the server and observe them from the client
- Delete records from the serve and inspect/clear the client DNS cache to gain understanding
- Touch on "CNAME" records (mapping one name to another name)

<h2>Actions and Observations</h2>

<p>

- From Client virtual machine try to ping “mainframe” notice that it fails.
- Nslookup “mainframe” notice that it fails becuase there is no DNS record
- Create a DNS A-record on the Domain virual machine for “mainframe” and have it point to the Domain’s Private IP address
- Go back to Client-1 and try to ping it. Observe that it works

</p>
<p>
<img src="https://github.com/vannessacates/azure-network-protocols/assets/140145473/944c7f0a-7293-4f16-838d-0e756dd31d0e"/>
</p>
<p>
<img src="https://github.com/vannessacates/azure-network-protocols/assets/140145473/0d4be3a4-c8c6-49df-89e6-9adbfd7e9af3"/>
</p>
<p>
<img src="https://github.com/vannessacates/azure-network-protocols/assets/140145473/5c778819-4ad1-4f22-82a5-e134333f2a8a"/>
</p>
<br />

<p>

- Go back to the Domain VM and change mainframe’s record address to 8.8.8.8
- Go back to the Client VM and ping “mainframe” again. Observe that it still pings the old address
- Observe the local dns cache (ipconfig /displaydns)
- Flush the DNS cache (ipconfig /flushdns). Observe that the cache is empty
- Attempt to ping “mainframe” again. Observe the address of the new record is showing up

</p>
<p>
<img src="https://github.com/vannessacates/azure-network-protocols/assets/140145473/d0a73005-6dff-4098-86f7-0d181d495e20"/>
</p>
<p>
<img src="https://github.com/vannessacates/azure-network-protocols/assets/140145473/ff6f2925-9879-45c4-8742-00e45bff4e0d"/>
</p>
<p>
<img src="https://github.com/vannessacates/azure-network-protocols/assets/140145473/6c2d8c5f-e051-4228-bf81-7e2addf5d718"/>
</p>
<p>
<img src="https://github.com/vannessacates/azure-network-protocols/assets/140145473/8cce6261-c77e-440f-8831-dcd5887f7dd5)"/>
</p>
<p>
<img src="https://github.com/vannessacates/azure-network-protocols/assets/140145473/1d4075a5-116d-42ed-aab4-7adcb461d712"/>
</p>
<br />


<p>

- Go back to the Domain VM and create a CNAME record that points the host “search” to “www.google.com”
- Go back to the Client VM and attempt to ping “search”, observe the results of the CNAME record
- On Client VM, nslookup “search”, observe the results of the CNAME record

</p>
<p>
<img src="https://github.com/vannessacates/azure-network-protocols/assets/140145473/22758a65-252d-4953-b9c3-9e10d469fd20"/>
</p>
<p>
<img src="https://github.com/vannessacates/azure-network-protocols/assets/140145473/954cdcbd-e6c1-4570-9f1a-498ba760e594"/>
</p>
<br />
