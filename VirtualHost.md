# Hosting Multiple websites on Amazon Lightsail

### What are the scenarios?

### The Process
Key Steps:
1. Locate Virtual host File
2. Add domains
3. Restart Apache

B
```
bitnami@ip-172-26-5-171:~$cd /opt/bitnami/apache2/conf
```
This location contains ```httpd.conf``` file. This file handles apache server configuration. Type/uncomment the following line is in this file
```
Include conf/extra/httpd-vhosts.conf
```




<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1MTIxNzg1NTEsMTYzMzIzODAzOSw2NT
IwODk4OV19
-->