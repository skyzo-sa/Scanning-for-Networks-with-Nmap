![image](https://github.com/user-attachments/assets/75a38a5e-96dd-416e-be09-d5ca966c7226)# Linux Lab – Scanning for Networks with Nmap
## Objective

The objective of this script is to block incoming network traffic from a list of specified IP addresses using the iptables firewall in Linux. It automates the process of applying IP-based traffic restrictions for network security purposes.

### Job Skills Learned

- Linux System Administration
- Managing firewall rules using iptables.
- Bash Shell Scripting
- Using loops and conditional commands.
- Network Security and Access Control
- Automation and Efficiency


### Tools Used

- Linux Terminal Command Line Interface (CLI)
- Bash Shell
- iptables (Firewall)
- Networking Commands: ping, ifconfig
- VMware Tools: Linux VM

### STEPS

##########################
## NMAP
##########################
 
##** SCAN ONLY YOUR OWN HOSTS AND SERVERS !!! **##
## Scanning Networks is your own responsibility ##
![image](https://github.com/user-attachments/assets/8877f4d6-ec2c-46cf-92a0-87525e55508f)
 
 
# Syn Scan - Half Open Scanning (root only)
`nmap -sS 192.168.18.103`
![image](https://github.com/user-attachments/assets/be63e656-396f-40d4-90c7-3750166d51d1)
 
 
# Connect Scan
`nmap -sT 192.168.0.1`
 ![image](https://github.com/user-attachments/assets/15c93ea7-c924-4c9a-9e37-e23a8f69939f)
 

# Scanning all ports (0-65535)
`nmap -p- 192.168.18.103`
![image](https://github.com/user-attachments/assets/48dcdd15-3e34-45dc-baee-3751949f05ae)
  

# Specifying the ports to scan
`nmap -p 20,22-100,443,1000-2000 192.168.18.103`
![image](https://github.com/user-attachments/assets/58536caf-f422-47f3-88e1-362af90b2907)
 
 
# Scan Version
`nmap -p 22,80 -sV 192.168.18.103`
![image](https://github.com/user-attachments/assets/cd4c46d5-bcb0-4ce4-ab3a-b56d60ab0c31)
 
 
# Ping scanning (entire Network)
`nmap -sP 192.168.18.0/24`
![image](https://github.com/user-attachments/assets/b060b0cf-ab35-4ea1-acd8-a9cc2f99242e)
 
 
# Treat all hosts as online -- skip host discovery
`nmap -Pn 192.168.18.0/24`
![image](https://github.com/user-attachments/assets/0a421877-7dc0-4859-ad88-802a23c31ff9)
 
 
# Excluding an IP
`nmap -sS 192.168.18.0/24 --exclude 192.168.18.103`

![image](https://github.com/user-attachments/assets/88d93c03-a758-4e99-abb3-dcbbebb8bae5)
 
 
# Saving the scanning report to a file
`nmap -oN output.txt 192.168.18.103`
![image](https://github.com/user-attachments/assets/db7133d2-4ff6-4fed-a9cf-0bfe70386701)
  

# OS Detection
`nmap -O 192.168.18.103`
![image](https://github.com/user-attachments/assets/447572e0-c2cd-4ce5-a52a-82397f2a9455)
 
 
# Enable OS detection, version detection, script scanning, and traceroute
`nmap -A 192.168.18.103`
![image](https://github.com/user-attachments/assets/d551a7af-4fd0-4e49-8fc2-4e6d1dbe5233)
 
 
https://nmap.org/book/performance-timing-templates.html
 
-T paranoid|sneaky|polite|normal|aggressive|insane (Set a timing template)
These templates allow the user to specify how aggressive they wish to be, while leaving Nmap to pick the exact
timing values. The templates also make some minor speed adjustments for which fine-grained control options do
not currently exist.
 
# -A OS and service detection with faster execution
`nmap -A -T aggressive cloudflare.com`
![image](https://github.com/user-attachments/assets/3b49b005-20f7-4427-97c0-98147c7f2e77)
 
 
# Using decoys to evade scan detection
`nmap -p 22 -sV 192.168.18.103 -D 192.168.18.1,192.168.18.21,192.168.18.100`
![image](https://github.com/user-attachments/assets/eac3d6ee-c15a-43a6-9f63-e5c2cb8771ee)
  
 
# Reading the targets from a file (ip/name/network separeted by a new line or a whitespace)

1. Ensure hosts.txt Exists and Is Formatted Correctly
Each target should be on a new line or separated by whitespace.

vim hosts.txt

Example of hosts.txt:

192.168.18.103
192.168.18.5
192.168.18.64
www.sky29.co.za
![image](https://github.com/user-attachments/assets/606c32aa-7f56-47f6-9d8f-1453620c446b)

 

# Check the file contents using:

`cat hosts.txt`
![image](https://github.com/user-attachments/assets/50f19cad-cc6e-424c-8ee7-7d887cdd7ee7)
 
2. Run the Command with Proper Permissions

`sudo nmap -p 80 -iL hosts.txt `
 
 
# Exporting to out output file and disabling reverse DNS
`nmap -n -iL hosts.txt -p 80 -oN output.txt`
 
