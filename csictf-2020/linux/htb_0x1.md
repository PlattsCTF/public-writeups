## HTB 0x1

### Writeup by Trent (teerix)

Category: Linux

```
I forgot my 'flag.txt' file on the server...

Server is at 34.93.37.238
```

Upon running `nmap -A -Pn -v 34.93.37.238` to search for open ports, there were two open ports, 22 (SSH) and 5001, which showed as a port running FTP, specifically with ftp-anon, allowing ftp access to practically anyone.

I was having issues with commands not issuing in both active and passive mode in the linux ftp shell, so I connected to the server using WinSCP with:

IP: 34.93.37.238
Port: 5001
User: anonymous
Pass: anonymous

Located in the `pub/` folder was the flag.txt file, which contained the flag.


Flag: csictf{4n0nym0u5_ftp_l0g1n}