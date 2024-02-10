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

- After you fill out the necessary information along with your username and password(don't forget your username and password, you need it to log into your VM) click review/create wait for the validation process to complete, and click Create. 
</p>

![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/64d72967-cd5e-4861-89dc-6a5ff024a548)

