# Laravel Ubuntu Setup
- Install apache2 and laravel in `/var/www/html` 
  - `composer create-project --prefer-dist laravel/laravel redmine`
- Directory Permissions for laravel :
  - `sudo chmod -R 775 /var/www/html/redmine/storage`
  - `sudo chmod -R  775 /var/www/html/remdine/bootstrap/cache`
- Setup apache for laravel : `sudo chgrp -R www-data /var/www/html/redmine`
-  Setup virtual host run : `sudo nano /etc/apache2/sites-available/redmine.test.conf`
```javascript
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName redmine.test
        DocumentRoot /var/www/html/redmine/public
        <Directory /var/www/html/redmine>
            Options FollowSymLinks
            AllowOverride All
            Require all granted
        </Directory>
        <IfModule mod_dir.c>
            DirectoryIndex index.php index.pl index.cgi index.html index.xhtml index.htm
        </IfModule>
        
        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```
- Enable new virual host file : `sudo a2ensite redmine.test.conf`
  - `sudo a2enmod rewrite`
- Restart apache2 : `sudo systemctl restart apache2`
- Setup domain :`sudo nano /etc/hosts`
```bash
127.0.0.1   localhost
127.0.1.1   guest-desktop
127.0.0.1   redmine.test

```
- Now run **http://redmine.test** in your browser