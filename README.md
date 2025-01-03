<p align="center">
<img src="https://i.imgur.com/lUDgEHe.jpeg" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Practical Security with Azure NSGs: Blocking Unwanted ICMP Traffic</h1>
This project demonstrates the use of Network Security Groups (NSGs) in Microsoft Azure to enhance the security of virtual machines by blocking ICMP traffic. ICMP (Internet Control Message Protocol) is commonly used for network diagnostics, such as ping requests, but can also be used to cause a denial of service attack.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute](https://youtu.be/hFMQYR5wpyQ)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines)
- Remote Desktop
- Network Security Group ( Firewall )
- CMD

<h2>Operating Systems Used </h2>

- Linux
- Windows 10 (22H2)

<h2>Getting Started</h2>

<p>
First, We have to create two virtual machines: a Windows VM and a Linux VM.
</p>
<p>
<img src="https://i.imgur.com/mKghvJY.png"/>
</p>

<br />

<p>
Then we RDP into our Windows computer with the public IP address of the Windows PC. 
</p>
<p>
<img src="https://i.imgur.com/WqpdNma.png"/>
</p>

<br />

<p>
Now we find the private IP address of the Linux VM. To find it go back to your Azure portal where your VMs are and click on the linux VM scroll down locate the private ip address and memorize it. 
</p>
<p>
<img src="https://i.imgur.com/aZjOBP0.png"/>
</p>

<br />

<p>
On your Windows search bar type in cmd and run CMD  
</p>
<p>
<img src="https://i.imgur.com/n2bKLkv.png"/>
</p>

<br />

<p>
To ping the private IP address of the Linux machine type "ping 10.0.0.5" use your own private IP address of your Linux machines.
<p>
<img src="https://i.imgur.com/KWu5kRD.png"/>
</p>

<br />

<p>
Ping uses the ICMP protocol which can be used to test network connectivity but it can also be used for a cyber attack for example a denial of service attack. A normal ping would stop after receiving an echo request back from the vm but what if we keep sending this ping request and it never stops? It can overwhelm the target. Let's try one by typing " ping 10.0.0.5 -t "
<p>
<img src="https://i.imgur.com/vJY3cO9.png"/>
</p>

<br />

<p>
This is a problem if it keeps happening. What if 1000 computers all ping the Linux machine like this? we can see the issue. Let's use Network Security Groups (firewall) to block ICMP traffic coming into the Linux VM. Go back to the Azure portal and click on the Linux machine > then click "Network settings" under "Networks"
</p>
<p>
<img src="https://i.imgur.com/aLLfbmh.png"/>
</p>

<br />

<p>
Under Network Security Group click on LinuxVM-nsg
</p>
<p>
<img src="https://i.imgur.com/gA6J7SL.png"/>
</p>

<br />

<p>
  click on Add.
</p>
<p>
<img src="https://i.imgur.com/u2OkrND.png"/>
</p>

<br />

<p>
  Add these settings in the inbound rule and save. You can refer to the video above for an explanation of this deny rule.
</p>
<p>
<img src="https://i.imgur.com/AsDn7Jz.png"/>
</p>

<br />

<p>
  Here is the inbound deny rule we just created.
</p>
<p>
<img src="https://i.imgur.com/7ptP4Xp.png"/>
</p>

<br />

<h2> Install Active Directory Domain Services </h2>

<p>
  Remember the perpetual ping we still had going ? let's see what happens. Due to the firewall blocking ICMP traffic, the pings stop going through and we get a time-out request.
</p>
<p>
<img src="https://i.imgur.com/g4fyPcw.png"/>
</p>

<br />

<h2>Congratulations by successfully configuring Azure Network Security Groups to block ICMP traffic, we have enhanced the security of the virtual machine</h2>



