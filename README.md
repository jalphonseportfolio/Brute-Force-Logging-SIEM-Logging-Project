# Brute-Force-Logging-SIEM-Logging-Project:
<h2>Failed RDP to IP Geolocation Information</h2>
<h3>Description: </h3>

The Powershell script in this repository parses out Windows Event Log information for failed RDP attacks and uses a third-party API to collect geographic information about the attackers' location. <br/>

<b>I performed the following tasks in Azure Sentinel (Microsoft’s cloud SIEM): <br/>
a. Create, configure, and deploy an Azure virtual machine. <br/>
b. Created a log analytics workspace within Azure to monitor and organize RDP traffic logs. <br/>
c. Used custom PowerShell script to extract metadata from Windows Event Viewer to be forwarded to third-party API to derive geolocation data of RDP traffic. <br/>
d. Configured Log Analytics Workspace in Azure to ingest custom logs containing geographical information like latitude, longitude, state, province, and country. <br/>
e. Designed an Azure Sentinel workbook to display global attack data (RDP Brute Force) on a world map according to physical location and magnitude of attacks. <br/>

The script is used in this project, where I set up Azure Sentinel (SIEM) and connected it to a live virtual machine that acts as a honey pot.
We will observe live attacks (RDP Brute Force) from all around the world. I will use a custom PowerShell script to look up the attackers' Geolocation information and plot it on an Azure Sentinel Map!

<h2>Languages Used</h2>

- <b>PowerShell:</b> Extract RDP failed logon logs from Windows Event Viewer 

<h2>Utilities Used</h2>

- <b>ipgeolocation.io:</b> IP Address to Geolocation API

<h2>Attacks from China coming in; Custom logs being output with geodata</h2>
Running Powershell script in Windows Powershell ISE: <br>
This PowerShell script reads Microsoft Event Viewer and sends a record of all failed RDP requests to Azure Sentinal so that it can be recorded by the heat map. <br> 
<img src="https://github.com/user-attachments/assets/ca13cd7b-d1af-4e33-b006-826f117ac9eb" />

Here is what the API call was returning: <br>
<img src="https://github.com/user-attachments/assets/51b71121-c975-4fa2-905e-ea8d9b52b1e4" />

<h2>World map of incoming attacks after 4 hours (built custom logs including geodata)</h2>
<img src="https://github.com/user-attachments/assets/b6d79515-5cf6-4434-b46e-7c6bb6b017e6" />

<h2>World map of incoming attacks after 24 hours</h2>
<img src="https://github.com/user-attachments/assets/06a559ab-6943-44eb-ab0f-19705c840e01" />

<h2>World map of incoming attacks after 48 hours</h2>
<img src="https://github.com/user-attachments/assets/83f26499-e66c-4c12-a458-be034c7d5b5b" />

<h2>World map of incoming attacks after 72 hours</h2>
<img src="https://github.com/user-attachments/assets/e1197f8e-8368-4ea7-a1ec-ddcde7b018d1" /> <br>

In total, I was able to record 4,376 failed login attempts over the last 72 hours. <br>
Here’s what my map looks like after about 3 days of letting the system run. <br>
The country with the highest amount of attacks was the Philippines with 1,851 login attempts recorded followed by Panama, France, and Belize ranging from 935 to 355 attempts trying to access my Azure cloud VM. <br>

<h2>Conclusion</h2>
This project was enjoyable and informative. It allowed me to test out theoretical concepts in a real-life scenario. After reviewing the PowerShell log, I could see that the hackers often tried to access the VM by using common usernames such as “administrator” and “admin”. Keeping this in mind, we can conclude that it is a good idea to use unique usernames and passwords when creating any server that is publically facing the internet.



