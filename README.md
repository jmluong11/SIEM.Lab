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
<img src="https://i.imgur.com/JGVjRKw.png" height="80%" width="100%"/>
<br/>
- <b>In "Data Collection" click to ensure it captures "All Events"
<br/>

<h10>Connecting VM and LAW</h10>
<img src="https://i.imgur.com/C2PtMAI.png" height="80%" width="100%"/>
<br/>
- <b>Navigate to LAW, click on "virtual machines," and click the designated VM name that you created<br>
<img src="https://i.imgur.com/2suLoqy.png" height="80%" width="100%" />
<br/>
- <b> Click "Connect" to connect the Virtual Machine and the Log Analytics Workspace, and this will take time to process <br>
<br/>

<h11> Virtual Machine IP Address</h11>
<img src="https://i.imgur.com/iGfapgl.png" height="80%" width="100%"/>
- <b>Go to your Virtual Machine (SIEM-LABZ "Note there was a slight name change, but the principle still applies the exact same!") and record the "Public IP address" that's assigned<br>
<br/>

<h12>Remote Desktop Connection
<img src="https://i.imgur.com/5Epq5hV.png" height="80%" width="80%"/>
<br/>
- <b>In your start menu on the computer, search for "Remote Desktop Connection" and paste the recorded Public IP address <br>
<br/>

<h13>Account Login</h13>
<img src="https://i.imgur.com/OvFIu8O.png" height="50%" width="90%"/>
<br/>
- <b> Enter the username and password that was created when creating the Virtual Machine and hit OK<br>
<br/>

<h14>Event Viewer</h14>
<img src="https://i.imgur.com/mco7rWk.png" height="80%" width="100%"/>
<br/>
- <b> RED: In the start menu of the Virtual Machine, search for "Event Viewer" and navigate to "Security" <br>
- <b> ORANGE: "Audit Failure" and "Task Category" represents a failed login attempt into the Virtual Machine with the date/time<br>
<br/>

<h15>Turning off the Firewall</h15>
<img src="https://i.imgur.com/l3jwTwc.png" height="80%" width="100%"/>
<br/>
- <b> In the start menu of the Virtual Machine type "wf.msc" to navigate to the firewall<br>
<img src="https://i.imgur.com/dogSFHT.png" height="80%" width="100%"/>
- <b> RED: Click on Wireless Defender Firewall Properties <br>
- <b> ORANGE: In "Domain Profile," "Private Profile," "Public Profile," and "IPsec Settings;" switch the "On (recommended)" to "Off" across all tabs and hit "Apply" then "OK"<br>
<br/>

<h16>IP Geolocation</h16>
<img src="https://i.imgur.com/63atKpQ.png" height="80%" width="100%"/>
<img src="https://i.imgur.com/d7NtbOF.png" height="80%" width="80%"/>
<br/>
- <b>In Microsoft Edge, go to this URL "[https://ipgeolocation.io/](https://ipgeolocation.io/)" and create an account<br>
- <b> Once signed in with your account, navigate to the "Dashboard" tab and copy the API Key<br>
<br/>

<h17>PowerShell ISE</h17>
<img src="https://i.imgur.com/0OF4AO2.png" height="80%" width="100%"/>
<img src="https://i.imgur.com/IV0nKRh.png" height="80%" width="100%"/>
<br/>
- <b> Open "Windows Powershell ISE" in your Windows Startup Menu within the Virtual Machine<br>
- <b> RED: Copy and paste the code into the Powershell query from this link "[https://github.com/joshmadakor1/Sentinel-Lab/blob/main/Custom_Security_Log_Exporter.ps1](https://github.com/joshmadakor1/Sentinel-Lab/blob/main/Custom_Security_Log_Exporter.ps1)" <br>
- <b> ORANGE: In the "$API_Key" , delete the current API key in the quotation marks and paste the API key that was copied from the previous step and then run the script by clicking the green arrow<br>
- <b> GREEN: After a period of time; coordinates, attempted username, IP address, City/State/Province with COuntry, and time of attempted failed logins will appear in each line of purple text <br>
<br/>

<h18>File Saving failed RDP attempt logs</h18>
<img src="https://i.imgur.com/ms32orJ.png" height="80%" width="80%"/>
<br/>
- <b> Use "Notepad" from the start menu on YOUR PERSONAL PC (outside the Virtual Machine) and in the Virtual Machine, then copy and paste several lines of the recorded failed login attempts into the Notepad<br>
- <b> Save the file under the given name that's desired<br>
<br/>

