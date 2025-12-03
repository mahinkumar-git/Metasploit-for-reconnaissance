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
<img width="864" height="570" alt="image" src="https://github.com/user-attachments/assets/0e76c26d-39e8-441a-9b6f-96da30989cd0" />


Invoke msfconsole:
## OUTPUT:
<img width="804" height="651" alt="image" src="https://github.com/user-attachments/assets/88eef8df-d68b-4b1b-a8c9-16f7765fac0a" />


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.




Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000  (Replace with appropriate IP Address)

step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24


Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary



Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT:


<img width="766" height="447" alt="image" src="https://github.com/user-attachments/assets/3e5f76dc-9c04-4f4e-861c-9550c97303c1" />


The info command provides information regarding a module or platform,

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init

## OUTPUT:

<img width="858" height="419" alt="image" src="https://github.com/user-attachments/assets/eab28273-c63e-4f09-8542-ab86d97ec40a" />



## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:

<img width="865" height="176" alt="image" src="https://github.com/user-attachments/assets/0279e4bc-7f32-4a46-ba33-b7bd90ba91b8" />



Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
## OUTPUT:

<img width="848" height="193" alt="image" src="https://github.com/user-attachments/assets/06a92bc7-1a75-4b6a-8956-5b927adf812c" />


use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
Use the set rhosts command to set the parameter and run the module, as follows:
After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.




set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
## OUTPUT:


<img width="848" height="369" alt="image" src="https://github.com/user-attachments/assets/38415743-f69d-4a24-bede-015a8d8be72e" />



## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
