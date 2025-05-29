<!-- Logical Diagram -->
## Diagram

Below is our logical diagram for what we can expect from our Active Directory Lab
![ADLab drawio](https://github.com/user-attachments/assets/f50a67eb-d6ca-42c5-bfb4-13f46bf41d24)

<!-- Steps -->
## Steps Taken
1. Virtual Machine Setup
I deployed three virtual machines using Vultr to host and manage the lab environment. The VMs include:

* ADDC01: A Windows Server configured as the Active Directory Domain Controller
* TEST: A Windows-based test server
* SPLUNK: An Ubuntu server running Splunk for SIEM purposes

2. On ADDC01, I installed and configured Active Directory Services. I also created a new user account in Active Directory, which the TEST server utilizes for authentication and access.

3. On the Ubuntu-based SPLUNK server, I installed and configured Splunk to act as the central receiver for telemetry and alert data. Both the Domain Controller (ADDC01) and test server (TEST) were set up as log senders. With the Splunk Dashboard, I was able to view and analyze aggregated log data from all sources. I then configured alerts to trigger on any unrecognized IP addresses attempting to access ADDC01 or TEST. These alerts are automatically forwarded to a dedicated Slack channel for real-time monitoring.

4. I implemented an automated incident response workflow triggered by Splunk alerts for unrecognized IP access to the TEST server. Upon detection:
* The system identifies the user account involved.
* An alert is posted to the Slack monitoring channel.
* An automated email is sent to the SOC Analyst, asking whether the associated Active Directory user should be disabled.
* If the analyst confirms, the account is disabled via the Domain Controller.
* A follow-up alert is posted in the Slack channel, detailing the specific user account that was disabled.

<!-- Images -->
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

<!-- Challenges -->
## Challenges
1. Cost of this home lab. I kept this lab up online for about a week and it cost about $34. I was able to get a free $300 credit for servers by signing up through the MyDFIR Referral (Vultr referral link below) 

2. Shufflr bugs. I kept running into authentication and indexing errors on the Shufflr application (first image in the gallery). Most of this was either resolved by refreshing the page or reloading the workflow. I suspect it was due to caching and since I would test different parts of the workflow individually, this may have caused such errors.

<!-- CONTACT -->
## Contact

Andrew Pascual - andrewjpascual@gmail.com

https://github.com/andrewjpascual/HostScanner


<!-- ACKNOWLEDGMENTS -->
## Acknowledgments

* [MyDFIR](https://www.mydfir.com/)
* [Best-README-Template](https://github.com/othneildrew/Best-README-Template)
* [Vultr Referral](https://www.vultr.com/?ref=9765025-9J) *New users only
