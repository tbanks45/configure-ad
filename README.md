<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1: Create the Domain Controller VM (Windows Server 2022) named “DC-1” and Create the Client VM (Windows 10) named “Client-1”
- Step 2: Install Active Directory
- Step 3: Create an Admin and Normal User Account in AD
- Step 4: Join Client-1 to your domain (mydomain.com)

<h2>Deployment and Configuration Steps</h2>

<p>
![image](https://github.com/tbanks45/configure-ad/assets/142834800/382bd111-d1c6-4b06-8019-d70f7ec24f3a)
</p>
<p>
Here in step 1 I created two virtual machines within the same resource group and virtual network in microsoft azure. One virtual machine(Domain controller) using windows server 2022 and the other virtual machine(Client) using windows 10. I set the domain controller’s NIC private IP address to be static because as the domain controller the address cannot change. Also, after logging into the domain controller's vm I enabled ICMPv4 in on the local windows firewall so that connectivity was functioning.
</p>
<br />

<p>
![image](https://github.com/tbanks45/configure-ad/assets/142834800/b4db08f5-e4f2-464b-8151-d5bf85088f5e)
</p>
<p>
Here while logged into the domain controller I installed active directory domain services. To promote this vm as the domain controller I setup a new forest as mydomain.com.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
After creating admin and normal user accounts in active directory I joined client-1 to my domain (mydomain.com). From the Azure Portal, set Client-1’s DNS settings to the DC’s private IP address. From the Azure Portal, restart Client-1. Next I logged into Client-1 (Remote Desktop) as the original local admin (labuser) to join it to the domain (computer will restart). Lastly, I logged in to the Domain Controller (Remote Desktop) to verify Client-1 shows up in Active Directory Users and Computers (ADUC) inside the “Computers” container on the root of the domain.

</p>
<br />
