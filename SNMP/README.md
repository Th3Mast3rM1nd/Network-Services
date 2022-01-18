# SNMP ( Simple Network Management Protocol ) 

it is a protocol for monitoring and managing network devices ( routers, switches, servers, IoT devices ) UDP port 161 


Community Strings .



***SNMP Enumeration***


```shell
sudo nmap -T4 -sU -A -p 161 127.0.0.1
```

```shell

onesixtyone -c /usr/share/wordlist/secLists/Discovery/SNMP/snmp.txt 127.0.0.1 # bruteforce Community String 

```

```shell
braa public@10.253.101.1:161:.1.3.6.* 
 
```


***Windows***

```shell
snmpwalk -c public -v1 -t ip  # enumrate the whole MIB tree 

```
```shell
snmp-check 192.168.1.2 -c public 

```

