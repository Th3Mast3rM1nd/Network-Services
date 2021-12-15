# SMTP ( Simple Mail Transfer Protocol ) 

SMTP is used to send and receive mail messages and runs on Port 25.

SMTP understand Some Simple Text Commands :  

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
nmap -sS -A -p 25 ip 

```

