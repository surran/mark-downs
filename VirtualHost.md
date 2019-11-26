# Hosting Multiple websites on Amazon Lightsail

### What are the scenarios?

### The Process
Key Steps:
1. Locate Virtual host File
2. Add domains
3. Restart Apache

Load Bitnami terminal on Lightsail on your instance. Browse to the apache configuration files location.
```
bitnami@ip-172-26-5-171:~$cd /opt/bitnami/apache2/conf
```
Apache server configuration is handled by ```httpd.conf``` file. This file handles apache server configuration. Type/uncomment the following line is in this file
```
Include conf/extra/httpd-vhosts.conf
```




<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEyODI2MTA0NzQsMTYzMzIzODAzOSw2NT
IwODk4OV19
-->