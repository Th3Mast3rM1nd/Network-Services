# SMTP ( Simple Mail Transfer Protocol ) 

SMTP is used to send and receive mail messages and runs on Port 25. newer SMTP on port 587 . 

SMTP understand Some Simple Text Commands :  

    AUTH PLAIN - AUTH is a service extension used to authenticate the client
    HELO - introduce yourself
    EHLO - introduce yourself and request extended mode
    MAIL FROM: - specify the sender
    RCPT TO: - specify the recipient
    DATA - specify the body of the message (To, From and Subject should be the first three lines.)
    RSET - reset
    QUIT - quit the session
    HELP - get help on commands
    VRFY - verify an address
    EXPN - expand an address
    VERB - verbose
    
* ***Enumerating SMTP***

```shell
sudo nmap --script smtp-open-relay -p 25 ip # https://nmap.org/nsedoc/scripts/smtp-open-relay.html 

``` 

```shell
nmap -sS -A -p 25,587,2525,456,25025 ip  # 456, 25025 used for smtp with SSL

```
<img width="1020" alt="Screen Shot 2021-12-15 at 17 23 23" src="https://user-images.githubusercontent.com/92652606/146224892-13722add-0da9-408a-b659-ad671eb87ba7.png">

* ***Enumerating Users With VRFY or EXPN***

```shell
telnet 127.0.0.1 25

```
<img width="712" alt="Screen Shot 2021-12-15 at 17 30 41" src="https://user-images.githubusercontent.com/92652606/146225924-faa1bf12-1d79-4fa0-baa6-2d307acb214d.png">

```python 
#!/usr/bin/python2

#python script to bruteforce usernames

import socket
import sys

if len(sys.argv) != 2:
        print("Usage: vrfy.py ./userlist.txt")
        sys.exit(0)
else:
    filename = sys.argv[1]

try:
    with open(filename, "r") as f:
        usernames = [line.strip() for line in f]
except FileNotFoundError:
    print("file not found")

print(usernames)

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

connect = s.connect(('127.0.0.1',25))

banner = s.recv(1024)

print(banner)
for username in usernames:
    print(username)
    s.send('VRFY  ' + username +  '\r\n')
    result = s.recv(1024)
    print(result)

s.close()
```


