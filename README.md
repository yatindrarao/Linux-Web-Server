### Linux Web Server
This web server is implemented using Apache2. It uses   mod_wsgi for intereface
between apache server and web apllication.
Catalog app is hosted on this server which is developed with flask and postgresql.  

- Server IP: 35.165.14.210 , Port: 2200

- Catalog app url: http://35.165.14.210/

### Softwares Installed
Following softwares are installed in order to setup the server:
- apache2
- mod_wsgi
- postgresql
- finger
- flask
- git
- oauth2client
- sqlalchemy

## Server Configuration
Following configuration files are changed:
- /etc/apache2/sites-available/000-default.conf

The below content is added into the file
```
  WSGIScriptAlias / /var/www/Cataloug-App/webapp.wsgi
  WSGIDaemonProcess webapp
    <Directory /var/www/Cataloug-App>
           WSGIProcessGroup webapp
           WSGIApplicationGroup %{GLOBAL}
           Order deny,allow
           Allow from all
   </Directory>

```
- webapp.wsgi file is added in /var/www/Catalog-App

```                                
import sys
sys.path.insert(0,'/var/www/Cataloug-App')
from application import app as application
```

## Steps For Deployment
### Step 1

Login into the server by following command.
```
$ ssh -i key.rsa grader@35.165.14.210 -p 2200
```
Here `key.rsa` is a key which is included on the server.

### Step 2
After login change your current directory to /var/www/ .
```
$ cd /var/www/
```
The catalog project is stored in this folder.

### Step 3
Take clone from git repository.
```
$ git clone https://github.com/yatindrarao/Cataloug-App.git
```

### Step 4
Change into Cataloug-App firectory and add webapp.wsgi into it as shown in server configuration section above.

## Credentials
There are two users on server grader and root.

```
user: grader
password: best$123$hello
```
```
user: root
password: root$123$hello
```
### Note
Password authenctication is disabled on server only key authentication is allowed.
