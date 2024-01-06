<h1>SIEM in Azure Sentinel</h1>

<h2>Description</h2>
The purpose of this project is to gain a better understanding and use of experience for Azure Sentinel (SIEM). This project helps the user walk through the use of various programs that coordinates everything together. Beginning with using a custom PowerShell script to extract metadata from Windows Event Viewer to be forwarded to a third party Application Programming Interface (API) in order to derive geolacation data. Next is using a Log Analytics Workspace (LAW) in Azure to ingest custom logs containing geographic information (latitude, longitude, stae/province, and country). Then configuring Custom Fields in LAW and using Azure Sentinel (Microsoft's cloud SIEM) workbork to display global attack data (RDP brute force) on a world map which is sorted by location and magnitude of attacks. 
<br />


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>Windows Event Viewer</b>
- <b>Log Analytics Workspace</b>
- <b>Azure Sentinel (SIEM)</b>
- <b>ipgeolocation.io</b>

<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2)
<h2>Program walk-through:</h2>
- <b>Azure account is required!</b>
- <b>Ensure your settings are matched with the images shown if following you're along <br>
<br>
 
<h3>Create a Virtual Machine </h3>
<img src="https://i.imgur.com/q6dHhvN.png" height="80%" width="100%"/>
- <b>Name your "Resource Group" which is where everything is going to be shared/connected among one another.<br>
- <b>Name your "Virtual Machine"<br>
- <b>Pick any designated "Region" where this VM is located<br>
 <br/>
 
<h4>Continued </h4>
<img src="https://i.imgur.com/BdRtnQs.png" height="80%" width="100%"/>
<br/>
- <b>Create your own "Username*" and "Password*" that will be used to login into the Virtual Machine<br>
- <b>Hit "Next: Disks>" and skip to "Next: Networing>" <br>
<br/>
 
<h5>Create a Virtual Machine: Networking </h5>
<img src="https://imgur.com/ZoSBTIj.png" height="80%" width="100%"/>
 <br/>
- <b>Hit "Advanced" in "NIC network security group" <br>
- <b>Hit "Create new" in "Configure network security group *" <br>
- <b>Essentially NIC network security group is simply a "firewall" that we are going to be adjusting and creating our own set of rules/settings to allow the Virtual machine to be open and targeted by other users globally. <br>
<br/>
 
<h8>Create a Virtual Machine: Create a Network Security Group </h8>
<img src="https://i.imgur.com/uIO79Mz.png" height="80%" width="100%"/>
 <br/>
- <b>"Add an inbount rule" that's highlighted in red<br>
- <b>Set "Destination port ranges" to a "*" symbol that represents for any/all port ranges<br>
- <b>Set "Priority" to somewhere low like 100, create a "Name" for this rule, and hit "Add" then "Ok"<br>
- <b>Lastly it will take you to the final screen in which you'll click "Review + Create" which will take some time to develop<br>
 <br/>
 
<h7>Create a Log Analytics Workspace</h7>
<img src="https://i.imgur.com/7nwaw5w.png" height="80%" width="100%">
<img src="https://i.imgur.com/VGej29r.png" height="80%" width="100%"/>
 <br/>
- <b>Select your account subscription and select the name you created for the "Resource Group"<br>
- <b>Create a simple name to remember (I used lawSIEM-LAB, law standing for Log Analytics Workspace) and select the "region" as West US 3, then hit "Review + Create" which will take some time to develop <br>
 <br/>
 
<h8>Microsoft Defender</h8>
<img src="https://i.imgur.com/lpZm8qW.png" height="80%" width="100%"/>
<br/>
- <b>In the search bar, navigate to "Microsoft Defender" <br>
- <b>Click on "Environment Settings" in the bottom left corner<br>
 <br/>
 
<h9>Data Collection settings</h9>
<img src="https://i.imgur.com/JGVjRKw.png" height="80%" width="100%" alt="Disk Sanitization Steps"/>
<br/>
- <b>In "Data Collection" click to ensure it captures "All Events"
<br/>

<h10>Connecting VM and LAW</h10>
<img src="https://i.imgur.com/C2PtMAI.png" height="80%" width="100%" alt="Disk Sanitization Steps"/>
<br/>
- <b>Navigate to LAW, click on "virtual machines," and click the designated VM name that you created<br>
<img src="https://i.imgur.com/2suLoqy.png" height="80%" width="100%" />
<br/>
- <b> Click "Connect" to connect the Virtual Machine and the Log Analytics Workspace, and this will take time to process <br>
<br/>

<h11> Virtual Machine IP Address</h11>
<img src="https://i.imgur.com/iGfapgl.png" height="80%" width="100%"/>
- <b>Go to your Virtual Machine (SIEM-LABZ) and record the "Public IP address" that's assigned<br>
<br/>

<h12>Remote Desktop Connection
<img src="https://i.imgur.com/5Epq5hV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
- <b>In your start menu on the computer, search for "Remote Desktop Connection" and paste the recorded Public IP address <br>
<br/>

<h13>Account Login</h13>
<img src="https://i.imgur.com/OvFIu8O.png" height="50%" width="90%" alt="Disk Sanitization Steps"/>
<br/>
- <b> Enter the username and password that was created when creating the Virtual Machine and hit OK<br>
<br/>

<h14>Event Viewer</h14>
<img src="https://i.imgur.com/mco7rWk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
- <b> RED: In the start menu of the Virtual Machine, search for "Event Viewer" and navigate to "Security" <br>
- <b> ORANGE: "Audit Failure" and "Task Category" represents a failed login attempt into the Virtual Machine with the date/time<br>
<br/>

<h15>Turning off the Firewall</h15>
<img src="https://i.imgur.com/l3jwTwc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
- <b> In the start menu of the Virtual Machine type "wf.msc" to navigate to the firewall<br>
<img src="https://i.imgur.com/dogSFHT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
- <b> RED: Click on Wireless Defender Firewall Properties <br>
- <b> ORANGE: In "Domain Profile," "Private Profile," "Public Profile," and "IPsec Settings;" switch the "On (recommended)" to "Off" across all tabs and hit "Apply" then "OK"
<br/>

<h16>IP Geolocation</h16>
<img src="https://i.imgur.com/63atKpQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/d7NtbOF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
- <b>In Microsoft Edge, go to this URL "[https://ipgeolocation.io/](https://ipgeolocation.io/)" and create an account<br>
- <b> Once signed in with your account, navigate to the "Dashboard" tab and copy the API Key<br>
<br/>

<h17>PowerShell ISE</h17>
<img src="https://i.imgur.com/0OF4AO2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
- <b> Open "Windows Powershell ISE" in your Windows Startup Menu<br>
<img src="https://i.imgur.com/IV0nKRh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/ms32orJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/rlr3NtO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/IgjHus7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/hUJAW8e.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/GTlXWSi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/XhFQPjM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/jIuSkPa.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/LuFTOY9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/A1p7UPT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/jNVrbUV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/RT0KlH3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/X1jj8Sv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
