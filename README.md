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

- Promote the Server to a domain controller.

![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/f3c28c89-e26e-4afc-b9c0-efa112e0a49f)


- Setup a new forest as zahran.com (can be anything, just remember what it is)

![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/982e65db-999e-4f68-bc8e-11b66398740b)

- Create a (DSRM) password (you won't need to enter this password again.)

![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/f84972c1-7ae3-427e-aa95-aa7a4a48f980)

- Restart and then log back into DC-1 as user: zahran.com\labuser (or whatever username you used when you created the VM in the Azure portal.)


![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/a7c85dec-1cb5-4e1c-b5d9-64eed1157f8d)

Create an Admin and Standard User Account in AD


- In Active Directory Users and Computers (ADUC), create an Organizational Unit (OU) called “_EMPLOYEES”


![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/b1ff6297-0c5d-4c2e-99f9-234c89db2387)

- Create a new OU named “_ADMINS”


![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/08d4d251-b502-4cac-8395-f86261c3b75b)


- In the _ADMINS folder create a new employee named “Jane Doe” (same password) with the username of “jane_admin”


![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/508e797e-5163-41db-b04c-82ee671044d6)

![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/c54135bb-b5f1-4358-b6d1-ecb76d32d54f)

![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/93a3859c-8a33-489e-b12a-429a862cbe3f)


- Add jane_admin to the “Domain Admins” Security Group.
- Log out/close the Remote Desktop connection to DC-1 and log back in as “zahran.com\jane_admin”.
- User jane_admin as your admin account from now on


![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/8262b0a5-a233-48c9-99bc-86cef36b2e14)

![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/6c21e7ad-a783-4084-bb35-65063c47261d)



Join Client-1 to your domain (zahran.com)


- From the Azure Portal, set Client-1’s DNS settings to the DC-1’s Private IP address.


![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/230fd218-d4dc-4de1-8690-6feee0b2fcc5)


- From the Azure Portal, restart Client-1
- Type ipconfig /all to check if your DNS server is the same as your domain controller.

![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/10758ca8-de08-461c-8a72-8d67bf4294e4)


![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/94a54cf0-16c1-4cd2-af73-ce47e69542b6)


- Login to Client-1 (Remote Desktop) as the original local admin (labuser) and join it to the domain (computer will restart)


![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/6f122eca-decf-43fb-98a7-db6086fd6d16)

![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/524452d4-396c-4dba-bb23-5a48b04e0619)

![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/f4802eb9-ec85-4f6e-a4be-065750039823)

![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/20fb05d9-c42b-455f-b065-a41c338609e1)

![image](https://github.com/zahranyousuff/AD-Azure-/assets/159392784/b96721e4-6ba3-4052-8ff5-bc69ff61af27)


