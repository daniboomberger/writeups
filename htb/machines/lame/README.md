# Lame
> Creator: `ch4p`
> Author: `daniboomberger`
> Date: `23.10.2020`

## Recon
> `nmap -sC -sV -Pn -oN lame_nmap.txt <MACHINE-IP>`
> - Just a nmap scan that save the received data into `lame_nmap.txt`
>
> `21/tcp  open  ftp vsftpd 2.3.4`
> `22/tcp  open  ssh OpenSSH 4.7p1 Debian 8ubuntu1 (protocol 2.0)`
> `139/tcp open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)`
> `445/tcp open  netbios-ssn Samba smbd 3.0.20-Debian (workgroup: WORKGROUP)`
```
We have these open ports
So we see there is a ftp port open, which might be worth to exploit 
```

## Exploit
> `searchsploit vsftpd 2.3.4``
```
This provides us with a vulnerability to exploit it. Next step is to open up `Metasploit` and search the exploit.
Afterwards we are going to use the found vulnerability, and set `RHOSTS <MACHINE-IP>`. `exploit` is our next command that will run the exploit. Sadly, we just get a Message back that we need a password, but we don't have one.
```
> `searchsploit smbd 3.0.20`
```
So that we cannot exploit the Machine over ftp, we need to find a new solution to get access to the Machine.
We try to find in our recon another good exploit. What my other thought was to ssh into the open port 22, but this was gone fast, because of the needed password(`probably just a stoopid beginner thought`). After that I searched for a smbd exploit of the given version by port 445. Succesfully there was a exploit for this version and we can do the same process as mentioned before with the vsftp vulnerability.
```
> `searching the flag...`
```
So my first try was to search what for user there are in the `/home` directory. I just searched for `txt` files and try to cat them out... Well it is a easy challenge so there was in the directory `/home/makenis` a text file called user.txt. Spoiler it had the flag hash in there. After that we needed to search another flag hash. This was maybe a little bit harder, but I knew already I had root Access which made me go look into the root folder. Second spoiler there was a file called root.txt
```

