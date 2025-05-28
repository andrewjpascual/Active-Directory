
## Diagram

Below is our logical diagram for what we can expect from our Active Directory Lab
![ADLab drawio](https://github.com/user-attachments/assets/f50a67eb-d6ca-42c5-bfb4-13f46bf41d24)

## Steps Taken
1. Set up 3 virtual machines. In this lab, I decided to utilize Vultr to setup and host my VMs. I have 3 VMs: Windows Domain Controller (ADDC01), Windows Test Server (TEST), and Ubuntu Splunk Server (SPLUNK).

2. I then configured Active Directory Server on the ADDC01. I added a new user to the AD where the TEST server utilizes.

3. On the Ubuntu Server, I set up Splunk as the receiving server for telemetry and alerts. The sending servers include the Domain Controller and test server. Once Splunk was configured on those servers, we were able to use the Splunk Dashboard to view aggregated log entries. Afterward, I configured alerts to detect any unrecognized IP addresses accessing the ADDC01 or TEST servers. I also setup a Slack channel to monitor these alerts and post them automatically as they come in.

4. Set up an automated workflow that consists of an alert from Splunk when detecting an unrecognized IP address to the Test server. Once completed, it will identify the user and create an alert within my Slack alerts channel. This will also send an automated email to the SOC Analyst and ask if they would like to disable the compromised Active Directory user account. If confirmed, then the user will be disabled through the Domain Controller and another automated alert will be sent to the Slack alerts channel specifying the exact account that has been disabled.
