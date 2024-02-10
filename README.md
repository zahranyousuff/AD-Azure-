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
