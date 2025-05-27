
## Diagram

Below is our logical diagram for what we can expect from our Active Directory Lab
![ADLab drawio](https://github.com/user-attachments/assets/f50a67eb-d6ca-42c5-bfb4-13f46bf41d24)

## Steps Taken
1. Set up 3 virtual machines. In this lab, I decided to utilize Vultr to setup and host my VMs. I have 3 VMs: Windows Domain Controller (ADDC01), Windows Test Server (TEST), and Ubuntu Splunk Server (SPLUNK).

2. I then configured Active Directory Server on the ADDC01. I added a new user to the AD where the TEST server utilizes.

3. On the Ubuntu Server, I set up Splunk as the receiving server for telemetry and alerts. The sending servers include the Domain Controller and test server. Once Splunk was configured on those servers, we were able to use the Splunk Dashboard to view aggregated log entries. Afterward, I configured alerts to detect any unrecognized IP addresses accessing the ADDC01 or TEST servers.
