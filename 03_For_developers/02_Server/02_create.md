@title Шаг 2: Создание виртуального хостинга
@short Создание виртуального хостинга
@group server

=Автоматический режим=

**1.** Переходим в директорию `$ cd /var/www`
___

**2.** Запускаем скрипт `$ ./create.sh example.makebecool.pro`
> где **example** - название сайта	

___

**3.** При перезагрузке модулей apache и nginx система запросит пароль.
Вводим **makebecool** и жмём enter

(IMPORTANT) В целях безопасности вводимый пароль не отображается на экране в виде символов.



=Ручной режим=

**1.** Добавляем директорию в `/var/www`
**`example`**.`makebecool.pro`
> где **example** - название сайта
___
**2.** Добавляем конфигурационый файл для apache: `/etc/apache2/sites-available/exmple.makebecool.pro.conf`
```<VirtualHost *:81>
    ServerAdmin webmaster@localhost
    ServerName example.makebecool.pro
    DocumentRoot /var/www/example.makebecool.pro
    <Directory /var/www/example.makebecool.pro/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
        Require all granted
    </Directory>
    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory /usr/lib/cgi-bin>
        AllowOverride None
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Require all granted
    </Directory>
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
    Alias /doc/ /usr/share/doc/
    <Directory /usr/share/doc/>
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
</VirtualHost>```
___
**3.** Добавляем конфигурационный файл для nginx: `/etc/nginx/sites-available/example.makebecool.pro`
```server {
listen 80;
server_name example.makebecool.pro;
access_log /var/log/nginx.access_log;
location ~* \.(jpg|jpeg|gif|png|css|zip|tgz|gz|rar|bz2|doc|xls|exe|pdf|ppt|tar|wav|bmp|rtf|swf|ico|flv|txt|xml|doc$
root /var/www/example.makebecool.pro/;
index index.php index.html;
access_log off;
expires 30d;
}
location ~ /\.ht {
deny all;
}
location / {
proxy_pass http://127.0.0.1:81/;
proxy_set_header X-Real-IP $remote_addr;
proxy_set_header X-Forwarded-for $remote_addr;
proxy_set_header Host $host;
proxy_connect_timeout 60;
proxy_send_timeout 90;
proxy_read_timeout 90;
proxy_redirect off;
proxy_set_header Connection close;
proxy_pass_header Content-Type;
proxy_pass_header Content-Disposition;
proxy_pass_header Content-Length;
}
}```
___

**4.** Добавляем символические ссылки в директорию `site-enabled` 
**Apache**: `$ sudo ln -s /etc/apache2/sites-available/example.makebecool.pro.conf /etc/nginx/sites-enabled/example.makebecool.pro.conf`
**Nginx** : `$ sudo ln -s /etc/ngninx/sites-available/example.makebecool.pro /etc/nginx/sites-enabled/example.pro`
___

**5.** Перезагружаем apache и nginx
`$ sudo /etc/init.d/apache2 restart`
`$ sudo /etc/init.d/nginx restart`