# MySQL 

MySQL is ideally suited for applications such as dynamic websites, where efficient syntax and high response speed are essential. 

It is often combined with a Linux OS, PHP, and an Apache web server and is also known in this combination as LAMP (Linux, Apache, MySQL, PHP), or when using Nginx,

as LEMP. In a web hosting with MySQL database, 

this serves as a central instance in which content required by PHP scripts is stored .

MySQL server runs on TCP port 3306 

***Enumration***

```shell
sudo nmap 127.0.0-1 -sV -sC -p3306 --script mysql* # NES for mysql 

```

***connect to mysql without password if mysql use empty password***

```shell
mysql -u root -h 127.0.0.1

```
```shell
mysql -u root -ptoor 127.0.0.1 # with a password 

```

MYSQL command 
```
mysql -u <user> -p<password> <IP address> 

show databases; 

use <database>; 	

show tables; 	

show columns from <table>; 

select * from <table>; 	

select * from <table> where <column> = "<string>"; 	

```
