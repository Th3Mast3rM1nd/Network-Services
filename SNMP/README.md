# SNMP ( Simple Network Management Protocol ) 

***SNMP Enumeration***

* snmp runs on udp port 161 

```shell
sudo nmap -T4 -sU -p 161 ip 
```

```shell
onesixtyone -c dict.txt 192.168.1.110

```

***Windows***

```shell
snmpwalk -c public -v1 -t ip  # enumrate the whole MIB tree 

```
```shell
snmp-check 192.168.1.2 -c public 

```

