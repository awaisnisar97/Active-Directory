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

Firstly, I installed virtual box which will be used to run the virtual machines on. Subsequently I installed a windows 10 ISO and a server 2019 ISO that I am going to use to install the two operating systems on two separate virtual machines. See links below. 

https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019

https://www.microsoft.com/en-us/software-download/windows10ISO
<br />
<br />
The first virtual machine is going to be our domain controller which is going to house active directory (AD). This virtual machine will have two network adapters, one is going to be used to connect to the outside internet and the other one will be used to connect to the private network of the virtual box that the clients are going to connect to. 
<img src="https://imgur.com/IGhoWMn.png" height="80%" width="100%" />


Once the virtual machines are created, we are going to assign server 2019 on it and assign IP addressing for the internal network. The external network will automatically get IP addressing from my home network. Next, we are going to install AD and create our domain, then we will configure NAT and routing so the clients on the private network can reach the internet through the domain controller. 
<img src="https://imgur.com/opVZfuW.png" height="80%" width="100%" />

Next we are going to install active directory domain services (ADDS) and create a domain. 
<img src="hhttps://imgur.com/54oBv3I.png" height="80%" width="100%" />
<img src="https://imgur.com/ww12OKi.png" height="80%" width="100%" />

Once installed, you will notice a yellow flag next to manage, click on that to do a post eployment configuration of the ADDS. This is to create the domain itself.
<img src="https://imgur.com/7GeK8Bk.png" height="80%" width="100%" />

The VM will restart once installed. 
We are going to create our own dedicated domain admin account. An organisational unit will be created to put the admin account in, create a new user in the admin folder 
<img src="https://imgur.com/xd9ov4Q.png" height="80%" width="100%" />
<img src="https://imgur.com/8WEG5Ny.png" height="80%" width="100%" />

Select properties and add in domain admin. 
<img src="https://imgur.com/d3Jef0a.png" height="80%" width="100%" />
Following this we will log out and log in again using our admin account. 

RAS/NAT (remote access server/netwrok address translation) will now be installed. The purpose of this is to allow the windows 10 client to be on a private virtual network but still be able to access the internet through the domain controller. Install RAS/NAT on domain controller. 
<img src="https://imgur.com/jpXCaOb.png" height="80%" width="100%" />
<img src="https://imgur.com/OjVQbkk.png" height="80%" width="100%" />
<img src="https://imgur.com/OIrWgGI.png" height="80%" width="100%" />
<img src="https://imgur.com/tcGNGMz.png" height="80%" width="100%" />

DHCP will be set up on the domain controller, so when we create our windows 10 VM it can automatically get an IP address. We do this by going on add roles and features, following this, we will our DHCP scope.
<img src="https://imgur.com/xLnr9Tc.png" height="80%" width="100%" />
<img src="https://imgur.com/OtX0bNn.png" height="80%" width="100%" />


Lastly, we run a powershell script, this will automatically create a thousand users in AD. 
Disclaimer - The powershell script was obtained 
Upload the script, enable excution policy to unrestricted. Going back to the AD users and computers you will notice the list of all created users.
<img src="https://imgur.com/X9ruz2C.png" height="80%" width="100%" />
<img src="https://imgur.com/4XyoWyk.png" height="80%" width="100%" />


We will create another VM and install windows 10 on it, this VM will be created to the private virtual box network. We are going to name it client 1 and join it to the domain and log in to it using our domain accounts. 
<img src="https://imgur.com/YJJWRd1.png" height="80%" width="100%" />
<img src="https://imgur.com/8pCHbI4.png" height="80%" width="100%" />
<img src="https://imgur.com/3HG0YgI.png" height="80%" width="100%" />


This project provides hands-on experience with core network infrastructure. AD is fundamental for managing users, groups, and resources, offering insight into access control, authentication, and Group Policy management.
