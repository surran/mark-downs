# Hosting Multiple websites on Amazon Lightsail

### What are the scenarios?
This happens when you own multiple domains but do not wish to host them on separate servers.  
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

A typical virtual host config for a domain (say www.website1.com) looks like this
```
<VirtualHost *:80>
    ServerAdmin your@email.com
    DocumentRoot "/opt/bitnami/apache2/docs/website1"
    ServerName website1.com
    ServerAlias www.website1.com
    ErrorLog "logs/website1_error_log"
    CustomLog "logs/website1_access_log" common
</VirtualHost>

<VirtualHost *:80>
    ServerAdmin your@email.com
    DocumentRoot "/opt/bitnami/apache2/docs/website2"
    ServerName website2.com
    ServerAlias www.website2.com
    ErrorLog "logs/website2_error_log"
    CustomLog "logs/website2_access_log" common
</VirtualHost>
```

You can add more such snippets to host more websites on the same server.

Save the file and restart the apache server to see the changes taking effect
```
sudo /opt/bitnami/ctlscript.sh restart apache
```
Open www.website1.com and www.website2.com on the browser to confirm



<!--stackedit_data:
eyJoaXN0b3J5IjpbMTI0MTgwNjMxNSwtMTgyNDIyNTQzXX0=
-->