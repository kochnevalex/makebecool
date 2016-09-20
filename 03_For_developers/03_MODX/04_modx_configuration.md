@title Шаг 2: Настройка и стандарты внути MODX для работы с проектом
@short Настройка и стандарты MODX
@group modxstandarts

В этом документе описаны основные настройки и принятые стандарты для работы в MODX

= Структура категорий элементов =
Создаем в админке следующую структуру категорий
NOTE: Название категорий соответствует названиям каталогов в файловой системе и повторяет ее структуру @{article:File structure}.

- baseTheme (Общий каталог для снипетов, плагинов и шаблонов)
-- **base** - подкаталог для **чанков** создающих общую струкутуру (metaBase, headerBase, footerBase)
-- **common** - подкаталог для общих **чанков**, которые используются в не зависимости от сушьности
-- **content** - подкаталог для **чанков** контентной зоны
-- **parts** + **Entity** - подкаталог для **чанков**, использующихся для конкретной сущности, к примеру partsBlog, partsIndex.
-- **tv** - подкаталог для **чанков** использующихся для кастомных tv
-- **technical** - подкаталог для технических **шаблонов**, доступ к кторомы не нужно давать редакторам

= Стандарты и настройки для SEO =
== Стандарты ==
С помощью этих стандартов мы решаем следующие проблемы:
- Переадресации
-- Приводим к одному виду ссылки со / или /// и без него с редиректом 301 на страницы без / в конце
-- Перенаправляем запросы с www на без www
-- Перенаправляем ссылки index.html, index.php, index.php/// на корень сайта /
-- Все сылки с прописными буквами переадресуем на строчные
-- Перенаправляем по нужному протоколу http или https исходя из настроек
-- Решаем проблему с работой админки и конфликтами перенаправлений
- Добавляем сжатие (если есть возможность это лучше делать настройками сервера)
- Добавляем время жизни кеша статических ресурсов (если есть возможность это лучше делать настройками сервера)
- Запрещаем индексирование если для страницы не стоит галочка ##Досутпен для поиска##
- Генерируем все ссылки полными, а не относительными

== Настройки ==
{nav, Настройки > Настройки системы > Дружественные URL}
- ##automatic_alias## Автоматически генирировать псевдоним - **да**
- ##container_suffix## Суффикс контейера - **пустой**
- ##friendly_alias_max_length## Максимальная длина псевдонима - **70**
- ##friendly_alias_restrict_chars_pattern## Шаблон для фильтрации символов в псевдонимах  - **/[\0\x0B\t\n\r\f\a&=+%#<>"~:`@«»,\?\[\]\{\}\|\^'\\\!\.\)\(]/**
- ##friendly_urls## Использовать дружественные URL - **да**
- ##friendly_urls_strict## Строгий режим дружественных URL - **да**
- ##use_alias_path## Использовать вложенные URL - **да**
{nav, Настройки > Настройки системы > Сайт}
- ##link_tag_scheme## Схема URL - **full**

{nav, Сайт > Типы содержимого}
- ##Расширение файла## для html - **пустое**

== Технические решения ==
=== Плагин lowercaseUrl ===
Для передресации сылок с прописными буквами на строчные создаем плагин lowercaseUrl в соответствующей категории
элементов по событию OnHandleRequest.
```
<?php
$eventName = $modx->event->name;

switch($eventName) {
    case 'OnHandleRequest':
        if($modx->context->get('key') != "mgr"){
            if(isset($_GET['rewrite-strtolower-url'])) {
                $url = $_GET['rewrite-strtolower-url'];
                unset($_GET['rewrite-strtolower-url']);
                $params = http_build_query($_GET);
                if(strlen($params)) {
                    $params = '?' . $params;
                }
                $modx->sendRedirect('http://' . $_SERVER['HTTP_HOST'] . '/' . strtolower($url) . $params, array('responseCode' => 'HTTP/1.1 301 Moved Permanently'));
            }
        }
        break;
}
```

=== Плагин transferProtocol ===
Для передресации по нужному протоколу http или https исходя из настроек создаем плагин transferProtocol в соответствующей
категории элементов по событию OnHandleRequest.
```
<?php
$eventName = $modx->event->name;

switch($eventName) {
    case 'OnHandleRequest':
        $isSecure = false;
        if (isset($_SERVER['HTTPS']) && $_SERVER['HTTPS'] == 'on') {
            $isSecure = true;
        } elseif (!empty($_SERVER['HTTP_X_FORWARDED_PROTO']) && $_SERVER['HTTP_X_FORWARDED_PROTO'] == 'https' || !empty($_SERVER['HTTP_X_FORWARDED_SSL']) && $_SERVER['HTTP_X_FORWARDED_SSL'] == 'on') {
            $isSecure = true;
        }

        $REQUEST_PROTOCOL = $isSecure ? 'https' : 'http';
        $SYSTEM_PROTOCOL = $modx->getOption('server_protocol');
        if($SYSTEM_PROTOCOL != $REQUEST_PROTOCOL) {
            if($SYSTEM_PROTOCOL == "https")
                $modx->sendRedirect('https://' . $_SERVER['HTTP_HOST'] . $_SERVER['REQUEST_URI'], array('responseCode' => 'HTTP/1.1 301 Moved Permanently'));
            else
                $modx->sendRedirect('http://' . $_SERVER['HTTP_HOST'] . $_SERVER['REQUEST_URI'], array('responseCode' => 'HTTP/1.1 301 Moved Permanently'));
        }
        break;
}
```

== Файлы .htaccess ==
=== Файл в корне ===
```
AddDefaultCharset utf-8
Options +FollowSymlinks
RewriteEngine On
RewriteBase /

# Rewrite www.domain.com -> domain.com
RewriteCond %{HTTP_HOST} ^www.example.com$
RewriteRule ^(.*)$ http://example.com/$1 [R=301,L]

# force url to lowercase if upper case is found
RewriteCond %{REQUEST_URI} [A-Z]
# ensure it is not a file on the drive first
RewriteCond %{REQUEST_FILENAME} !-s
RewriteRule (.*) index.php?rewrite-strtolower-url=$1 [QSA,L]


# Rewrite index.php -> /
RewriteCond %{THE_REQUEST} ^[A-Z]{3,9}\s(.*)/index\.php [NC]
RewriteRule ^ %1 [R=301,L]

# Rewrite index.html -> /
RewriteCond %{THE_REQUEST} ^[A-Z]{3,9}\ /index\.html\ HTTP/
RewriteRule ^ %1 [R=301,L]

# Remove trailing slash
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^(.+)/$ /$1 [L,R=301]

# Remove many trailing slash
RewriteCond %{THE_REQUEST} //
RewriteRule .* $1 [L,R=301]

# The Friendly URLs part
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^(.*)$ index.php?q=$1 [L,QSA]

#Caching include if not config in server
#Header set Cache-Control "max-age=2592000"

# For servers that support output compression, you should pick up a bit of
# speed by un-commenting the following lines.
#include if not config in server
#php_flag zlib.output_compression On
#php_value zlib.output_compression_level 5
```

=== Файл в папке assets ===
```
RewriteEngine Off
Options -Indexes
```

=== Файл в папке connectors ===
```
RewriteEngine Off
```

=== Файл в папке manager ===
```
RewriteEngine Off
```

= Навигация =
- Назад: Файловая структура и названия файлов: @{article:File structure}
- Вперед: Настройка пользовательского досутпа в MODX: @{article:Permissions setting}