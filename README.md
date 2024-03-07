![image](https://github.com/CamdenBodden/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/114665835/5deaba4b-492e-4f5c-862a-2a86fb8a8530)



<h1>NSG and Network Protocols Project</h1>

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Firewall and Network Security Groups
- Wireshark

<h2>Operating Systems Used </h2>

- Windows 11
- Ubuntu Linux

<h2>Project Overview</h2>
I will be using Azure to create a virtual network that has a Windows virtual machine and a Ubuntu Linux virtual machine. I will be performing some activities in the network between the virtual machines. I will use Wireshark a network analyzer to observe the interactions across the network. I will also change some rules on the firewall to observe the impact that it has across the network.
<p>
  
![image](https://github.com/CamdenBodden/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/114665835/9a7e7a9a-08f0-4a68-b72b-a945972c4aaa)

</p>

<h2>Virtual Machine Creation</h2>
I created a resource group that acted as a repository for this project and that holds both virtual machines.
<p>
  
![image](https://github.com/CamdenBodden/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/114665835/09639221-5f02-4139-b25f-1c6fad464f41)

</p>

I created the virtual machines one with Ubuntu Linux and one with Windows.
<p>
  
![image](https://github.com/CamdenBodden/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/114665835/9bdecac4-6a60-4a51-8c11-ea91cc69bd89)

</p>

<h2>Observe ICMP Traffic</h2>
I used Remote Desktop to connect to the Windows 11 virtual machine
<p>
  
![image](https://github.com/CamdenBodden/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/114665835/1159704f-a7b4-4873-98fc-9b782dccc053)

</p>

On the Windows 11 virtual machine I downloaded and installed Wireshark
<p>
  
![image](https://github.com/CamdenBodden/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/114665835/3cbe993a-ca87-47c1-a074-b8764f6d7b75)

</p>

I used the command line to ping the private IP address of the Linux virtual machine
<p>
  
![image](https://github.com/CamdenBodden/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/114665835/6d9a8e36-a07e-458e-a6c2-afc69644995c)

</p>

I used Wireshark to filter for ICMP traffic and observed the traffic between the two computers after pinging the Linux Virtual Machine
<p>
  
![image](https://github.com/CamdenBodden/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/114665835/3568bc54-6a5f-49c0-b00a-3e6c2a5d632f)

</p>

I pinged www.google.com and used Wireshark to observe the interaction
<p>
  
![image](https://github.com/CamdenBodden/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/114665835/c495646d-f9b1-46b9-83d5-7e9103ec4c70)

</p>

I issued a perpetual ping from the Windows virtual machine to the Linux virtual machine
<p>
  
![image](https://github.com/CamdenBodden/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/114665835/a77aa5e2-0759-4d68-8efa-2902328596a6)

</p>

I then disabled the inbound ICMP traffic on the Network Security Group of the Linux virtual machine
<p>
  
![image](https://github.com/CamdenBodden/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/114665835/1e4f9bcf-6af5-4928-ab55-c8460a2d55a1)

</p>

Disabling the inbound ICMP traffic blocked the ping traffic and caused the Linux virtual machine not to respond. In Windows Virtual Machine command line the request for a ping reply from Linux began to time out.
<p>
  
![image](https://github.com/CamdenBodden/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/114665835/b17bee9f-bdda-4fe9-9b19-2be9742e1092)

</p>
<h2>Observe SSH Traffic</h2>
From the Windows virtual machine command line I used SSH to connect to the Linux virtual machine
<p>
  
![image](https://github.com/CamdenBodden/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/114665835/d83bdfa3-076f-4216-85af-a685a65e674f)

</p>

Then I filtered to view ssh (port 22) traffic only in Wireshark.
<p>
  
![image](https://github.com/CamdenBodden/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/114665835/11da5e6f-bc07-4a70-8aad-b05c9b080cdd)

</p>

<h2>Observe DHCP Traffic</h2>
The computer uses DHCP to automatically assign an IP address so when I used the command (ipconfig /renew) it issued the Windows virtual machine a new IP address
<p>
  
![image](https://github.com/CamdenBodden/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/114665835/f61683fc-17e7-4860-9ece-4d4412e63d68)

</p>

I filtered to view DHCP (port 67) traffic only in Wireshark
<p>
  
![image](https://github.com/CamdenBodden/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/114665835/742c8959-508b-405f-8664-e81386e8d1c2)

</p>

<h2>Observe DNS Traffic</h2>
I used nslookup to see what google.com and Disney.com’s IP addresses were
<p>
  
![image](https://github.com/CamdenBodden/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/114665835/15758817-662b-43f4-98a4-89bec29a0635)

</p>

I filtered to view DNS (port 53) traffic only in Wireshark
<p>
  
![image](https://github.com/CamdenBodden/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/114665835/01976c9a-b88e-423f-8bc7-da7bd87853b4)

</p>

<h2>Observe RDP Traffic</h2>
I filtered to see RDP (port 3389) traffic only in Wireshark. Wireshark displays an immediate nonstop spam of RDP traffic because we are connected to the virtual machine with remote desktop. It is showing all the traffic from my personal computer, the virtual machine, and Azure servers.
<p>
  
![image](https://github.com/CamdenBodden/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/114665835/1f1f98fa-d3ac-4467-8fd9-f90686b256ff)

</p>
