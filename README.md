<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>How To Set Up Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of Active Directory within Azure Virtual Machines.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute](https://youtu.be/hFMQYR5wpyQ)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines)
- Remote Desktop
- Active Directory Domain Services
- PowerShell
- DNS

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (22H2)

<h2>Deployment and Configuration Steps</h2>

- Create A Resource group and Install Windows Server 2022 VM
- RDP into the Windows server and Install Active Directory Domain Services
- Make the server the Domain Controler
- Create Organisation units OUs) and some users
- Create a Win10 client VM add the WIN10 client to the domain
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
We are going to name the resource group AzureAD. I chose Southeast Asia region, you can choose whatever region you like and click on "review and create" and "create" to create your resource group. 
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

<p>
Skip the disk section and on the networking section, give your virtual network a name and leave the default value of the subnet
<p>
<img src="https://i.imgur.com/01r0tdE.png"/>
</p>

<br />

<p>
Click on review and create and then click on create to deploy the VM. It does take sometime to deploy. It is now time to RDP into the windows server.
</p>
<p>
<img src="https://i.imgur.com/lL2HHwH.png"/>
</p>

<br />

<h2>RDP into the Windows server </h2>

<p>
Copy the public Ip address of the Windows server 
</p>
<p>
<img src="https://i.imgur.com/EH5stot.png"/>
</p>

<br />

<p>
  click on the search icon and search for remote desktop and run it.
</p>
<p>
<img src="https://i.imgur.com/yyko8jL.png"/>
</p>

<br />

<p>
  paste in the public IP address of the server VM and click on connect.
</p>
<p>
<img src="https://i.imgur.com/LFhQZaO.png"/>
</p>

<br />

<p>
  log in with your user credentials.
</p>
<p>
<img src="https://i.imgur.com/CppI0Ry.png"/>
</p>

<br />

<h2> Install Active Directory Domain Services </h2>

<p>
  Once in, we see the server manager dashboard. Click on Add Roles and features to begin the active directory installation
</p>
<p>
<img src="https://i.imgur.com/LQaHeir.png"/>
</p>

<br />

<p>
  Run through the installation by clicking next until the server roles section.
</p>
<p>
<img src="https://i.imgur.com/uGtawAc.png"/>
</p>

<br />

<p>
  In the server roles section click on Active Directory Domain Services then click on Next.
</p>
<p>
<img src="https://i.imgur.com/xUqbxUJ.png"/>
</p>

<br />

<p>
  Click on Add Features and Install.
</p>
<p>
<img src="https://i.imgur.com/abkTqwD.png"/>
</p>

<br />

<p>
  Speed through to the confirmation section and make sure the box is checked and install. Give it some time to install. It is now time to promote the server to a domain controller.
</p>
<p>
<img src="https://i.imgur.com/g1Uh7Ge.png"/>
</p>

<br />

<h2>Make the server the Domain Controler</h2>

<p>
  Click on Promote this server to a domain controller.
</p>
<p>
<img src="https://i.imgur.com/rpocKKP.png"/>
</p>

<br />

<p>
  Click on add a New Forest, put in a domain name, and click on Next. I will be using mydomain.com
</p>
<p>
<img src="https://i.imgur.com/QM7wIXx.png"/>
</p>

<br />

<p>
  we are not going to be using this but for the purpose of completing the installation put in a password and confirm it and click next
</p>
<p>
<img src="https://i.imgur.com/yIj5E8g.png"/>
</p>

<br />

<p>
  Run through the setup by clicking next until you pass the prerequisite checks and click install. The vm will restart and now it is time to create our Organisation units and users.
</p>
<p>
<img src="https://i.imgur.com/C7EQg0C.png"/>
</p>

<br />

<h2> Creating Organisational Units and Users </h2>

<p>
  Now we have to log in to the server using our domain credentials. RDP into the server click on more choices and click on use another account. Login using the domain and the credentials
</p>
<p>
<img src="https://i.imgur.com/9HS9YUe.png"/>
</p>

<br />

<p>
  Click on tools and click on active directory users and computers
</p>
<p>
<img src="https://i.imgur.com/rnLkqxe.png"/>
</p>

<br />

<p>
  right click on the domain, click on new, and click on organisational unit
</p>
<p>
<img src="https://i.imgur.com/98OsZHK.png"/>
</p>

<br />

<p>
 we are going to name this OU "_EMPLOYEES". You can name yours whatever you want. OUs are like departments. We are also going to create "_ADMINS".
</p>
<p>
<img src="https://i.imgur.com/dEWo24k.png"/>
<img src="https://i.imgur.com/I2SfUGR.png"/>
</p>

<br />

<p>
 we are going to create a user in our _ADMIN OU. Right-click on the _ADMIN OU, click on new, and click on user.
</p>
<p>
<img src="https://i.imgur.com/eBDBnhN.png"/>
</p>

<br />

<p>
 Fill in the user credentials and click on next.
</p>
<p>
<img src="https://i.imgur.com/dDQ7sMg.png"/>
</p>

<br />

<p>
 Because this is a lab environment we can uncheck the box and fill in the password and click next. A user is created inside the _ADMIN OU.
</p>
<p>
<img src="https://i.imgur.com/XBfIuNo.png"/>
</p>

<br />

<p>
 Let us actually give our new user administrative privileges by adding him to the domain administrator group. Right-click on the user and click on properties.
</p>
<p>
<img src="https://i.imgur.com/gkGWHvd.png"/>
</p>

<br />

<p>
Click on the members of tab
</p>
<p>
<img src="https://i.imgur.com/LCJzvgd.png"/>
</p>

