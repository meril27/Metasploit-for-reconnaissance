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

<img width="906" height="737" alt="image" src="https://github.com/user-attachments/assets/c7be388e-f69e-45ec-aea6-fd70680d231c" />


Invoke msfconsole:
## OUTPUT:

<img width="967" height="600" alt="image" src="https://github.com/user-attachments/assets/a58ae501-e04e-42bf-a8f7-a36ed6fbf4a5" />


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

## Output:

<img width="997" height="962" alt="image" src="https://github.com/user-attachments/assets/d74f2763-08d1-41f6-ada7-ab3e03b884cc" />


Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000  (Replace with appropriate IP Address)
## OUTPUT:

<img width="953" height="292" alt="image" src="https://github.com/user-attachments/assets/7ac95c1c-3766-4592-884a-2057016cc877" />


step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:

<img width="823" height="723" alt="image" src="https://github.com/user-attachments/assets/f9d538b2-027a-4a8b-80dc-35e9b829ae71" />



Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:

<img width="745" height="600" alt="image" src="https://github.com/user-attachments/assets/68a6b06c-7a10-4ea3-8ecc-dc2264ce70b3" />



Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT:

<img width="1918" height="768" alt="image" src="https://github.com/user-attachments/assets/457f8369-caae-4b78-86b4-ea3bb32a5de5" />



The info command provides information regarding a module or platform,

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## OUTPUT:

<img width="748" height="303" alt="image" src="https://github.com/user-attachments/assets/7516fa30-a293-4a3e-8d3d-8ee3cfc960b7" />



## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:

<img width="1752" height="408" alt="image" src="https://github.com/user-attachments/assets/42b3a9e8-a8b4-40c1-9983-796406377dc7" />


Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
## OUTPUT:

<img width="1665" height="686" alt="image" src="https://github.com/user-attachments/assets/0785500a-2f21-4fc5-992d-894afaaaa6e9" />

use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
## OUTPUT:

<img width="1437" height="330" alt="image" src="https://github.com/user-attachments/assets/30f4d8b3-aaf7-4f26-8cd0-061b539502c7" />



Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:

<img width="1042" height="179" alt="image" src="https://github.com/user-attachments/assets/d18c2d20-01a6-4f37-a494-124f38f06be6" />


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
## OUTPUT:

<img width="1566" height="767" alt="image" src="https://github.com/user-attachments/assets/f03ddd34-8726-4f7f-aca4-c024182ef40b" />



set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
## OUTPUT:

<img width="1270" height="473" alt="image" src="https://github.com/user-attachments/assets/b93bfba4-adb0-4f9c-af39-f4aea8d45913" />





## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
