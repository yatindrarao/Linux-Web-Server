# Linux Web Server

- IP: 35.165.14.210 , Port: 2200

- Catalog app url: http://35.165.14.210/

Following softwares are installed in order to setup the server:
- apache2
- mod_wsgi
- postgresql
- finger
- flask
- git
- oauth2client
- sqlalchemy

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
