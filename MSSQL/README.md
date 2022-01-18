# MSSQL 
 
Microsoft's SQL-based relational database management system and uses default tcp port 1433 


![Screenshot from 2022-01-18 19-42-20](https://user-images.githubusercontent.com/92652606/150007730-8ec360aa-1134-42cb-8c58-65ecb03a59bd.png)


***Enumeration***

```shell
nmap --script ms-sql-info,ms-sql-empty-password,ms-sql-xp-cmdshell,ms-sql-config,ms-sql-ntlm-info,ms-sql-tables,ms-sql-hasdbaccess,ms-sql-dac,ms-sql-dump-hashes --script-args mssql.instance-port=1433,mssql.username=sa,mssql.password=,mssql.instance-name=MSSQLSERVER -sV -p 1433 10.129.201.248

# ms-sql-info # mssql info
# ms-sql-empty-password # trying empty password
# ms-sql-xp-cmdshell # run a command using the command shell of Microsoft SQL Server 
# ms-sql-config  # Queriy ms-sql instances for a list of databases, linked servers, and configuration settings. 
# ms-sql-ntlm-info  # enumerates information from mssql with NTLM authentication enabled.
# ms-sql-tables # query mssql list of tables
# ms-sql-hasdbaccess # Queries Microsoft SQL Server (ms-sql) instances for a list of databases a user has access to 
# ms-sql-dac # Queries the Microsoft SQL Browser service for the DAC (Dedicated Admin Connection) port of a given (or all) SQL Server instance 
# ms-sql-dump-hashes # Dumps the password hashes from an MS-SQL 
```

***metasploit***

```shell
auxiliary/scanner/mssql/mssql_ping 
 
``` 

***connect to mssql with creds***

```shell
python3 mssqlclient.py Admin@127.0.0.1 -windows-auth

```
