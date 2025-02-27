<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1> Active Directory: Installation & Infrastructure </h1>
This tutorial outlines the implementation of on-premises Active Directory within two Azure virtual machines. 

<p align="center">    
<img src="https://i.imgur.com/oL043lv.png" height="80%" width="80%" 
<p align="center">    




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
<img src="https://i.imgur.com/ddzNbgx.png" height="80%" width="80%" 
<br />



- Create a Virtual Network and Subnet as Active Directory V-net: 
    - We can use East US 2 as our time zone. 



Go into dc-1 VM azure network setting > Go into dc-1 virtual network interface card > Click on ipconfig1 > Below Public IP address setting change allocation from dynamic to static > save:
<p align="center"> 
<img src="https://i.imgur.com/QRPMgGZ.png" height="80%" width="80%" 
<br />
<p align="center"> 
<img src="https://i.imgur.com/z8vDm5B.png" height="80%" width="80%" 
<br />
<br />

Navigate into Client 1 network settings > Click on Client 1 virtual network interface card > Click on DNS Servers and click on custom > Type or paste 10.0.0.4 (dc-1 private ip address): 
<p align="center"> 
<img src="https://i.imgur.com/HPtHpsU.png" height="80%" width="80%" 
<br />



  - From the Azure Portal, restart Client-1
    - Navigate In VM azure setting to restart it

  - Using remote desktop connection via macOS or windows into client 1 VM
       - Log into using client 1 username and password made
 

<br />

Click start and search for Window Powershell > Type ping 10.0.0.4, attempt to ping DC-1’s private IP address > With 4 replies, this indicates an successful ping: 
<p align="center">
<img src="https://i.imgur.com/IsVJetO.png" height="80%" width="80%" 
<p align="center">

Continue to type ipconfig /all. Output for the DNS settings should show DC-1’s private IP Address: 
<p align="center">
<img src="https://i.imgur.com/ipztBhi.png" height="80%" width="80%"     
<p align="center">
<img src="https://i.imgur.com/we4VdUA.png" height="80%" width="80%" 
<p align="center">

Login to DC-1 VM > install Active Directory Domain Services > Click start > server manager: 
<p align="center"> 
<img src="https://i.imgur.com/dJaVobe.png" height="80%" width="80%" 
<p align="center">
<br /> 
    
When server manager runs > add roles and features > Continue to click next > server roles > check Active Domain Services > Finish install: 

<p align="center">
<img src="https://i.imgur.com/uNcYn8l.png height="80%" width="80%"
<p align="center">


Setup a new forest as mydomain.com (can be anything, just remember what it is) > log into DC-1 VM >
server manager > click promote server to domain controller:
<p align="center"> 
<img src="https://i.imgur.com/EHl9qzq.png" height="80%" width="80%" 
<br /> 

Click add a new host and type in mydomain name into Root domain name
<p align="center"> 
<img src="https://i.imgur.com/em1Syi1.png" height="80%" width="80%" 
<p align="center"> 


Continue to click next, in domain controller options and directory services restore mode password, we are very likely never going to use this. (You may set up your own password)
<p align="center"> 
<img src="https://i.imgur.com/Ov1xImS.png" height="80%" width="80%" 
<p align="center"> 

Uncheck DNS Delegation > Continue with Install > We have succesfully downloaded Active Directory!
<p align="center"> 
<img src="https://i.imgur.com/Lfm72Gn.png" height="80%" width="80%" 
<br /> 
<p align="center">     
<img src="https://i.imgur.com/GdHA9v3.png" height="80%" width="80%" 
<p align="center">     





We've successfully succesfully installed Active Directory, we will continue on <a href="https://github.com/AnthonydcHo/addeployment"> deployment of Active Directory!   <br/>
