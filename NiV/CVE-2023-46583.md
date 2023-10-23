## Nipah virus (NiV) – Testing Management System


**Bug Description:**

A unauthenticated stored cross-site scripting (XSS) vulnerability in PHPGurukul Nipah virus (NiV) – Testing Management System 1.0 allows attackers to execute arbitrary web scripts via a crafted payload injected into the State field.

**Steps to Reproduce:** 

```
# Exploit Title: Unauthenticated stored cross-site scripting (XSS) vulnerability in PHPGurukul Nipah virus (NiV) – Testing Management System
# Date: 22-10-2023
# Exploit Author: rumble773
# Vendor Homepage: https://phpgurukul.com/
# Software Link: https://phpgurukul.com/nipah-virus-niv-testing-management-system-using-php-and-mysql/
# Version: 1.0
# Tested on: firefox/chrome
# CVE : 
```

To reproduce the attack: 

1- Head to the `nipah-tms/new-user-testing.php` endpoint 
2- Fill the information all in normal way and in the State put the XSS payload: `<script>alert(document.domain)</script>` or `Test+<script>alert(document.domain)</script>`
3- Going back to the dashboard at `nipah-tms/live-test-updates.php` you will notice that the stored XSS has been triggered.
4- Checkign the SQL data localy you can see it is stored in the data base without sanitizing the input.

**Recommendation:** 
It is recommended to add layer of input validation and sanitizing before adding the data to the database.  
