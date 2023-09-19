# Starting Point
This is the starting of my journey to become a god-like pentester.Building my knowledge from zer0 by cracking Hack the box machines. Starting point is a section to learn the basics of penetration testing. There are 3 tiers with multiple machines in each tier.
```
Bound to succeed
```
## Machines - Tier 0
### Meow
- Difficulty: Very easy     
- Understand the working of Telnet
- Uses port 23
- Use telnet command to login to the server with blank password
- Find the flag in the directory
### Fawn
- Difficulty: Very easy 
- Understand the working of FTP(FileTransferProtocol)
- Uses port 21
- Nmap scan to see the services and ports that are running ftp
``
nmap -sV -sC -Pn <targetip>
``
- FTP into the server and login as anonymous
- Find the flag in the directory

### Dancing
- Difficulty: Very easy 
- Understand the working of 'Server message block'
- Uses port 445 and 139
- use sambaclient to connect to the smb server
- To list out the directories 
```
smbclient -L <targetip> 
```
- To access the shares use the command 
```
smbclient\\\\<targetip>\\Sharename <username>
```

- Grab the flag
### Redeemer
- Difficulty: Very easy 
- Understand the working of Databases
- Usual Nmap scan took around 21min 
- Workaround 
```
nmap T:1009-9999 -Pn -sV <targetip>
```
- Redis service detected running
- Connect to redis using ``redis-cli``
- After getting access to the database -> use the following steps
- >>info  (get info about the database)
- >>keys* (Displays all the keys)
- >>Browse to the keys by selecting the database
- >>get flag (to retrieve the flag)

### Explosion
- Difficulty: Very easy
- Understand the working of RDP
- Nmap scan for recon 
```
nmap -sV -sC -Pn <targetip>
```

- RDP service running in 3389
- Using xfreerdp > logged in to the vm and grabbed the flag 
```
xfreerdp /u:Administrator /v:<victimip>
```

### Preignition
- Difficulty: Very easy 
- Performed Nmap scan
```
nmap -sV -sC -Pn 10.12923.177
```
- HTTP services found running on por 80
- Conducting more recon using Gobuster to enumerate browser directories 
```
gobuster -h
gobuster dir -u http://10.129.242.244/ -w /usr/share/wordlist/rockyou.txt -x php
```
- Admin.php page found 
- Login page detected 
- 'admin' 'admin' was the credentials
- Flag found on the admin panel page