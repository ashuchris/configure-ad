<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>How To Set Up Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>Deployment and Configuration Steps</h2>

- Create A Resource group and Install Windows Server 2022 VM
- RDP into the Windows server and Install Active Directory Domain Services
- Make the server the Domain Controler
- Create Organisation units OUs) and some users
- Create a Win10 client VM and add the WIN10 client to the domain
- Create many users using PowerShell scripting 
- RDP into the Win10 VM using user credentials created 

<h2>Create A Resource group and Install Windows Server 2022 VM</h2>

<p>
First We have to create a resource group, the resource group acts as a home for our virtual machines. On the Azure portal dashboard click on the resource group.
</p>
<p>
<img src="https://i.imgur.com/DExp5Lz.png"/>
</p>

<br />

<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<p>
<img src="https://i.imgur.com/DExp5Lz.png"/>
</p>

<br />

<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<p>
<img src="https://i.imgur.com/DExp5Lz.png"/>
</p>

<br />