<br />

<p>
Click on Add
</p>
<p>
<img src="https://i.imgur.com/iUzHGeV.png"/>
</p>

<br />

<p>
on the box type " domain admins" and click on check names and then OK. This searches for an inbuilt group for domain admins.
</p>
<p>
<img src="https://i.imgur.com/nYRckbC.png"/>
</p>

<br />

<p>
Click on apply then OK
</p>
<p>
<img src="https://i.imgur.com/MtP92iS.png"/>
</p>

<br />

<h2>It is now time to install our Windows 10 client VM</h2>

<p>
  While creating the VM we must select the same Resource group we created from the start and also the region must be the same as that of the server. We choose the WIN10 pro image.
</p>
<p>
<img src="https://i.imgur.com/MtP92iS.png"/>
</p>

<br />

<p>
  Fill in your credentials, check the confirmation box, and go to Next.
</p>
<p>
<img src="https://i.imgur.com/MkjkMHZ.png"/>
</p>

<br />

<p>
The virtual network must be the same as the virtual network of the server. The subnet should be the same too. If not the two computers won't be able to communicate. You can now create the VM.</p>
<p>
<img src="https://i.imgur.com/3RR0KLq.png"/>
</p>

<br />

<h2>Joining the windows VM to the domain controler</h2>

<p>Before we join the windows VM to the domain controller it is very important that we do two things for it to be a success <p>
<p>We must make the private Ip address of the server static and we must configure the DNS of the windows VM by making the DNS entry the private address of the domain controller<p>
<p>By doing so the DNS server of the windows VM becomes the DC<p>  
<p>Inside of VM machines in the Azure portal click on the server VM and click on network settings <p>
  <img src="https://i.imgur.com/JNM6PC4.png"/>
</p>

<br />

<p>
Click on the network interface
<p>
<img src=" https://i.imgur.com/SWwCPHu.png"/>
</p>

<br />

<p>
Click on IP Config
<p>
<img src="https://i.imgur.com/HWvTjEm.png"/>
</p>

<br />

<p>
change the selection from DHCP to static and save. This way the private ip address will not keep changing each time the server reboots.Now reboot the server.
<p>
<img src="https://i.imgur.com/8YczOgi.png"/>
</p>

<br />

<p>
Now we go back to the Windows VM and change the DNS server config. Click on the Windows VM in the Azure portal and go to network settings.
<p>
<img src="https://i.imgur.com/MeqL72N.png"/>
</p>

<br />

<p>
enter the network interface and this time click on DNS servers
<p>
<img src="https://i.imgur.com/4Bh7uhN.png"/>
</p>

<br />

<p>
Click on custom and type in the private IP address of the domain controller and click on save and reboot the WIN10 VM.
<p>
<img src="https://i.imgur.com/w1iNxgA.png."/>
</p>
<br />

<p>
RDP into the Windows VM and right-click on the Windows icon and click on system.
<p>
<img src="https://i.imgur.com/kSzaRdk.png"/>
</p>
<br />

<p>
Scroll down and click on rename this PC (advanced).
<p>
<img src="https://i.imgur.com/h7NBFpv.png"/>
</p>
<br />

<p>
Click on change.
<p>
<img src="https://i.imgur.com/Tn1wabo.png" />
</p>
<br />

<p>
Click on domain, input the domain name, and click ok. 
<p>
<p><img src="https://i.imgur.com/hwXW8M1.png" />
</p>
<br />

<p>You have to input an administrative domain account credential. Let's use the user we created in the _ADMIN OU. If done right we receive a welcome to the domain dialogue box and the VM restarts <p>
  
<p><img src="https://i.imgur.com/h48hMmL.png"
</p>
<br />

<h2>Create many users using PowerShell scripting</h2>

<p>Let's create many users for our _EMPLOYEES OU. This time we want to use Powershell rather than creating it manually</p>
  <p>In our Windows server click on search and type in PowerShell ISE and run it</p>
<p><img src="https://i.imgur.com/5AYhUNm.png" />
</p>
<br />


<p>This is the script we have to run. We make sure the path specifically relates to our "_EMPLOYEES" OU and we run it. This will create random users inside of our "_EMPLOYEES" OU. </p>
    <p><img src="https://i.imgur.com/rp7Mj0A.png" /></p>
    
<br />

<p>
Now we have many users in our _EMPLOYEES OU and we can now use any of them to login into our WIN10 VM as members of the domain.
<p>
<img src="https://i.imgur.com/s948jKa.png"/>
</p>

<br />

<p>But before we log in using our newly created domain users we have to give them permission to RDP into our WIN10 VM.</p>
<p>In the Windows 10 VM go to systems as we did before and click on Remote Desktop </p>
<p><img src="https://i.imgur.com/6cgghkj.png"/></p>

<br />

<p>
  Click on Select Users under user accounts
</p>
<p>
<img src="https://i.imgur.com/09c9xDh.png"/>
</p>

<br />

<p>
  Just as we did give permissions to the domain admins this time we want to click Add, search for the domain users group, and click OK. Now the domain users we created can RDP into the WIN 10 VM.
</p>
<p>
<img src="https://i.imgur.com/xNGx66C.png"/>
</p>

<br />

<p>
  Let's RDP into the Windows VM using one of the user domain accounts we created in the _EMPLOYEE OU.
</p>
<p>
<img src="https://i.imgur.com/vmYS4Zm.png"/>
</p>

<br />

<h2>Congratulations We have just installed and configured active directory in the cloud using Azure VMs</h2>



