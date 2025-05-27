
## Diagram

Below is our logical diagram for what we can expect from our Active Directory Lab
![ADLab drawio](https://github.com/user-attachments/assets/f50a67eb-d6ca-42c5-bfb4-13f46bf41d24)

## Steps Taken
1. Set up 3 virtual machines. In this lab, I decided to utilize Vultr to setup and host my VMs. I have 3 VMs: Windows Domain Controller (ADDC01), Windows Test Server (TEST), and Ubuntu Splunk Server (SPLUNK).

2. I then configured Active Directory Server on the ADDC01. I added a new user to the AD where the TEST server utilizes.

3. On the Ubuntu Server, I then setup Splunk as the Receiving Server for Telemetry and alerts. The sending servers would be the Domain Controller and Test Servers. Once Splunk has been configured on the sending servers, we can utilize the Splunk Dashboard and see our aggregated log entries. Once completed, I setup alerts for any unrecognized IPs accessing my ADDC01 or TEST servers.
