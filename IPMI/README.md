# Intelligent Platform Management Interface 

IPMI provides sysadmins with the ability to manage and monitor systems even if they are powered off or in an unresponsive state . 

Systems that use the IPMI protocol are called Baseboard Management Controllers (BMCs) .

IPMI use port 623 UDP 

***Enumerating IPMI***

```shell
sudo nmap -sU --script ipmi-version -p 623 127.0.0.1 #

```
```shell
auxiliary/scanner/ipmi/ipmi_version # metasploit 

```

Default Creds 

```
Product name : Dell iDRAC , username: 	root 	, password :calvin
Product name : HP iLO  , username : Administrator 	, password : randomized 8-character string consisting of numbers and uppercase letters
Product name : Supermicro IPMI , username: 	ADMIN , password: 	ADMIN .

```

*** Metasploit Dumping Hashes ***

```
auxiliary/scanner/ipmi/ipmi_dumphashes

```
