<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>VirtualHost</title>
  <link rel="stylesheet" href="https://stackedit.io/style.css" />
</head>

<body class="stackedit">
  <div class="stackedit__html">


  
  
  <title>VirtualHost</title>
  


  <div class="stackedit__html"><h1 id="hosting-multiple-websites-on-amazon-lightsail">Hosting Multiple websites on Amazon Lightsail</h1>
<h3 id="what-are-the-scenarios">What are the scenarios?</h3>
<p>
This happens when you own multiple domains but do not wish to host them on separate servers.</p>
</div><p>A typical virtual host config for a domain (say <a href="http://www.website1.com">www.website1.com</a>) looks like this</p>
<pre><code>&lt;VirtualHost *:80
    ServerAdmin your@email.com
    DocumentRoot "/opt/bitnami/apache2/docs/website1"
    ServerName website1.com
    ServerAlias www.website1.com
    ErrorLog "logs/website1_error_log"
    CustomLog "logs/website1_access_log" common
/VirtualHost&gt;

&lt;VirtualHost *:80&gt;&gt;
    ServerAdmin your@email.com
    DocumentRoot "/opt/bitnami/apache2/docs/website2"
    ServerName website2.com
    ServerAlias www.website2.com
    ErrorLog "logs/website2_error_log"
    CustomLog "logs/website2_access_log" common
&lt;</code></pre>
<p>You can add more such snippets to host more websites on the same server.</p>
<p>
</p><p>Save the file and restart the apache server to see the changes taking effect</p>
<pre><code>sudo /opt/bitnami/ctlscript.sh restart apache
</code></pre>
<p>Open <a href="http://www.website1.com">www.website1.com</a> and <a href="http://www.website2.com">www.website2.com</a> on the browser to confirm</p>



</div>
</body>

</html>
