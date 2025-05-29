
## Diagram

Below is our logical diagram for what we can expect from our Active Directory Lab
![ADLab drawio](https://github.com/user-attachments/assets/f50a67eb-d6ca-42c5-bfb4-13f46bf41d24)

## Steps Taken
1. Set up 3 virtual machines. In this lab, I decided to utilize Vultr to setup and host my VMs. I have 3 VMs: Windows Domain Controller (ADDC01), Windows Test Server (TEST), and Ubuntu Splunk Server (SPLUNK).

2. I then configured Active Directory Server on the ADDC01. I added a new user to the AD where the TEST server utilizes.

3. On the Ubuntu Server, I set up Splunk as the receiving server for telemetry and alerts. The sending servers include the Domain Controller and test server. Once Splunk was configured on those servers, we were able to use the Splunk Dashboard to view aggregated log entries. Afterward, I configured alerts to detect any unrecognized IP addresses accessing the ADDC01 or TEST servers. I also setup a Slack channel to monitor these alerts and post them automatically as they come in.

4. Set up an automated workflow that consists of an alert from Splunk when detecting an unrecognized IP address to the Test server. Once completed, it will identify the user and create an alert within my Slack alerts channel. This will also send an automated email to the SOC Analyst and ask if they would like to disable the compromised Active Directory user account. If confirmed, then the user will be disabled through the Domain Controller and another automated alert will be sent to the Slack alerts channel specifying the exact account that has been disabled.

## Gallery Walkthrough

Automated Workflow Diagram. This is all initiated through a Webhook event when we receive an alert in Splunk.
![Shuffler2](https://github.com/user-attachments/assets/dffa80ee-6bbe-4fad-b894-1d31de822e20)

Attacker Successfully authenticates into my Test server:
![bigattack](https://github.com/user-attachments/assets/cb63170b-9e08-4e86-8233-6fb0ec7b33af)


Receiving the Alert in Splunk
![Splunk Alert](https://github.com/user-attachments/assets/d08fdb4a-23c2-4429-9f18-88e6244bb110)

Automated Alert sent to Slack; We see a user named Steven has an unauthorized login
![FirstSlackAlert](https://github.com/user-attachments/assets/ea8d6a66-278a-4d18-aaeb-666aee826489)


Email sent to SOC Analyst for user input and determine next action
![User Input](https://github.com/user-attachments/assets/01e38d16-00aa-4161-9a62-9ad3114396a5)

After confirming to disable (true); We notice that in our example Steven has been disabled
![DisabledINActiveDirectory](https://github.com/user-attachments/assets/8642523b-7b8a-48af-9c19-e9f4ed82fe99)

Disabled alert sent to Slack; Steven has been disabled
![Slack Alert](https://github.com/user-attachments/assets/748dc4b6-d75b-4fc1-b923-e4b47f0c1515)


