<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of Active Directory within Azure Virtual Machines.<br />




<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services


<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Setup Resources in Azure
- Ensure Connectivity between the client and Domain Controller
- Install Active Directory
- Create an Admin and Normal User Account in AD
- Join Client-1 to your domain (mydomain.com)
- Setup Remote Desktop for non-administrative users on Client-1
- Create additional users and attempt to log into client-1 with one of the users


<h2>Deployment and Configuration Steps</h2>

- Setup Resources in Azure
<p>

![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/24339f52-82d8-46e6-95c5-1a04ca181637)

<p>
- After you create your Azure account navigate to the Virtual Machine tab and click Create.
<p>

![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/ef9cc8ce-9e51-4154-a003-4b1ec1369f69)


- Create the Domain Controller VM (Windows Server 2022) named “DC-1”
Take note of the Resource Group and Virtual Network (Vnet) that get created at this time

![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/5b167d98-98a1-4f76-aeea-5c5202676c74)

<p>

- After you fill out the necessary information (don't forget your username and password, you need it to log into your VM) click review/create wait for the validation process to complete, and click Create. 
</p>

![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/64d72967-cd5e-4861-89dc-6a5ff024a548)


- The domain control's (DC-1), IP address must be set to static. 

- To perform this step navigate to the network settings tab in DC-1. 

![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/e7fda090-a22d-4f6d-8de6-8d3aac2f9803)

- Click the Network interface: dc-1221_21

![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/d85b342c-04c9-4f1a-ac0f-c69e40fc5097)

- Click IP configuration.

![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/bf54e5f9-5c84-4a80-80b3-13850b8faba0)

- Click Edit configuration set the IP address to static and hit save.


![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/97068573-9c62-4de9-8e7e-c51a003ade9a)

- Create the Client VM (Windows 10) named “Client-1”. Use the same Resource Group and Vnet that was created for DC-1.

![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/13cb9c1e-8759-481b-be1d-7055e209f016)

- Ensure that both VMs are in the same Vnet (you can check the topology with Network Watcher).

![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/3c88ad6f-a05f-4a1d-b5e4-6af97e3850f3)

- Once the process of creating your second VM is done, go to the Virtual Machine section and make sure you have two VMs.

![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/52ba3a18-360f-4f6d-bf3b-c524a03f88cf)

Ensure Connectivity between the client and Domain Controller


- Login to Client-1 with Remote Desktop and ping DC-1’s private IP address with ping -t <ip address> (perpetual ping)


![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/7cf33898-bb30-4eb3-90e6-450c059ddf7f)

- Login into the Domain Controller and enable ICMPv4 on the local Windows firewall.

![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/21496fd4-16c9-476a-92e8-22ee9b33b441)

- Go to the inbound rules list locate ICMPv4 echo and enable it.

![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/ce3d8820-70ef-4f8d-8742-018386d91bc6)

- Check back at Client-1 to see the ping succeed

![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/82768413-3708-443b-8111-be3895c2c50b)

Install Active Directory


- Go to DC-1 open Server Manager, and click on Add roles and features.

![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/a0adf369-3afc-4c98-91d0-7c5eabf5bd28)

- Select the destination server.

![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/bf83b623-6e69-4bd7-872a-b9ac24889ab4)

- Select Active Directory Domain Services. 

![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/3681892b-4943-4745-9393-3800616f6f72)

- Install Active Directory Domain Services.

![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/4539bedc-c954-408b-98d4-9145ead6c0bb)

- After Active Directory Domain Services is downloaded, the Local Server and All Server columns will appear.

![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/ed2c4ea3-6523-486d-b604-9ff8925f0dce)
