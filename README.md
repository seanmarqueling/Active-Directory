# Active-Directory Domain Server
How to setup an Active Directory Domain Server in Windows 2019 Server

## Introduction

In this project, I build an Active Diretory Server in a Windows 2019 Server.

![image](https://github.com/seanmarqueling/Active-Directory/blob/main/0.%20Direction.png?raw=true)

## Instuctions

In this project - I created a Windows 2019 Server within Virtual Box. When setting up the server I needed to make sure that that are two different networks
The first network is the internet network that will be used to allow users to use the same public IP address and access the Internet.

![image](https://github.com/seanmarqueling/Active-Directory/blob/main/1.%20NAT.png?raw=true)

The second network is the internal network allow users to connect from their workstation to the server.

![image](https://github.com/seanmarqueling/Active-Directory/blob/main/2.%20Internet.png?raw=true)

Once the two networks are created, I need to go login to the Windows 2019 Server and setup the networks. In the image below we can see that we have both of the networks created. I went into the
change adapter options to rename the networks to be 'Internet' and 'Interal' to easily differentiate the two when connecting users to the server. 

![image](https://github.com/seanmarqueling/Active-Directory/blob/main/1.%20Network.png?raw=true)

After the netwroks have been renamed, I went into the internal network and configured the IPv4 address that I will be using in this lab. 
IP: 172.16.0.1
Subnet Mask: 255.255.255.0
DNS Server: 127.0.0.1

![image](https://github.com/seanmarqueling/Active-Directory/blob/main/33.png?raw=true)
