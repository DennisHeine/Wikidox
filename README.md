WikiDox is a Wiki (an information management system) with an attached document management system.<br>
It was built with easy installation and configuration in mind.<br>
<br>
Requirements:<br>
-------------<br>
dotNET Core 2.1<br>
Apache webserver<br>
MySQL database server<br>
<br>
Installation:<br>
-------------<br>
-Set up your mysql server. Don't create a database yet.<br>
-(a) Create an Apache vhost entry with a reverse proxy to your dotnet core server. (something like backend.wikidox.ultracoolcompany.com):<br>
 <a href="https://raw.githubusercontent.com/DennisHeine/Wikidox/master/vhost.conf">https://raw.githubusercontent.com/DennisHeine/Wikidox/master/vhost.conf</a><br>
-Create an Apache vhost entry for the angular client (something like wikidox.ultracoolcompany.com)<br>
 It requires a valid SSL certificate. Self signed certificates are not possible!<br>
 You can get free ssl certificates from letsencrypt.<br>
 Add the following lines to your vhost:<br><br>
 
RewriteEngine On<br>
RewriteCond %{DOCUMENT_ROOT}%{REQUEST_URI} -f [OR]<br>
RewriteCond %{DOCUMENT_ROOT}%{REQUEST_URI} -d<br>
RewriteRule ^ - [L]<br>
RewriteRule ^ /index.html<br>
<br>
<br>
Server:<br>
-Unzip server.zip to a directory of your server that is not publically accessable.<br>
-Edit db.settings.conf and change it so it fits your mysql configuration.<br>
-Change to the server's directory and run "dotnet ./WikiDoxServer.dll" to start it.<br>
 (it is a good idea to start it using screen)<br>
 It will automatically create the database scheme on first run according to db.settings.conf<br>
 Default port is 127.0.0.1:5000<br>
<br>
Client:<br>
-Copy the contents of client zip to your webroot directory<br>
-edit config.json and enter the adress of the apache proxy that you have created in (a)<br>
<br>
Finishing stuff:<br>
-navigate your browser to your backend's installer, for example https://backend.wikidox.ultracoolcompany.com/api/Install/Install<br>
 this will create the initial database entries.<br>
<br>
First login:<br>
Login using admin:admin<br>
!!!Don't forget to change the default admin password!!!
