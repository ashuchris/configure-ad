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
We are going to name the resource group AzureAD. I choose Southeast Asia region, you can choose whatever region you like and click on "review and create" and "create" to create your resource group. 
</p>
<p>
<img src="https://i.imgur.com/oDTjU61.png"/>
</p>

<br />

<p>
Now we have to create our Windows server virtual machine. on the search bar, type "virtual machines" and click on virtual machines
</p>
<p>
<img src="https://i.imgur.com/NOJFXTw.png"/>
</p>

<br />

<p>
Choose the same resource group we created, and give the virtual machine a name. I will be naming mine Azure-AD-Lab. choose a region, choose the Windows server 2022 datacenter Azure edition 
</p>
<p>
<img src="https://i.imgur.com/ipskruz.png"/>
</p>

<br />

<p>
Choose a size with at least 2 VCPUs as this will increase the performance of the VM. Give the account a username and a password and click on next 
</p>
<p>
<img src="https://i.imgur.com/6klxmjN.png"/>
</p>

<br />

