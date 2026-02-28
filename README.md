<p align="center">
  <img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo" />
</p>

<h1>osTicket - Post-Install Configuration</h1>
This tutorial outlines the post-install configuration of the open-source help desk ticketing system osTicket.<br />

<ul>
  <li>Microsoft Azure (Virtual Machines/Compute)</li>
  <li>Remote Desktop</li>
  <li>Internet Information Services (IIS)</li>
</ul>

<h2>Operating Systems Used</h2>

<ul>
  <li>Windows 10 (21H2)</li>
</ul>

<h2>Post-Install Configuration Objectives</h2>

<ul>
  <li>Creating a virtual machine with Windows Server (will act as a domain controller)</li>
  <li>Creating a virtual machine with Windows Desktop (will act as a client machine)</li>
  <li>Configuring IP addresses and DNS</li>
  <li>Connecting remotely to virtual machines and checking connectivity</li>
</ul>

<h2>Configuration Steps</h2>

<p>
  <img
    src="https://github.com/tabrizcyber/images/blob/main/VirtualMachines.JPG"
    height="80%"
    width="80%"
    alt="Disk Sanitization Steps"
  />
</p>

<p>
  <i>
    <strong>
      Here, I've created two virtual machines — ADVM and ClientPC. First, Windows Server 2022
      has been installed on ADVM so that we can use this machine as a domain controller. On the
      other hand, Windows Enterprise 2022 has been installed on ClientPC so that we can use this
      machine as a standard client PC.
    </strong>
  </i>
</p>

<p>
  <img
    src="https://github.com/tabrizcyber/images/blob/main/VirtualNetworks.JPG"
    height="80%"
    width="80%"
    alt="Disk Sanitization Steps"
  />
</p>

<p>
  <i>
    <strong>
      I didn’t create new virtual networks, since I already had virtual networks that were
      created automatically from previous virtual machines in Azure. However, I used the same
      virtual network for both machines in order to manage connectivity between them.
    </strong>
  </i>
</p>

<p>
  <img
    src="https://github.com/tabrizcyber/images/blob/main/staticIP.JPG"
    height="80%"
    width="80%"
    alt="Disk Sanitization Steps"
  />
</p>

<p>
  <i>
    <strong>
      I changed the public IP of ADVM from dynamic to static, just in case, since I will be using
      ADVM as a domain controller and its private IP will act as the DNS server for ClientPC.
    </strong>
  </i>
</p>

<p>
  <img
    src="https://github.com/tabrizcyber/images/blob/main/ClienDNS.JPG"
    height="80%"
    width="80%"
    alt="Disk Sanitization Steps"
  />
</p>

<p>
  <i>
    <strong>
      As mentioned, I used ADVM’s IP address as the DNS server for ClientPC, so I copied the IP
      and added it to the DNS settings of ClientPC.
    </strong>
  </i>
</p>

<p>
  <img
    src="https://github.com/tabrizcyber/images/blob/main/disableFirewall.PNG"
    height="80%"
    width="80%"
    alt="Disk Sanitization Steps"
  />
</p>

<p>
  <i>
    <strong>
      Additionally, for the purpose of this lab, the firewall was disabled to allow ADVM to
      accept ping requests and connections from ClientPC.
    </strong>
  </i>
</p>

<p>
  <img
    src="https://github.com/tabrizcyber/images/blob/main/pingADVM.PNG"
    height="80%"
    width="80%"
    alt="Disk Sanitization Steps"
  />
</p>

<p>
  <i>
    <strong>
      Here, I signed in to ClientPC to verify connectivity with ADVM.
    </strong>
  </i>
</p>

<p>
  <img
    src="https://github.com/tabrizcyber/images/blob/main/ipconfigAll.PNG"
    height="80%"
    width="80%"
    alt="Disk Sanitization Steps"
  />
</p>

<p>
  <i>
    <strong>
      This is the output of the command <code>ipconfig /all</code>.
    </strong>
  </i>
</p>

<p>
  <img
    src="https://github.com/tabrizcyber/images/blob/main/installingAD.PNG"
    height="80%"
    width="80%"
    alt="Disk Sanitization Steps"
  />
</p>

<p>
  <i>
    <strong>
      Here I'm installing ad within the network manager, which is straight forward process. We just have to create new forest, and I called mine as a mydomain.com.
    </strong>
  </i>
</p>

<p>
  <img
    src="https://github.com/tabrizcyber/images/blob/main/usersAD.PNG"
    height="80%"
    width="80%"
    alt="Disk Sanitization Steps"
  />
</p>

<p>
  <i>
    <strong>
      Here I've create few folders as _EMPLOYEE and etc. After I created new user Tabriz Glanton and gave added him to the "Admin Users " group to give me permissions to change certain things both in domain controller which is ADVM and all other machines. For example, we'll add ClientPC to the domain as well.
    </strong>
  </i>
</p>



<p>
  <img
    src="https://github.com/tabrizcyber/images/blob/main/ipconfigAll.PNG"
    height="80%"
    width="80%"
    alt="Disk Sanitization Steps"
  />
</p>

<p>
  <i>
    <strong>
      Here I'm joining the ClientPC to the domain and in order to do that we can to sytems -> about -> change this pc name(advanced) and after we can do the steps as shown in the picture.
    </strong>
  </i>
</p>

<p>
  <img
    src="https://github.com/tabrizcyber/images/blob/main/joined%20pc.PNG"
    height="80%"
    width="80%"
    alt="Disk Sanitization Steps"
  />
</p>

<p>
  <i>
    <strong>
     Here I've logged in ADVM and we can see that the clientPC has been added to domain
    </strong>
  </i>
</p>

<p>
  <img
    src="https://github.com/tabrizcyber/images/blob/main/ipconfigAll.PNG"
    height="80%"
    width="80%"
    alt="Disk Sanitization Steps"
  />
</p>

<p>
  <i>
    <strong>
      Here I'm joining the ClientPC to the domain and in order to do that we can to sytems -> about -> change this pc name(advanced) and after we can do the steps as shown in the picture.
    </strong>
  </i>
</p>

<p>
  <img
    src="https://github.com/tabrizcyber/images/blob/main/ipconfigAll.PNG"
    height="80%"
    width="80%"
    alt="Disk Sanitization Steps"
  />
</p>

<p>
  <i>
    <strong>
      Here I'm joining the ClientPC to the domain and in order to do that we can to sytems -> about -> change this pc name(advanced) and after we can do the steps as shown in the picture.
    </strong>
  </i>
</p>
