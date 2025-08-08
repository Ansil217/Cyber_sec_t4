# Cyber_sec_t4
Setup and Use a Firewall on Windows/Linux
Task 4: Firewall Configuration and Testing (Windows)

Objective
Configure the firewall to block a specific port (Telnet – port 23), test the rule, and restore the firewall to its original state.

NOTE: I use my windows os and cmd instead of kali 



Steps Performed

1. Open Firewall Configuration Tool
- Press Start, type cmd, right-click Command Prompt, and select Run as administrator.



2. List Current Firewall Rules
cmd
netsh advfirewall firewall show rule name=all | more


3. Add Rule to Block Inbound Traffic on Port 23 (Telnet)
cmd
netsh advfirewall firewall add rule name="Block Telnet 23" dir=in action=block protocol=TCP localport=23

4. Test the Rule Locally
Run PowerShell as Administrator:
Test-NetConnection -ComputerName 127.0.0.1 -Port 23
Expected Result: TcpTestSucceeded : False

6. Remove the Test Block Rule
netsh advfirewall firewall delete rule name="Block Telnet 23" protocol=TCP localport=23


7. Document Commands Used
Commands run during this task:

netsh advfirewall firewall show rule name=all | more
netsh advfirewall firewall add rule name="Block Telnet 23" dir=in action=block protocol=TCP localport=23
powershell Test-NetConnection -ComputerName 127.0.0.1 -Port 23
netsh advfirewall firewall delete rule name="Block Telnet 23" protocol=TCP localport=23

9. Summary: How Firewall Filters Traffic
A firewall examines network packets and applies rules to determine whether to allow or block traffic.
Rules can filter by:
Direction: inbound or outbound
Protocol: TCP, UDP, etc.
Port number
IP address

In this test:
We blocked inbound TCP traffic to port 23.
The connection test failed, showing the firewall enforced the rule.
After removing the rule, the port was no longer blocked.

