# task-4-CS
1. Open Firewall Configuration Tool
Windows:
Open Control Panel > System and Security > Windows Defender Firewall

Click Advanced settings on the left to open the Windows Defender Firewall with Advanced Security console.
--------------------------------------------->
 2. List Current Firewall Rules
Windows:
In the advanced settings window, check Inbound Rules and Outbound Rules for active entries.
----------------------------------------------->
3. Add a Rule to Block Inbound Traffic on Port 23 (Telnet)
Windows:
Go to Inbound Rules > New Rule.

Choose Port > Select TCP > Enter port 23.

Select Block the connection.

Apply to all profiles and name it (e.g., Block Telnet
----------------------------------------------->
4. Test the Rule (Telnet Port 23)
Locally (if Telnet is installed and running):
bash
Copy
Edit
telnet localhost 23
Should fail to connect.

Remotely:
bash
Copy
Edit
telnet <your-ip-address> 23
Connection should be refused or time out.
------------------------------------------------->
5. Add Rule to Allow SSH (Port 22, for Linux)
Linux (UFW):
bash
Copy
Edit
sudo ufw allow 22
This ensures remote SSH access is still permitted.

Windows:
No action needed unless you're running SSH server on Windows (rare). If so, allow port 22 under inbound rules.
--------------------------------------------------->
6. Remove the Test Block Rule
Windows:
Go to Inbound Rules > Right-click the Block Telnet rule > Delete.

Linux (UFW):
First, list the rules with numbers:

bash
Copy
Edit
sudo ufw status numbered
Then delete the rule (e.g., if it's rule #2):

bash
Copy
Edit
sudo ufw delete 2
-------------------------------------------------------->
7. Documented Commands or GUI Steps Used
Linux (UFW):
bash
Copy
Edit
sudo ufw status verbose
sudo ufw deny in 23
sudo ufw allow 22
sudo ufw delete <rule-number>
Windows (GUI):
Open Windows Defender Firewall with Advanced Security.

Add new inbound rule for port 23 → block.

Remove rule by right-click > Delete.
-------------------------------------------------------------->
🛡️ 8. Summary: How Firewalls Filter Traffic
Firewalls monitor and control network traffic based on pre-defined rules. They serve as a barrier between trusted and untrusted networks.

Inbound rules manage what external connections are allowed in.

Outbound rules control what internal connections can go out.

Rules can be set based on port, protocol, IP address, or application.

Block rules deny unwanted access (e.g., Telnet on port 23).

Allow rules ensure essential services remain reachable (e.g., SSH on port 22).




















