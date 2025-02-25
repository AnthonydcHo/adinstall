<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1> Active Directory: Installation & Infrastructure </h1>
This tutorial outlines the implementation of on-premises Active Directory within two Azure virtual machines. <br/>
<br/>
<p align="center">
<img height ="80% ="<img width="40%" alt="Screenshot 2025-02-25 at 4 05 26 PM" src="https://github.com/user-attachments/assets/effe8a9b-6c87-4011-9da1-e041a08a700b" /> <br/>


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>Deployment and Configuration Steps</h2>

<p align="center">
Create a Resource Group as Active Directory Lab > Create the Domain Controller VM (Windows Server 2022) named “DC-1” > Username: labuser, password: Cyberlab123! 
<p align="center">    
<img width="933" alt="Screenshot 2025-02-25 at 4 05 42 PM" src="https://github.com/user-attachments/assets/7324eeef-6ea5-4ebb-af6b-7c918c09f988" />
<br />


- Create a Virtual Network and Subnet as Active Directory V-net: 
    - We can use East US 2 as our time zone. 

<br />

Go into dc-1 VM azure network setting > Go into dc-1 virtual network interface card > Click on ipconfig1 > Below Public IP address setting change allocation from dynamic to static > save:
<p align="center"> 
<img width="352" alt="3" src="https://github.com/user-attachments/assets/bed997e0-6ecc-44d6-b753-cb82329997fa" />
<br />
<p align="center"> 
<img width="293" alt="Screenshot 2025-02-25 at 4 09 35 PM" src="https://github.com/user-attachments/assets/1713a834-dbd4-4381-b65c-9b53eb89bcd7" />

Navigate into Client 1 network settings > Click on Client 1 virtual network interface card > Click on DNS Servers and click on custom > Type or paste 10.0.0.4 (dc-1 private ip address): 
<p align="center"> 
<img width="885" alt="x" src="https://github.com/user-attachments/assets/2d09fd61-97b3-43aa-a7da-6a8d252a4d40" />




  - From the Azure Portal, restart Client-1
    - Navigate In VM azure setting to restart it

  - Using remote desktop connection via macOS or windows into client 1 VM
       - Log into using client 1 username and password made
 


Click start and search for Window Powershell > Type ping 10.0.0.4, attempt to ping DC-1’s private IP address > With 4 replies, this indicates an successful ping: 
<p align="center">
<img width="925" alt="Screenshot 2025-02-25 at 4 10 27 PM" src="https://github.com/user-attachments/assets/66ff0b05-162a-4ad8-a925-e6d73eba4f4d" />
<p align="center">

Continue to type ipconfig /all. The output for the DNS settings should show DC-1’s private IP Address: 
<p align="center"> 
<img width="443" alt="Screenshot 2025-02-25 at 4 10 44 PM" src="https://github.com/user-attachments/assets/360c6810-228a-455d-bd64-1d4f6b6c2480" />
<img width="930" alt="Screenshot 2025-02-25 at 4 14 19 PM" src="https://github.com/user-attachments/assets/88aa303f-317f-4be6-b940-57b70bbd492a" />

Login to DC-1 VM and install Active Directory Domain Services > Click start and go into server manager: 
<p align="center"> 
<img width="377" alt="Screenshot 2025-02-25 at 4 12 43 PM" src="https://github.com/user-attachments/assets/b33ad494-aa13-4e09-9e7e-040e2a194a5f" />
  
When server manager runs, click on add roles and features > Continue to click next > In server roles > check Active Domain Services > Finish install: 
<p align="center">
<img width="547" alt="Screenshot 2025-02-25 at 4 13 43 PM" src="https://github.com/user-attachments/assets/6b13ca1e-1bf5-4ccf-9b9b-c52002917d53" />

Setup a new forest as mydomain.com (can be anything, just remember what it is) > log into DC-1 VM >
server manager > click promote server to domain controller:
<p align="center"> 
<img width="927" alt="Screenshot 2025-02-25 at 4 16 25 PM" src="https://github.com/user-attachments/assets/15bcc435-c7dd-4626-8cec-6f5d3bfa05e2" />


Click add a new host and type in mydomain name into Root domain name
<p align="center"> 
<img width="535" alt="Screenshot 2025-02-25 at 4 16 41 PM" src="https://github.com/user-attachments/assets/f91fdbe5-7881-46db-aa6b-2a50206832f5" />

Continue to click next, in domain controller options and directory services restore mode password, we are very likely never going to use this. (You may set up your own password)
<p align="center"> 
<img width="541" alt="Screenshot 2025-02-25 at 4 17 15 PM" src="https://github.com/user-attachments/assets/7402ba1e-537a-40a0-a421-503bccfe3f52" />

Uncheck DNS Delegation > Continue with Install > We have succesfully downloaded Active Directory!
<p align="center"> 
<img width="309" alt="Screenshot 2025-02-25 at 5 07 11 PM" src="https://github.com/user-attachments/assets/c2368ddf-6f6b-417a-9861-bdf9d66fe14b" />
<p align="center"> 
<img width="476" alt="Screenshot 2025-02-25 at 5 09 21 PM" src="https://github.com/user-attachments/assets/582c18c8-00d7-4116-9cd0-1619f9d155a2" />
 <br/>





We've successfully succesfully installed Active Directory, we will continue on deployment of Active Directory! :  <br/>
