# Remote Desktop Protocol  

RDP USES TCP port 3389 as the transport protocol or  UDP protocol  port 3389 also for remote administration.

***Enumeration***

```shell
nmap -sV -sC 10.129.201.248 -p3389 --script rdp*

```
```shell
./rdp-sec-check.pl 127.0.0.1 # https://github.com/CiscoCXSecurity/rdp-sec-check 

```

***connect to rdp***

```shell
rdesktop -u username -p password 127.0.0.1 # or xfreerdp,Remmina

xfreerdp /u:<user> /p:"<password>" /v:IP
```
# WinRM 

Windows Remote Management (WinRM) is a simple Windows integrated remote management protocol based on the command line.

Port CP ports 5985(HTTP) and 5986(HTTPS) 

***Enumeration***

```shell
nmap -Pn -sV -sC 127.0.0.1 -p5985,5986 --disable-arp-ping -n

```

***connect to winrm***

```shell
evil-winrm -i 10.129.201.248 -u admin -p password

```

# WMI 

Windows Management Instrumentation (WMI) is Microsoft's implementation and also an extension of the Common Information Model (CIM) 

TCP port 135 

```shell
/usr/share/doc/python3-impacket/examples/wmiexec.py admin:"admin"@127.0.0.1 "hostname"
```
