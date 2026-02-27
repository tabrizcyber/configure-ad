<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Post-Install Configuration</h1>
This tutorial outlines the post-install configuration of the open-source help desk ticketing system osTicket.<br />



- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>Post-Install Configuration Objectives</h2>

- Creating Virtual Machine with Windows Server(Will act as a domain controller)
- Creating Virtual Machine with Windows Desktop(Will act as a client machine)
- Configuring IP addresses and DNS
- Connect remotely to virtual machines and check the connectivity

<h2>Configuration Steps</h2>

<p>
<img src="https://github.com/tabrizcyber/images/blob/main/VirtualMachines.JPG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p><i><strong>Here I've created two virtual machines - ADVM and ClientPC. Primarily, Windows Server 2022 has been installed to ADVM so that we can use the machine as a domain controller. On the other hand, Windows Enterprise 2022  has been installed to ClientPC, so that we can use the machine as some random client PC. </strong></i></p>
<p>

<p>
<img src="https://github.com/tabrizcyber/images/blob/main/VirtualNetworks.JPG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p><i><strong>I haven't created new virtual networks, since I had virtual networks which have been created automatically from the previous virtual machines in Azure. However, I used the same virtual network for both machines to be able to manage connectivity between the machines.</strong></i></p>
<p>

<p>
<img src="https://github.com/tabrizcyber/images/blob/main/staticIP.JPG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p><i><strong>I've changed the public ip of ADVM from dynamic to static just in case, since I'll be using ADVM as a domain controller and the private ip of ADVM will act as a DNS for ClientPC.</strong></i></p>
<p>

<p>
<img src="https://github.com/tabrizcyber/images/blob/main/ClienDNS.JPG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p><i><strong>I've said that I would use ADVM public IP address as a DNS for ClientPC, so I copied the IP and added it to DNS of ClientPC </strong></i></p>
<p>

<p>
<img src="https://github.com/tabrizcyber/images/blob/main/disableFirewall.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p><i><strong>Also we have to disable firewall in case of the lab to let ADVM accept ping and requests from ClientPC </strong></i></p>
<p>

<p>
<img src="https://github.com/tabrizcyber/images/blob/main/pingADVM.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p><i><strong>Here I'm signing in to ClientPC to check the connectivity to ADVM </strong></i></p>
<p>

<p>
<img src="https://github.com/tabrizcyber/images/blob/main/ipconfigAll.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p><i><strong>And this is the outcome of the command IPCONFIG /ALL </strong></i></p>
<p>
