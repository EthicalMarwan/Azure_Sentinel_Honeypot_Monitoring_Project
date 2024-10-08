# SIEM Implementation on Azure with Microsoft Sentinel and Honeypot Deployment
<div>
    <img src= "https://github.com/user-attachments/assets/37ac5b65-e0dd-42d0-9947-cc28f434a627" />
</div>

## Project Overview
In this project, I set up an Azure-based Security Information and Event Management (SIEM) system with Microsoft Sentinel to monitor a virtual machine honeypot. The system captured real-time data on RDP Brute Force attacks from various global sources, utilizing a custom PowerShell script for geolocation mapping of the attackers.
<div>
    <img src= "https://github.com/user-attachments/assets/30fd348f-afae-4572-a6a2-40eca4c2f7dc" />
</div>

### Azure Sentinel Honeypot Project Steps:
- **Virtual Machiine initialization:** Configured a virtual machine (VM) with a Windows 10/11 image, setting the stage for the honeypot environment.
- **Deliberately Vulnerable Configuration:**
    - **Network Configuration:** Adjusted the firewall settings to accept all incoming connections, ensuring the VM was exposed to potential attacks.
    -** Defender Configuration:** Disabled the Windows Defender Firewall, further making the VM vulnerable.
- This setup is intentionally insecure to evaluate Azure Sentinel’s capabilities and to get a simulated real life brute force attack.
<div>
    <img src= "https://github.com/user-attachments/assets/ad1008e6-bb1e-4b1a-b33f-ffcf166db450" />
</div>

### Setting Up Log Analysis and Data Collection: 
- **Log Analytics Workspace Creation:** Then I set up a dedicated Log Analytics Workspace in Azure to serve as the central point for collecting and analyzing security logs.

### Microsoft Defender for Cloud Configuration:
- **Environment Settings:** Enabled the "Servers" option in Microsoft Defender for Cloud to focus on monitoring the VM.
- **Data Collection:** Configured the collection of "All Events" from the VM, capturing comprehensive security logs for detailed analysis.

### Azure Sentinel Integration:
- **Integration:** Linked Azure Sentinel with the Log Analytics Workspace to facilitate data ingestion and enable real-time security monitoring and analysis.

### RDP Attack Simulation and Data Collection:
- **Simulated Attacks:** Conducted simulated failed RDP logins using incorrect passwords to generate and capture security log events related to attempted intrusions.
- **PowerShell Script:** Utilized a custom PowerShell script to extract data from the Windows Event Log, specifically focusing on failed RDP attempts. The script was designed to query an external API for geolocation data of the attackers' IP addresses.

### API Key Setup and Script Configuration:
- **IPGeolocation API:** Acquired an API key from IPGeolocation.io for translating IP addresses into geographic locations. Integrated this key into the PowerShell script to enrich the log data with location information.
<div>
    <img src= "https://github.com/user-attachments/assets/5c950a16-f036-4fe9-9b3e-34fb2ebf1e15" />
</div>

### Executing the PowerShell Script:
- **Script Execution:** Ran the Security_Log_Exporter.ps1 script, which generated detailed log files stored at C:\ProgramData containing information about the failed RDP attempts and the corresponding attacker locations.

### Log File Management:
- **Log Upload:** Copied and uploaded the generated log files to the Azure Log Analytics Workspace. These files were designated as custom logs for further analysis.
- **Custom Log Configuration:** Configured Azure Sentinel to recognize and process the custom logs, ensuring that the data was accurately ingested and available for query.
<div>
    <img src= "https://github.com/user-attachments/assets/81a83d5d-384d-474e-9026-a7df3972edde" />
</div>

### Data Extraction and Visualization:
- **KQL Script:** Deployed a Kusto Query Language (KQL) script within Azure Sentinel to extract and structure the data from the custom logs. This script focused on isolating pertinent details such as IP addresses and geographic locations.
<div>
    <img src= "https://github.com/user-attachments/assets/e0148f68-54f2-4a87-9ccf-5a13568d5918" />
</div>

- **Map Visualization:** Used Azure Sentinel’s visualization tools to create a dynamic map that plotted the locations of the RDP attack attempts. This real-time visualization provided clear insights into the origin of the threats and allowed for better understanding and response to the malicious activities.
<div>
    <img src= "https://github.com/user-attachments/assets/987f3237-b896-4ac9-9718-a894f3c1a08f" />
</div>

- The visualization map above indicates that initially, RDP attacks were originating from a single geographical location. However, after leaving the firewall open for a day, the updated visualization map reveals that attacks are now occurring from multiple geographical locations.
<div>
    <img src= "https://github.com/user-attachments/assets/5293a908-3d2b-4567-a107-521ae36ad1bc" />
</div>

## Conclusion
Through this project, I demonstrated the capability to set up a comprehensive SIEM solution on Azure, effectively using Microsoft Sentinel for advanced threat monitoring and analysis. The deployment of the honeypot and real-time geolocation visualization highlighted my proficiency in managing and responding to security incidents, showcasing a robust approach to enhancing cybersecurity defenses.
