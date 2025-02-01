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


<h2>This is a walkthrough on how to deploy virtual machines with the use of azure. We also will observe network traffic of different network protocols with wireshark as our tool.  </h2>



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
  <br />
  <img src="https://github.com/SleeplessDev-null/azure-network-protocols/blob/main/Linux-vm-setup.PNG?raw=true" height="90%" width="80%"  />
<br />
<br />
  Now that both are created check to make sure both are running. click on the windows vm to get the public ip address.
<br />
  <img src="https://github.com/SleeplessDev-null/azure-network-protocols/blob/main/VM%20Select.PNG?raw=true" height="90%" width="80%"  />
<br />
<br />
Copy the VM ip address, right click on your pc's windows symbol on the lower left and search for remote desktop 
 <img src="https://github.com/SleeplessDev-null/azure-network-protocols/blob/main/Windows%20IP.PNG?raw=true" height="90%" width="80%"  />
<br />
<br />
In remote desktop paste the VM's ip address then click connect 
<img src="https://github.com/SleeplessDev-null/azure-network-protocols/blob/main/IP%20for%20Remote%20Desktop.PNG?raw=true" height="90%" width="80%"  />
<br />
<br />
Then sign in with the VM's username and password. NOTE this will be the windows VM :
<img src="https://github.com/SleeplessDev-null/azure-network-protocols/blob/main/Login%20to%20the%20windows%20vm.PNG?raw=true" height="90%" width="80%"  />
<br />
<br />
Once you are signed in go to Microsoft edge browser and search for wireshark, make sure its from the official site like in the picture and run the exe leave everything default during the install
<br />
<img src="https://github.com/SleeplessDev-null/azure-network-protocols/blob/main/Wireshark%20Download.PNG?raw=true" height="90%" width="80%"  />
<br />
<br />
Once installed the program should look this. Click the ethernet option and then click the blue fin on the top left this will enable packet capture:
<img src="https://github.com/SleeplessDev-null/azure-network-protocols/blob/main/Starting%20wireshark.PNG?raw=true" height="90%" width="80%"  />
<br />
<br />
 Now in the filter bar type icmp and press enter. Then go to the windows search bar and run powershell as administrator, Once powershell is open type ping and enter the private ip of the linux VM then press enter. This will show the icmp traffic between the windows and linux machines:
<br />
<img src="https://github.com/SleeplessDev-null/azure-network-protocols/blob/main/Pinging%20the%20linux%20vm.PNG?raw=true" height="90%" width="80%"  />
<br />
<br />
you can also ping websites by using ping in the same way as you did the linux VM. example:
<img src="https://github.com/SleeplessDev-null/azure-network-protocols/blob/main/Pinging%20a%20website%20in%20the%20windows%20vm.PNG?raw=true" height="90%" width="80%"  />
<br />
<br />
Now we want to initiate a continuous ping to the linux VM,Inside of powershell run ping -t(your linux private ip) Then press enter, when you want to stop it press Ctrl + C:
<br />
<img src="https://github.com/SleeplessDev-null/azure-network-protocols/blob/main/Continuous%20ping.PNG?raw=true" height="90%" width="80%"  />
<br />
<br />
Before we stop the ping we need to edit the Network Security Group so back in azure go to your linux VM, click on network then network settings : 
<br />
<img src="https://github.com/SleeplessDev-null/azure-network-protocols/blob/main/Network%20inbound%20stop%20rule1.PNG?raw=true" height="20%" width="30%"  />
<br />
<br />
The setting to add the rule should look like this, click create port rule. we are doing this to show what it looks like when the traffic is blocked :
<br />
<img src="https://github.com/SleeplessDev-null/azure-network-protocols/blob/main/Network%20security%20inbound%20rule.PNG?raw=true" height="90%" width="80%"  />
<br />
<br /> 
Your port rule should look like this when setting it:
<br /> 
<img src="https://github.com/SleeplessDev-null/azure-network-protocols/blob/main/Network%20security%20rule%202.PNG?raw=true" height="90%" width="80%"  />
<br />
<br />  
Now back inside of the windows VM the inbound connection should timeout which should show inside of powershell. After this go back to the port rule section and in azure and delete the Network Security Group rule you created, should be a trash bin button next to the rule, click that to delete it and the connection should run again 
<br />  
<img src="https://github.com/SleeplessDev-null/azure-network-protocols/blob/main/Disable%20inbound%20connections.PNG?raw=true" height="90%" width="80%"  /> 
<br />
<br />
 Now we will ssh into the linux VM be sure to filter ssh in wireshark, we do this by typing ssh labuser-8@<private IP address> in powershell. Note this would be the username of your linux VM followed by the @ and private ip.When this is done you will be connected to the linux VM terminal and anything you type will show as traffic in wireshark. type logout in powershell and press enter to disconnect.
<br />
<img src="https://github.com/SleeplessDev-null/azure-network-protocols/blob/main/Wireshark%20ssh%20test.PNG?raw=true" height="90%" width="80%"  /> 
<br />
<br />
We will now in powershell type ipconfig /renew to attempt to give our VM a new ip address, make sure to have dhcp filterd in wireshark 
<br />
<img src="https://github.com/SleeplessDev-null/azure-network-protocols/blob/main/DHCP%20traffic.PNG?raw=true" height="90%" width="80%"  /> 
<br />
<br />
Now in wireshark filter for dns. In powershell type nslookup (any well known website) and the ip of that website should show up followed by some traffic showing in wireshark:
<br />
<img src="https://github.com/SleeplessDev-null/azure-network-protocols/blob/main/DNS%20traffic.PNG?raw=true" height="90%" width="80%"  /> 
<br />
<br />
Head back to wireshark, we will be filtering for rdp but instead of typing rdp in the filter bar we will type tcp.port == 3389, after you should see a lot of spam in wireshark. This is because wireshark is picking up the traffic of everything displayed in the VM including your mouse movements.
<br />
<img src="https://github.com/SleeplessDev-null/azure-network-protocols/blob/main/RDP%20traffic.PNG?raw=true" height="90%" width="80%"  /> 
<br />
<br />
   
</p>
<br />
<br />
With that this concludes the walkthrough I hope with this guide you have learned a bit about azure, virtual machines, and networking. To end all of this off be sure to delete the azure resource groups with the virtual machines so you won't be charged for the usage.


