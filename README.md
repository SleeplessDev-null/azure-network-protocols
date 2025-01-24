<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png"" height="90%" width="80%"  alt="Traffic Examination"/>
</p>

<h1>Azure Virtual Machines and Networking </h1>




<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<p align="center">
  First login to Microsoft Azure and create a resource group :
<img src="https://github.com/SleeplessDev-null/azure-network-protocols/blob/main/step_one.PNG?raw=true" height="90%" width="80%"  />
  <br />
  <br />
  Name the resource group and make sure to remember what region you have selected: 
<img src="https://github.com/SleeplessDev-null/azure-network-protocols/blob/main/Resource%20Group.PNG?raw=true" height="90%" width="80%"  />
  <br />
  <br />
  Next navigate to azure services or search for virtual machines :
<img src="https://github.com/SleeplessDev-null/azure-network-protocols/blob/main/Virtual%20Machine%20nav.PNG?raw=true" height="90%" width="80%"  />
  <br />
  <br />
  Now select create and choose the first option :
   <img src="https://github.com/SleeplessDev-null/azure-network-protocols/blob/main/VM%20set%20up-1%20.PNG?raw=true"  height="80%" width="80%"  />
  <br />
  <br />
  In this step make sure you have your resource group selected and the region is the same as the resource group.<br /> In the image drop down select windows 10 pro for this VM. 
<img src="https://github.com/SleeplessDev-null/azure-network-protocols/blob/main/VM%20set%20up%202%20.PNG?raw=true" height="90%" width="80%"  />
  <br />
  Next select the size, anything that has 2 vcpus and at least 8 gib of memory.  <br />
  Username and password can be anything you like,(easy to remember) be sure to check the box at the bottom
  <img src="https://github.com/SleeplessDev-null/azure-network-protocols/blob/main/VM%20set%20up%203.PNG?raw=true" height="90%" width="80%"  />
<br />
<br />
Now on the bottom click next until you get to networking.Then create a new virtual network be sure to remember the name and leave the rest default, click review + create. Note sometimes you may have to reselect the resource group or the image for it to pass review.
  <img src="https://github.com/SleeplessDev-null/azure-network-protocols/blob/main/Networking%20set%20up%20for%20vm.PNG?raw=true" height="90%" width="80%"  />
<br />
<br />
  For this network test we need 2 virtual machines so next we will do the same process but select a linux image this time. Make sure to select password at the authentication type section. Note: use the same region and resource group as the other VM.
  <img src="https://github.com/SleeplessDev-null/azure-network-protocols/blob/main/Linux-vm-setup.PNG?raw=true" height="90%" width="80%"  />
<br />
<br />
</p>

