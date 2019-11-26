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
Now open ```httpd-hosts.conf``` located in the extras folder and configure Virtual hosts.

A typical virtual host config looks like this
```
<VirtualHost *:80>
    ServerAdmin your@email.com
    DocumentRoot "/opt/bitnami/apache2/docs/website1"
    ServerName website1.com
    ServerAlias website
    ErrorLog "logs/website1_error_log"
    CustomLog "logs/website1_access_log" common
</VirtualHost>
```



<VirtualHost *:80>
    DocumentRoot "/opt/bitnami/apache2/docs/www.suryaranjanshandil.com"
    ServerName suryaranjanshandil.com
    ServerAlias www.suryaranjanshandil.com
    RewriteEngine On
    RewriteRule ^/[a-zA-Z0-9]+[/]?$ /index.html [QSA,L]
    RewriteRule ^/comments/[0-9]+[/]?$ /index.html [QSA,L]
    ErrorLog "logs/suryaranjanshandil.com-error_log"
    CustomLog "logs/www.suryaranjnashandil.com-access_log" common
</VirtualHost>
<VirtualHost *:80>
    ServerAdmin suryaran@gmail.com
DocumentRoot "/opt/bitnami/apache2/docs/www.edvane.com"
ServerName edvane.com
ServerAlias www.edvane.com
ErrorLog "logs/www.edvane.com-error_log"
CustomLog "logs/www.edvane.com-access_log" common
</VirtualHost>
```



<!--stackedit_data:
eyJoaXN0b3J5IjpbMTY2NTY4NTgyMywxNjMzMjM4MDM5LDY1Mj
A4OTg5XX0=
-->