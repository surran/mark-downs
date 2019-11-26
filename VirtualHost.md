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
General Apache server configuration is handled by ```httpd.conf``` file. This file in turn loads other files for specific  settings. For setting up virtual hosts add/uncomment the following line in it and save the file.
```
Include conf/extra/httpd-vhosts.conf
```
Now open ```httpd-hosts.conf```



<!--stackedit_data:
eyJoaXN0b3J5IjpbMTE4NzkwMDkwMywxNjMzMjM4MDM5LDY1Mj
A4OTg5XX0=
-->