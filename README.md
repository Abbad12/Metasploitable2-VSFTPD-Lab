# Metasploitable2-VSFTPD-Lab
Built a virtual penetration testing environment using VMware, Kali Linux and Metasploitable2. Conducted service enumeration, vulnerability identification and exploitation using Metasploit Framework.

# Lab Environment

Attacker:
-	 Kali Linux

Target:
-	 Metasploitable2

Virtualization:
-	 VMware Workstation

Network:
-	 Host Only  

# Service Enumeration:
Objective 
-	Discover open ports and identify running services.

Command
-	nmap -sV 192.168.233.129

Result 
-	Finding several running services 

| Port | Service | Version | Priority |
| :--- | :--- | :--- | :--- |
| 21 | FTP | vsftpd 2.3.4 | Very High |
| 22 | SSH | OpenSSH 4.7 | Middle |
| 80 | HTTP | Apache 2.2.8 | High |
| 139 | SMB | Samba | High |
| 445 | SMB | Samba | High |
| 3306 | MySQL | 5.0 | Middle |
| 5432 | PostgreSQL | 8.3 | Middle |
  
  
# Vulnerability Identification:
Objective 
-	Determine whether the detected FTP Service has any publicly documented vulnerability. 

Tool
-	Searchsploit

Commend
-	Sechsploit vsftpd 2.3.4

Result 
-	Public exploit exists for vsftpd 2.3.4.

Note
-	A public exploit existing for vsftpd does not mean that vulnerability necessarily exists in this system.

# Exploit Validation:
Objective
-	Verify whether Metasploit contains an exploit module for the identified ftp vulnerability 

Tool
-	Metasploit Framework

Command
-	Search vsftpd

Result
-	Metasploit have module exploit the targeted ftp version (vsftpd 2.3.4) and the module ranked “excellent”.
 
# Exploitation:
Objective 
-	Targeting the vulnerable FTP service identified during the previous phases.

Tool 
-	Metasploit Framework.

Module used 
-	exploit/unix/ftp/ vsftpd_234_backdoor

Result
-	successfully exploited the ftp service.
-	Obtained the remote command shell.
-	Verify root privileges using ‘howami’ an ‘id’.
-	Confirmed access to the target system.

