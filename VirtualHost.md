<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>VirtualHost</title>
  <link rel="stylesheet" href="https://stackedit.io/style.css" />
</head>

<body class="stackedit">
  <div class="stackedit__html"><h1 id="hosting-multiple-websites-on-amazon-lightsail">Hosting Multiple websites on Amazon Lightsail</h1>
<h3 id="what-are-the-scenarios">What are the scenarios?</h3>
<p>
This happens when you own multiple domains but do not wish to host them on separate servers.</p>
<h3 id="the-process The Process</h3><p>
Key Steps:</p>
<ol>
<li>Locate Virtual host File</li>
<li>Add domains</li>
<li>Restart Apache</li>
</ol>
<p>Load Bitnami terminal on Lightsail on your instance. Browse to the apache configuration files location.</p>
<pre><code>bitnami@ip-172-26-5-171:~$cd /opt/bitnami/apache2/conf
</code></pre>
<p>General Apache server configuration is handled by <code>httpd.conf</code> file. This file in turn loads other files for specific  settings. For setting up virtual hosts add/uncomment the following line in it and save the file.</p>
<pre><code>Include conf/extra/httpd-vhosts.conf
</code></pre>
<p>Now open <code>httpd-hosts.conf</code> located in the extras folder and configure Virtual hosts.<p>

A typical virtual host config for a domain (say <a href="http://www.website1.com">www.website1.com</a>) looks like this</p>
<pre><code>&lt;VirtualHost *:80
    ServerAdmin your@email.com
    DocumentRoot "/opt/bitnami/apache2/docs/website1"
    ServerName website1.com
    ServerAlias www.website1.com
    ErrorLog "logs/website1_error_log"
    CustomLog "logs/website1_access_log" common
/VirtualHost&gt;

&lt;VirtualHost *:80&gt;>
    ServerAdmin your@email.com
    DocumentRoot "/opt/bitnami/apache2/docs/website2"
    ServerName website2.com
    ServerAlias www.website2.com
    ErrorLog "logs/website2_error_log"
    CustomLog "logs/website2_access_log" common
&lt;</VirtualHost&gt;
</code></pre>
<p>You can add more such snippets to host more websites on the same server.</p>
<p>

Save the file and restart the apache server to see the changes taking effect</p>
<pre><code>sudo /opt/bitnami/ctlscript.sh restart apache
</code></pre>
<p>Open <a href="http://www.website1.com">www.website1.com</a> and <a href="http://www.website2.com">www.website2.com</a> on the browser to confirm</p>
</div>
</body>

</html>
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTc3MjA4MjMwOV19
-->