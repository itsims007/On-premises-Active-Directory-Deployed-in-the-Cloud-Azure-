<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute](https://youtu.be/XaYNFtlybCE)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2> Deployment and Configuration Steps</h2>

SETUP RESOURCES IN AZURE

<p>
<img src=https://i.imgur.com/7x9KE2Z.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In this step, I created 2 VMs. One Vm named DC1 (domain controller) and the other named client1.
</p>

CONFIRM CONNECTIVITY BETWEEN BOTH VMs
                                                                                                <p>
<img src="https://i.imgur.com/hthqRR1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
                                                                                               <p>
<img src="https://i.imgur.com/yLZTRBu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
                                                                                               <p>
<img src="https://i.imgur.com/P0zHZpE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
It is very important to make sure both VMs communicate with each other. First, communication was tested with a "ping -t" command and it failed. It sent back a "request timed out" response. Next, I enabled ICMPv4 protocol in the local windows firewall. After doing that, I tested the connection again and the a "ping -t" command and it was a success! A reply was received.
</p>
                                                                                                
INSTALL ACTIVE DIRECTORY

<p>
<img src="https://i.imgur.com/RC5pgqC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>                                                                                                                                                                                            <p>
<img src="https://i.imgur.com/FFlWk7C.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
                                                                                               
<p>
Install Active Directory Domain Services. Then setup a new forest as mydomain.com.
</p>
                                                                                                 
CREATE AN ADMIN AND NORMAL USER ACCOUNG IN ACTIVE DIRECTORY

<p>
<img src="https://i.imgur.com/VpUKuwf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Created a normal user named Jane Doe. Then added her to the ADMINS group.
</p>

JOIN CLIENT1 TO DOMAIN (MYDOMAIN.COM)

<p>
<img src="https://i.imgur.com/UiC09tQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.imgur.com/lLhwqIM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From the Azure portal, I set Client1's DNS settings to the DC's private Ip address..
</p>


SETUP REMOTE DESKTOP FOR NON-ADMINISTRATIVE USERS ON CLIENT 1

<p>
<img src="https://i.imgur.com/CK0jdba.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

CREATE MULTIPLE ADDITIONAL USERS TO CREATE A DATABASE OF USERS
                                                                                               
<p>
<img src="https://i.imgur.com/R6jRhtK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
To create 10000 additional randomly name uses, I used a script that would execute the solution.
</p>
<br />


<br />
