# SMB ( Server Message Block Protocol ) 

<h>The SMB protocol establishes communication by creating a client-server connection based on sending request-response messages back and forth. This setup would then set up a file-sharing as if a user is accessing files on their hard drive. It would make working easier with networked systems across the globe.</h>

***SMB*** : For Windows OS

***Samba*** : Unix OS 

- TCP 445 – SMB over TCP without the need for NetBIOS
- UDP 137 – SMB over UDP (Name Services)
- UDP 138 – SMB over UDP (Datagram)
- TCP 139 – SMB over TCP (Session service)

![Screenshot from 2021-12-07 22-39-02](https://user-images.githubusercontent.com/92652606/145117095-8766eef7-37ea-400a-a1e5-0574de7fc673.png)

* ***Connect to SMB With User and Password***

```shell 
smbclient //IP/SharedFolder -U "Username"
```
![Screenshot from 2021-12-07 22-47-40](https://user-images.githubusercontent.com/92652606/145117882-cfab423e-62f3-4139-909f-f51f2bb161ae.png)

* ***Enumerating SMB***

[enum4linux](https://labs.portcullis.co.uk/tools/enum4linux/)

```
-U             get userlist
-M             get machine list*
-N             get namelist dump (different from -U|-M)*
-S             get sharelist
-P             get password policy information*
-G             get group and member list
-L             get LSA policy information*
-D             dictionary crack, needs -u and -f*
-d             be detailed, applies to -U and -S
-u username    specify username to use (default "")
-p password    specify password to use (default "")
-f filename    specify dictfile to use (wants -D)*
```
```shell
enum4linux -n 192.168.1.107                                                                                                                                                                                                           1 ⨯
Starting enum4linux v0.8.9 ( http://labs.portcullis.co.uk/application/enum4linux/ ) on Tue Dec  7 23:25:20 2021

 ========================== 
|    Target Information    |
 ========================== 
Target ........... 192.168.1.107
RID Range ........ 500-550,1000-1050
Username ......... ''
Password ......... ''
Known Usernames .. administrator, guest, krbtgt, domain admins, root, bin, none


 ===================================================== 
|    Enumerating Workgroup/Domain on 192.168.1.107    |
 ===================================================== 
[+] Got domain/workgroup name: WORKGROUP

 ============================================= 
|    Nbtstat Information for 192.168.1.107    |
 ============================================= 
Looking up status of 192.168.1.107
        DESKTOP-CN9CEF8 <00> -         M <ACTIVE>  Workstation Service
        WORKGROUP       <00> - <GROUP> M <ACTIVE>  Domain/Workgroup Name
        ***DESKTOP-CN9CEF8*** <20> -         M <ACTIVE>  File Server Service
        WORKGROUP       <1e> - <GROUP> M <ACTIVE>  Browser Service Elections
        WORKGROUP       <1d> -         M <ACTIVE>  Master Browser
        ..__MSBROWSE__. <01> - <GROUP> M <ACTIVE>  Master Browser
```
* ***enumerate the shares***

```shell
enum4linux -s /usr/share/enum4linux/share-list.txt 192.168.1.107
```

* ***Enumerating samrdump.py*** 

![Screenshot from 2021-12-07 23-42-32](https://user-images.githubusercontent.com/92652606/145123129-42b498e3-d553-4165-a6a9-e5407b1dfcb7.png)

* ***nmap Scripts For SMB***

```shell
─$ ls  /usr/share/nmap/scripts/smb-*                                                                                                                                                                                                     2 ⨯
/usr/share/nmap/scripts/smb-brute.nse                   /usr/share/nmap/scripts/smb-enum-users.nse    /usr/share/nmap/scripts/smb-security-mode.nse       /usr/share/nmap/scripts/smb-vuln-ms08-067.nse
/usr/share/nmap/scripts/smb-double-pulsar-backdoor.nse  /usr/share/nmap/scripts/smb-flood.nse         /usr/share/nmap/scripts/smb-server-stats.nse        /usr/share/nmap/scripts/smb-vuln-ms10-054.nse
/usr/share/nmap/scripts/smb-enum-domains.nse            /usr/share/nmap/scripts/smb-ls.nse            /usr/share/nmap/scripts/smb-system-info.nse         /usr/share/nmap/scripts/smb-vuln-ms10-061.nse
/usr/share/nmap/scripts/smb-enum-groups.nse             /usr/share/nmap/scripts/smb-mbenum.nse        /usr/share/nmap/scripts/smb-vuln-conficker.nse      /usr/share/nmap/scripts/smb-vuln-ms17-010.nse
/usr/share/nmap/scripts/smb-enum-processes.nse          /usr/share/nmap/scripts/smb-os-discovery.nse  /usr/share/nmap/scripts/smb-vuln-cve2009-3103.nse   /usr/share/nmap/scripts/smb-vuln-regsvc-dos.nse
/usr/share/nmap/scripts/smb-enum-services.nse           /usr/share/nmap/scripts/smb-print-text.nse    /usr/share/nmap/scripts/smb-vuln-cve-2017-7494.nse  /usr/share/nmap/scripts/smb-vuln-webexec.nse
/usr/share/nmap/scripts/smb-enum-sessions.nse           /usr/share/nmap/scripts/smb-protocols.nse     /usr/share/nmap/scripts/smb-vuln-ms06-025.nse       /usr/share/nmap/scripts/smb-webexec-exploit.nse
/usr/share/nmap/scripts/smb-enum-shares.nse             /usr/share/nmap/scripts/smb-psexec.nse        /usr/share/nmap/scripts/smb-vuln-ms07-029.nse
```

![Screenshot from 2021-12-07 23-49-32](https://user-images.githubusercontent.com/92652606/145123675-4729b303-00ae-4771-801b-61a57482c3c9.png)

* ***Exploiting SMB***

* With anonymous 

![Screenshot from 2021-12-07 23-57-19](https://user-images.githubusercontent.com/92652606/145124257-db6ffd44-cfc9-486d-a04b-6349e13c8036.png)

* Mounting The Shares to the Local Host 

sudo mount -t cifs -o username=Anonymous,password=Anonymous  //IP/sharename  ./

![Screenshot from 2021-12-08 00-12-41](https://user-images.githubusercontent.com/92652606/145125582-3f7c6506-56da-4a98-afb2-271fdaf9004f.png)



