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

<p align="center">
Launch the utility: <br/>
<img src="https://i.imgur.com/q6dHhvN.png" height="80%" width="80%"/>
<br />
<br />
Select the disk:  <br/>
<img src="https://i.imgur.com/tcTyMUE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Enter the number of passes: <br/>
<img src="https://i.imgur.com/nCIbXbg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Confirm your selection:  <br/>
<img src="https://i.imgur.com/cdFHBiU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Wait for process to complete (may take some time):  <br/>
<img src="https://i.imgur.com/JL945Ga.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Sanitization complete:  <br/>
<img src="https://i.imgur.com/K71yaM2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Observe the wiped disk:  <br/>
<img src="https://i.imgur.com/AeZkvFQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