<h19>Creating a Custom Log</h19>
<img src="https://i.imgur.com/rlr3NtO.png" height="80%" width="100%"/>
<img src="https://i.imgur.com/IgjHus7.png" height="80%" width="80%"/>
<br/>
- <b> Minimize or exit the Virtual Machine and go to your Virtual Machine through Microsoft Azure from your personal PC<br>
- <b> Navigate to "Tables" then click "New custom log (MMA based)"
- <b> Enter the file name saved from earlier (failed_rdp) and hit "Next"<br>
<br/>
<img src="https://i.imgur.com/hUJAW8e.png" height="80%" width="100%" />
- <b> Now the failed RDP attempts will be sorted and separated into its own respected line of text as shown above<br>
- <b> Hit "Next" <br>
<br/>
<img src="https://i.imgur.com/GTlXWSi.png" height="80%" width="100%"/>
- <b> Manually type the route of the "Notepad" file that was saved IN the VIRTUAL MACHINE<br>
<br/>
<img src="https://i.imgur.com/XhFQPjM.png" height="80%" width="100%"/>
- <b> Create a name of the Custom Log<br>
<br/>
<img src="https://i.imgur.com/jIuSkPa.png" height="80%" width="100%"/>
- <b> Ensure all steps are done properly and "Create"
<br/>
<br/>

<h20>Microsoft Sentinel<h20>
<img src="https://i.imgur.com/LuFTOY9.png" height="80%" width="100%"/>
<img src="https://i.imgur.com/A1p7UPT.png" height="80%" width="100%"/>
- <b> Navigate and create "Microsoft Sentinel" in Microsoft Azure<br>
- <b> RED: Go to Workbooks<br>
- <b> ORANGE: "+ Add workbook"<br>
<br/>

<h21>Failed RDP World Map</h21>
<img src="https://i.imgur.com/jNVrbUV.png" height="80%" width="100%"/>
- <b> RED: Create a Name for the workbook<br>
- <b> Also remove everything that's defaulted on the screen until you reach that "Azure Sentinel Report has no content"<br>
- <b> ORANGE: "Add query"<br>
<img src="https://i.imgur.com/RT0KlH3.png" height="80%" width="100%"/>
- <b> RED: Into the query copy and paste this code below:<br>
<br/>
<b> FAILED_RDP_WITH_GEO_CL 
| extend username = extract(@"username:([^,]+)", 1, RawData),
         timestamp = extract(@"timestamp:([^,]+)", 1, RawData),
         latitude = extract(@"latitude:([^,]+)", 1, RawData),
         longitude = extract(@"longitude:([^,]+)", 1, RawData),
         sourcehost = extract(@"sourcehost:([^,]+)", 1, RawData),
         state = extract(@"state:([^,]+)", 1, RawData),
         label = extract(@"label:([^,]+)", 1, RawData),
         destination = extract(@"destinationhost:([^,]+)", 1, RawData),
         country = extract(@"country:([^,]+)", 1, RawData)
| where destination != "samplehost"
| where sourcehost != ""
| summarize event_count=count() by latitude, longitude, sourcehost, label, destination, country <br>
<br/>
- <b> ORANGE: Run Query<br>
<br/>
<img src="https://i.imgur.com/X1jj8Sv.png" height="80%" width="100%"/>
- <b> RED: Match the Map Settings on the right side of the screen and hit "Apply"<br>
- <b> ORANGE: The map illustates all logged failed RDP attempts by different sized circles representing the magnitude of attempts. Different countries are separated by color, and the amount of recorded failed RDP attempts are listed below in the legend.<br>
- <b> ORANGE: After a certain period of time, Poland has the most failed RDP attempts (12.5k) that's represented by the red circle on the map<br/>
<br/>
<b>Congratulations! You have successfully created a Virtual Machine linked to a SIEM to observe live attacks through RDP Brute Force from various parts of the world. You are able to see how either individuals/bots attempt to Brute Force their way into a Host IP address through various usernames. In application into the real world, the massive amount of attempts are important to note of because one successful login attempt for a small or huge corporation can lead to leaked data which can cost the company millions of dollars if not billions<b> 
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
