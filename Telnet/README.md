# Telnet 

 Telnet is an unencrypted and therefore insecure protocol and runs on Port 23

* ***Connect To Telnet***

```shell
telnet 10.10.10.10 23

```
<img width="724" alt="Screen Shot 2021-12-09 at 23 44 06" src="https://user-images.githubusercontent.com/92652606/145487563-c767e6a0-34e9-4e86-b47e-633959fa9871.png">

* ***Telnet Enumeration***

```shell 
nmap -script=telnet-ntlm-info 192.168.1.122
```

<img width="577" alt="Screen Shot 2021-12-09 at 23 57 39" src="https://user-images.githubusercontent.com/92652606/145489174-383de853-6625-4f40-a546-cae561ef92fc.png">

* ***Banner Grabbing With Telnet***

```shell
telnet goole.com 80
Get / HTTP/1.1
Host: goole.com

```
<img width="684" alt="Screen Shot 2021-12-10 at 00 07 11" src="https://user-images.githubusercontent.com/92652606/145489933-095aa798-0498-43e1-bd6b-55873ecc1819.png">
