@title Шаг 3: Настройка деплоя
@short Deploy
@group server

**1.** Клонируем репозиторий `$ git clone git@git.makebecool.com:deploy`
___
**2.** Переходим в ветку `$ git checkout develop`
___
**3.** Добавляем новый файл
название файла состоит из `<prefix>`**.**`<repository-name>` 
>Префикс может быть: 
> **dev.** - деплой будет применён к ветке **origin/develop**
> **rel.** - деплой будет применён к последней ветке **origin/release-***
(NOTE)  Если префикс не указан, то деплой будет приминён к ветке **origin/master** 

==Пример деплой файла для modx==
```
<?php
require 'deployer.phar';

define('localfile', __DIR__.'example.makebecool.pro');
define('remote', '/var/www/example.makebecool.pro');
define('remotecache', '/var/www/example.makebecool.pro/core/cache');
define('remotecore', '/var/www/example.makebecool.pro/core');
define('server', 'example.makebecool.pro:9090');
define('user', 'makebecool');
define('password', 'makebecool');

task('connect', 'Connect to server.', function () {
    connect(server, user, password);
    cd(remote);
});


task('pull', 'Update repository via git pull.', function () {
    run('git reset --hard');
    run('git pull origin develop');
});

task('clearcache', 'Clone repository on remote server.', function () {
    run('rm -r "'.remotecache.'"');
    cd(remotecore);
    run('mkdir cache');
});


task('update', 'update site on server.', ['connect', 'pull', 'clearcache']);

start();

```

== Пример файла для PrestaShop ==
```
<?php
require 'deployer.phar';

define('remote', '/var/www/etagerca/data/www/dev-etagerca.ru');
define('server', 'etagerca.ru'); // sftp
define('user', 'etagerca');
define('password', 'z5cydz8i');

task('connect', 'Connect to server.', function () {
    connect(server, user, password);
    cd(remote);
});

task('pull', 'Update repository via git pull.', function () {
    run('git checkout develop');
    run('git reset --hard');
    run('git pull origin develop');
});

task('clean', 'Remove untracked files.', function(){
    run('git clean -f -d');
});

task('grab', 'Update repository via git push fron serer.', function () {
    run('git checkout develop');
    run('git add .');
    run('git commit -a -m "grab from server"');
    run('git push origin develop');
});

task('update', 'update site on server.', ['connect', 'pull']);

start();

```

