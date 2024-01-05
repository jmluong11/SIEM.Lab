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
<br>
<br>Create a Virtual Machine </br>
<img src="https://i.imgur.com/q6dHhvN.png" height="80%" width="80%"/>
- <b>Name your "Resource Group" which is where everything is going to be shared/connected among one another.<br>
- <b>Name your "Virtual Machine"<br>
- <b>Pick any designated "Region" where this VM is located<br>
<b>Select the disk:  <br/>
<img src="https://i.imgur.com/BdRtnQs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Enter the number of passes: <br/>
 <p align="center"> <br/>
<img src="https://imgur.com/ZoSBTIj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <p align="center"> Create a Virtual Machine <br/>
<img src="https://i.imgur.com/uIO79Mz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
   <p align="center"> Create a Virtual Machine <br/>
<img src="https://i.imgur.com/7nwaw5w.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/VGej29r.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/JGVjRKw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/C2PtMAI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/lq7Td4H.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/iGfapgl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/5Epq5hV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/OvFIu8O.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/mco7rWk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/l3jwTwc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/dogSFHT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/0OF4AO2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/63atKpQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/d7NtbOF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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
