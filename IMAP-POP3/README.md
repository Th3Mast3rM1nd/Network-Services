# IMAP / POP3

[IMAP and POP3](https://www.one.com/en/email/what-is-imap-and-pop3)

IMAP allows online management of emails directly on the server and supports folder structures : port 143 or 993

POP3 provides listing, retrieving, and deleting emails as functions at the email server : port : 110 or 995

***Enumeration***

```shell
sudo nmap 127.0.0.1 -sV -p110,143,993,995 -sC
```

```shell
curl -k 'imaps://12.3.4.21.' --user root:toor -v # connect to imaps
curl -k 'pop3s://110.10.10.1' --user root:toor -v # connect to pop3s
```

```shell
openssl s_client -connect 10.129.14.128:pop3s # TLS Encrypted Interaction POP3
openssl s_client -connect 10.129.14.128:imaps # TLS Encrypted Interaction imaps
```

[Access IMAP Server From The Command Line ](https://tewarid.github.io/2011/05/10/access-imap-server-from-the-command-line-using-openssl.html)
