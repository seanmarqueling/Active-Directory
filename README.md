# Active-Directory Domain Server
How to setup an Active Directory Domain Server in Windows 2019 Server

## Introduction

In this project, I build an Active Diretory Server in a Windows 2019 Server.

![image](https://github.com/seanmarqueling/Active-Directory/blob/main/0.%20Direction.png?raw=true)

## Instuctions - Setting up the network

- Create two different networks: Internal & Internet
- Active Directory Domain Server
- Remote Access Server & Network Address Translation
- Dynamic Host Configuration Protocol

In this project - I created a Windows 2019 Server within Virtual Box. When setting up the server I needed to make sure that there are two different networks.
The first network is the internet network that will be used to allow users to use the same public IP address and access the Internet.

![image](https://github.com/seanmarqueling/Active-Directory/blob/main/1.%20NAT.png?raw=true)

The second network is the internal network allow users to connect from their workstation to the server.

![image](https://github.com/seanmarqueling/Active-Directory/blob/main/2.%20Internet.png?raw=true)

Once the two networks are created, I login to the Windows 2019 Server and setup the networks. In the image below we can see that we have both of the networks created. I went into the
change adapter options to rename the networks to be 'Internet' and 'Interal' to easily differentiate the two when connecting users to the server. 

![image](https://github.com/seanmarqueling/Active-Directory/blob/main/1.%20Network.png?raw=true)

After the netwroks have been renamed, I went into the internal network and configured the IPv4 address that I will be using in this lab. 

- IP: 172.16.0.1
- Subnet Mask: 255.255.255.0
- DNS Server: 127.0.0.1

![image](https://github.com/seanmarqueling/Active-Directory/blob/main/33.png?raw=true)

## Instructions - Setting up AD DS - Active Directory Domain Server

From Windows 2019 Server dashboard - to add AD DS - we need to go into Roles and Features to select that AD DS and install it.

![image](https://github.com/seanmarqueling/Active-Directory/blob/main/4.%20AD%20DS%20roles.png?raw=true)

![image](https://github.com/seanmarqueling/Active-Directory/blob/main/5.%20select.png?raw=true)

After AD DS is installed - go to the yellow flag at the top and promote this computer to a domain to fully execute.

When deploying the configurement we will be adding a new forest that will be called 'example.com'.

![image](https://github.com/seanmarqueling/Active-Directory/blob/main/6.%20Deployment.png?raw=true)_

Once the domain is created I then created an admin account for the server.

To create an admin account I went to Active Directory Users and Computers.

Go into example.com, create a new organizational unit and call it '_ADMIN'.

![image](https://github.com/seanmarqueling/Active-Directory/blob/main/7.%20admin.png?raw=true)

From the _Admin organizational unit create a new user.

![iamge](https://github.com/seanmarqueling/Active-Directory/blob/main/8.%20user.png?raw=true)

In order to make this user an admin I added it to 'Domain Admins'.

![image](https://github.com/seanmarqueling/Active-Directory/blob/main/9%20domain%20admins.png?raw=true)

## Instructions - RAS / NAT - Remote Access Server & Network Address Translation

Next step is to install the RAS / NAT. This server will allow uses to connect to the server and use the internet.

In the server dashboard we need to add roles and features to install this application.

Select 'Remote Access'.

![iamge](https://github.com/seanmarqueling/Active-Directory/blob/main/10.%20ras%20nat.png?raw=true)

Select 'Routing".

![image](https://github.com/seanmarqueling/Active-Directory/blob/main/11.%20ras%20nat%202.png?raw=true)

Once that has been installed go into 'Tools' and select 'Routing and Remote Access'

![image](https://github.com/seanmarqueling/Active-Directory/blob/main/12.%20ras%20nat%203.png?raw=true)

From here - configure the server to NAT.

![image](https://github.com/seanmarqueling/Active-Directory/blob/main/NAT.png?raw=true)

Select 'Internet' for the network to be used for NAT server.

![image](https://github.com/seanmarqueling/Active-Directory/blob/main/13.%20ras%20nat%204.png?raw=true)

## Instructions - DHCP - Dynamic Host Configuration Protocol

Within the Server Dashboard go into add roles and features and select DHCP server.

![image](https://github.com/seanmarqueling/Active-Directory/blob/main/DHCP%201.png?raw=true)

After DHCP installs, go into tools and select DHCP

![image](https://github.com/seanmarqueling/Active-Directory/blob/main/DHCP%202.png?raw=true)

In the DHCP server application, create a new scope.

![image](https://github.com/seanmarqueling/Active-Directory/blob/main/DHCP%203.png?raw=true)

Within the scope create a range for the list of IPs that can be used on the server.

-Start IP Address: 172.16.0.100
-End IP Address: 172.16.0.200
-Length: 24
-Subnet Mask: 255.255.255.0

![image](https://github.com/seanmarqueling/Active-Directory/blob/main/DHCP%204.png?raw=true)

Select 'Yes, I want to configure these options now.

![image](https://github.com/seanmarqueling/Active-Directory/blob/main/DHCP%205.png?raw=true)

Create a router default gateway IP address 172.16.0.1

![image](https://github.com/seanmarqueling/Active-Directory/blob/main/DHCP%206.png?raw=true)

Windows Server 2019 is now setup with Active Directory that can allow users to connet to it and gain access to the internet.
