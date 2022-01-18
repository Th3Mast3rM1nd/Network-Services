# DNS Enumeration 



DIG A query fro ns server 

```
dig A ns2.megacorpone.com

```

DIG - NS Query

```
dig ns megacorpone.com @51.222.39.63

```
DIG - ANY Query


```
dig any megacorpone.com @51.222.39.63

```
DIG - AXFR Zone Transfer

```
dig axfr megacorpone.com @51.222.39.63

```

```shell
dnsrecon -d domain.com  -t axfr 
```

```shell
dnsenum -d domain.com

dnsenum --dnsserver 51.222.39.63 --enum -p 0 -s 0  -f /usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-110000.txt megacorpone.com

```

```shell
nmap --script=dns-zone-transfer -p 53 ns.domain.com 

```

Sub-domain Brute FOrcing 

```
for sub in $(cat /usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-110000.txt ); do dig $sub.megacorpone.com @51.222.39.63 | grep -v ';\|SOA' |  grep $sub; done

```





