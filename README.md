# Active-Directory
This project details how to setup a basic home lab running active directory using oracle virtual box to create the virtual machines and adding users using a powershell script. 

<h2>Practical Skills Developed</h2>

<b> Active directory management | Virtualisation | Troubleshooting | Identity and access management | Networking | Group policy management | System administration </b> 

<h2>Tools Used</h2>

- <b>Microsoft Windows 10</b>
- <b>Microsoft server 2019</b> 
- <b>Oracle virtual box + extension pack</b> 

<h2>Environment Used </h2>

- <b>Windows 11</b>

<h2>Project walk-through:</h2>

<p align="center">

Firstly, I installed virtual box which will be used to run the virtual machines on. Subsequently I installed a windows 10 ISO and a server 2019 ISO that I am going to use to install the two operating systems on two separate virtual machines. 
<img src=" " height="80%" width="100%" />
<br />
<br />
The first virtual machine is going to be our domain controller which is going to house active directory (AD). This virtual machine will have two network adapters, one is going to be used to connect to the outside internet and the other one will be used to connect to the private network of the virtual box that the clients are going to connect to. 
<img src="https://imgur.com/wBMQKRU.png" height="80%" width="100%" />


Once the virtual machines are created, we are going to assign server 2019 on it and assign IP addressing for the internal network. The external network will automatically get IP addressing from my home network. Next, we are going to install AD and create our domain, then we will configure NAT and routing so the clients on the private network can reach the internet through the domain controller. 

DHCP will be set up on the domain controller, so when we create our windows 10 VM it can automatically get an IP address. Lastly, we run a powershell script which will be obtained for this project, this will automatically create a thousand users in AD. We will create another VM and install windows 10 on it, this VM will be created to the private virtual box network. We are going to name it client 1 and join it to the domain and log in to it using our domain accounts. 

This project provides hands-on experience with core network infrastructure. AD is fundamental for managing users, groups, and resources, offering insight into access control, authentication, and Group Policy management.
<img src=" " height="80%" width="100%" />
<br />
<br />
 After both installations, I proceeded to scan the Windows sandbox to identify vulnerabilities on the endpoint. The scan returned eighteen vulnerabilities with one "Medium" severity and a CVSS of 5.3. Other vulnerabilities in providing information were also looked at and taken notice of.<br/>
<img src="https://i.imgur.com/RcBSPmq.png" height="80%" width="100%" />
<br />
<br />
 I proceeded to conduct a more in-depth scanning through Credential scanning. With this, I had to grant permission to the sandbox environment to connect remotely. I did this by enabling the Remote Registry to be automatic, turning on the advanced sharing setting and creating a LocalAccountTokenFilterPolicy to grant access as directed by Nesus documentation for connecting remotely with users on a different network. I then restarted the computer for the new setting to take effect. <br/>
<img src="https://i.imgur.com/KlDVpk2.png" height="80%" width="100%" />
<img src="https://i.imgur.com/QLCIAWz.png" height="80%" width="100%" />
<img src="https://i.imgur.com/5WGJhDz.png" height="80%" width="100%" />
<br />  
I configured the Credential scanning on my pc by validating it with the credentials of the sandbox OS and running the scan. It took quite some time to scan, s it returned more high-severity vulnerabilities.<br />
  <br/>
<img src="https://i.imgur.com/BokhzoX.png" height="80%" width="100%" />
<img src="https://i.imgur.com/H42DiuN.png" height="80%" width="100%" />
<br />
<br />
 Additionally, an old version of Firefox version was also installed on the sandbox to perform scanning tests.<br/>
<img src="https://i.imgur.com/bNcZEEx.png" height="80%" width="100%" />
<br />
<br />
The results returned had more critical vulnerabilities that required immediate attention. The remedies for the vulnerabilities were to apply an update to the system.<br/>
<img src="https://i.imgur.com/HdmcJJL.png" height="80%" width="100%" />
<img src="https://i.imgur.com/nUuPWwH.png" height="80%" width="100%" />
<br />
<br />
 The sandbox system was updated, and the main critical issue was the deprecated Firefox. It was realised that most vulnerabilities identified after the update were for informational purposes. <br/>
<img src="https://i.imgur.com/OsSzoNC.png" height="80%" width="100%" />
<br />
<br />

