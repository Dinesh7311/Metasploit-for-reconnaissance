# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find out the ip address of the attackers system
## OUTPUT:
![5 13](https://github.com/user-attachments/assets/50d8a331-eb6c-41f5-9c0f-f257c5c2abd8)


Invoke msfconsole:
## OUTPUT:
![5 4](https://github.com/user-attachments/assets/15e17cc3-6aeb-4c26-808d-e91892e7254c)


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
![5 6](https://github.com/user-attachments/assets/38ef16ab-3cf4-48ae-8a80-6d7666370653)


Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000  (Replace with appropriate IP Address)
## OUTPUT:
![5 3](https://github.com/user-attachments/assets/d94ec58d-662b-45f2-8ae1-4f371c3ad9e8)

step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:
![5 7](https://github.com/user-attachments/assets/99d6f937-f4d3-4cdc-9048-0b74aeee1d37)


Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:
![5 2](https://github.com/user-attachments/assets/826c13aa-e9c6-4cb0-82b1-03379892c74e)


Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT:
![5 12](https://github.com/user-attachments/assets/d984518a-d0bb-4f78-b50c-4bbdb8ea54af)

The info command provides information regarding a module or platform,

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## OUTPUT:
![5 9](https://github.com/user-attachments/assets/0db40bbf-41f1-40bc-b8ed-1bbc5196a7ae)


## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:
![5 5](https://github.com/user-attachments/assets/4105f6f0-2846-4589-a6d8-cf37a7ae1266)


Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
## OUTPUT:
![5 1](https://github.com/user-attachments/assets/953d3caa-7419-4d3c-878c-69f843c98ec5)


use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
## OUTPUT:
![5 11](https://github.com/user-attachments/assets/ff7f6fca-bd2c-427b-89f5-3676b3fd0c99)


Use the set rhosts command to set the parameter and run the module, as follows:
After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
## OUTPUT:
![5 8](https://github.com/user-attachments/assets/f0ea388f-9fce-45ed-9e2c-c364dafb44b9)

set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
## OUTPUT:
![5 10](https://github.com/user-attachments/assets/b34391af-7c31-4def-8685-b79fb35cb836)

## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
