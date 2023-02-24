---
date: 2018-10-04
categories: [it, web]
tags: [Установка, Сервер, Apache, PHP, MySQL, phpMyAdmin]
author: Anton Sergienko
author-email: anton.b.sergienko@gmail.com
license: CC BY 4.0
license-url: https://github.com/Harrix/harrix.dev/blob/main/LICENSE.md
url-src: https://github.com/Harrix/harrix.dev-blog-2018/blob/main/apache-php-mysql/apache-php-mysql.md
url: https://harrix.dev/ru/blog/2018/apache-php-mysql/
---

# Установка Apache + PHP + MySQL + phpMyAdmin в Windows 10

В статье рассказывается о том, как настроить связку Apache + PHP + MySQL + phpMyAdmin в Windows 10.

Данная статья является переработкой статьи 2014 года.

## Скачивание файлов

Файлы скачиваете согласно битности вашей операционной системы.

Вначале надо скачать и установить (и возможно перегрузить комп) системную библиотеку от Microsoft. Конкретная версия будет зависеть от сборки Apache. Сейчас для `Apache 2.4.35 Win64` нужна библиотека `Microsoft Visual C++ 2015 Redistributable Update 3`:

<https://www.microsoft.com/en-us/download/details.aspx?id=53840>

![Скачивание Microsoft Visual C++ 2015 Redistributable Update 3](img/download-microsoft-visual-cpp-2015.png)

Апач скачиваем не с официального сайта, а с другого, где есть скомпилированная под Windows версия Apache Lounge:

<https://www.apachelounge.com/download/>

![Скачивание Apache Lounge](img/download-apache.png)

Теперь перейдем к скачиваю PHP. Будьте очень внимательны. Надо скачать архив с последней версией PHP вашей битности в версии `Thread Safe`. Я вначале несколько раз не то скачивал и не понимал, почему не работает:

<https://windows.php.net/download/>

![Скачивание PHP](img/download-php.png)

Для работы с базами данных скачиваем phpMyAdmin. На сайте только один вариант для загрузки:

<https://www.phpmyadmin.net/>

![Скачивание phpMyAdmin](img/download-phpmyadmin.png)

Скачиваем MySQL с сайта в виде установщика под Windows:

<https://dev.mysql.com/downloads/installer/>

![Скачивание MySQL](img/download-mysql.png)

И да, у вас сайт попросит зарегистрироваться, чтобы вы могли скачать файл.

## Структура папок

На диске `C:` (или на том, котором вы хотите разместить сервер) создаем папку `Server` в которую скидываем архивы Apache, PHP:

![Папка Server](img/install_01.png)

В этой же папке создаем директорию `htdocs`, в которой создаем папки `www` и `phpmyadmin`. В последнюю копируем наш архив phpMyAdmin:

![Папка Server с директорией htdocs](img/install_02.png)

![Папка htdocs](img/install_03.png)

![Папка phpmyadmin](img/install_04.png)

## Установка Apache

В папке `C:\Server` разархивируем архив с Apache и оставим только папку `Apache24`, а файлы `ReadMe.txt` и `-- Win64 VC15 --` (у вас может по-другому называться) удалим. Архив с Apache тоже удалим, так как он нам не нужен:

![Лишние файлы для удаления](img/install_05.png)

![Содержимое папки Server](img/install_06.png)

Ищем теперь файл `C:\Server\Apache24\conf\httpd.conf` и открываем его в любом текстовом редакторе:

![Файл httpd.conf](img/config-apache_01.png)

Ищем и меняем в нем строчку:

```ini
#ServerName www.example.com:80
```

Меняем на следующее значение:

```ini
ServerName localhost
```

Ищем и меняем в нем строчку:

```ini
Define SRVROOT "c:/Apache24"
```

Меняем на следующее значение:

```ini
Define SRVROOT "c:/Server/Apache24"
```

Ищем и меняем в нем строчку:

```ini
DocumentRoot "${SRVROOT}/htdocs"
```

Меняем на следующее значение:

```ini
DocumentRoot "c:/Server/htdocs/"
```

Ищем и меняем в нем строчку:

```ini
<Directory "${SRVROOT}/htdocs">
```

Меняем на следующее значение:

```ini
<Directory "c:/Server/htdocs/">
```

Ищем и меняем в нем строчку:

```ini
DirectoryIndex index.html
```

Меняем на следующее значение:

```ini
DirectoryIndex index.html index.php index.htm
```

Ищем и меняем в нем строчку:

```ini
#Include conf/extra/httpd-vhosts.conf
```

Меняем на следующее значение:

```ini
Include conf/extra/httpd-vhosts.conf
```

Теперь находим файл `C:\Server\Apache24\conf\extra\httpd-vhosts.conf` и открываем его.

Удаляем всё в нем. И вставляем туда следующие строчки:

```ini
<VirtualHost *:80>
    DocumentRoot "c:/Server/htdocs/www"
    ServerName localhost
    ErrorLog "c:/Server/htdocs/www/error.log"
    CustomLog "c:/Server/htdocs/www/access.log" common
</VirtualHost>

<VirtualHost *:80>
   DocumentRoot "c:/Server/htdocs/phpmyadmin"
   ServerName phpmyadmin
   ErrorLog "c:/Server/htdocs/phpmyadmin/error.log"
   CustomLog "c:/Server/htdocs/phpmyadmin/access.log" common
</VirtualHost>
```

Теперь находим файл `C:\Windows\System32\drivers\etc\hosts` и открываем каким-нибудь блокнотом `под администратором` (иначе изменения при сохранении не сохранятся) и добавьте в него строчку:

```ini
127.0.0.1 phpmyadmin
```

![Файл hosts](img/hosts.png)

Теперь запустим приложение `C:\Server\Apache24\bin\httpd.exe`. При этом может появиться запрос на разрешение к доступу к сетям. Разрешаем:

![Запрос от Брандмауэра Windows](img/config-apache_02.png)

Если вы видите ошибку, как на рисунке ниже, то вы не установили библиотеку от Microsoft, о которой говорилось в самом начале статьи:

![Сообщение об ошибке](img/error.png)

Откроем браузер и введем `http://localhost` и жмем `Enter`. Если видим следующее, то всё хорошо:

![Первый запуск http://localhost](img/config-apache_03.png)

Создадим текстовой файл `index.html` в папке `D:\Server\htdocs\www` со следующим содержимым:

```html
<!DOCTYPE html>
<html>
  <body>
    <h1>Localhost</h1>
    <p>This is page in Localhost.</p>
  </body>
</html>
```

И создадим текстовой файл `index.html` в папке `D:\Server\htdocs\phpmyadmin` со следующим содержимым:

```html
<!DOCTYPE html>
<html>
  <body>
    <h1>PhpMyAdmin</h1>
    <p>This is page in PhpMyAdmin.</p>
  </body>
</html>
```

Теперь, если откроем в браузере `http://localhost`, то получим:

![Проверка доступности HTML файла по адресу http://localhost](img/config-apache_04.png)

А при заходе на адрес `http://phpmyadmin` получим вот это:

![Проверка доступности HTML файла по адресу http://phpmyadmin](img/config-apache_05.png)

Закрываем приложение `httpd.exe`. Тем самым мы закрыли наш созданный сервер. Сделаем так, чтобы сервер был всегда открыт при запуске системы.

Откроем командную строку под администратором. Через поиск находим программу `Командная строка`:

![Поиск приложения командной строки](img/config-apache_06.png)

Запускаем от имени администратора:

![Запуск от имени администратора](img/config-apache_07.png)

![Запущенная командная строка](img/config-apache_08.png)

Вводим там:

```console
c:\Server\Apache24\bin\httpd.exe -k install
```

И нажимаем `Enter`:

![Установка службы Apache24](img/config-apache_09.png)

Служба Apache24 установилась. Теперь сервер будет всегда работать при работе операционной системы.

Закрываем командную строку (а можете и не закрывать: еще пригодится).

Открываем приложение `C:\Server\Apache24\bin\ApacheMonitor.exe`. В трее должна появится иконка:

![Иконка ApacheMonitor в трее](img/apache-monitor_01.png)

Щелкаем по ней и выбираем кнопку `Start`:

![Запуск сервера](img/apache-monitor_02.png)

Если иконка изменилась на зеленый квадратик, то всё в порядке:

![Сервер запущен](img/apache-monitor_03.png)

Если осталась с красной точкой, то проверьте все шаги. И проверьте: вы закрыли или нет `httpd.exe`.

Чтобы каждый раз не заходить в папку `C:\Server\Apache24\bin` для запуска `ApacheMonitor.exe`, то создайте где-нибудь ярлык к программе.

## Установка PHP

Создадим папку `PHP` в папке `C:\Server` и туда разархивируем архив с PHP. Сам архив потом удалим:

![Содержимое папки с PHP](img/install_07.png)

В конец файла `C:\Server\Apache24\conf\httpd.conf` (с которым мы уже работали) добавим в самом конце такие строчки:

```ini
PHPIniDir "C:/Server/PHP"
AddHandler application/x-httpd-php .php
LoadModule php7_module "C:/Server/PHP/php7apache2_4.dll"
```

![Файл httpd.conf](img/config-php_01.png)

В папке `D:\Server\htdocs\www` удаляем файл `index.html` и добавляем текстовой файл `index.php` с таким содержимым:

```php
<?php
phpinfo ();
?>
```

Перезапускаем сервер:

![Перезапуск сервера](img/config-php_02.png)

И в браузере открываем `http://localhost`. Если видите такое,то всё в порядке:

![Результат работы PHP скрипта](img/config-php_03.png)

В папке `C:\Server\PHP` файл `php.ini-development` переименуем в `php.ini` и откроем его в блокноте.

Находим в нем строчку:

```ini
; extension_dir = "ext"
```

И заменяем на:

```ini
extension_dir="C:\Server\PHP\ext"
```

Находим строчки:

```ini
;extension=bz2
;extension=curl
;extension=fileinfo
;extension=gd2
;extension=gettext
;extension=gmp
;extension=intl
;extension=imap
;extension=interbase
;extension=ldap
;extension=mbstring
;extension=exif      ; Must be after mbstring as it depends on it
;extension=mysqli
;extension=oci8_12c  ; Use with Oracle Database 12c Instant Client
;extension=odbc
;extension=openssl
;extension=pdo_firebird
;extension=pdo_mysql
;extension=pdo_oci
;extension=pdo_odbc
;extension=pdo_pgsql
;extension=pdo_sqlite
;extension=pgsql
;extension=shmop
```

В этих строчках убираем точку с запятой в начале строк. То есть получим вот это:

```ini
extension=bz2
extension=curl
extension=fileinfo
extension=gd2
extension=gettext
extension=gmp
extension=intl
extension=imap
extension=interbase
extension=ldap
extension=mbstring
extension=exif      ; Must be after mbstring as it depends on it
extension=mysqli
extension=oci8_12c  ; Use with Oracle Database 12c Instant Client
extension=odbc
extension=openssl
extension=pdo_firebird
extension=pdo_mysql
extension=pdo_oci
extension=pdo_odbc
extension=pdo_pgsql
extension=pdo_sqlite
extension=pgsql
extension=shmop
```

Аналогично поступаем со стоками:

```ini
;extension=soap
;extension=sockets
;extension=sqlite3
;extension=tidy
;extension=xmlrpc
;extension=xsl
```

То есть в них убираем также точку с запятой:

```ini
extension=soap
extension=sockets
extension=sqlite3
extension=tidy
extension=xmlrpc
extension=xsl
```

Найдите в файле строчку:

```ini
short_open_tag = Off
```

И замените ее на:

```ini
short_open_tag = On
```

Создайте в папке `C:\Server` папку `temp`:

![Папка temp в директории Server](img/config-php_04.png)

Найдите в `php.ini` строчку:

```ini
;     session.save_path = "N;/path"
```

И замените ее на:

```ini
session.save_path = "C:\Server\temp"
```

Найдите в `php.ini` строчку:

```ini
upload_max_filesize = 2M
```

И замените ее на:

```ini
upload_max_filesize = 200M
```

Найдите строчку:

```ini
post_max_size = 8M
```

И замените ее на:

```ini
post_max_size = 50M
```

Сохраните и перезапустите сервер. Если видите зеленый треугольник, то всё нормально. Фактически вы настроили сервер, но пока без MySQL:

![Индикация успешного перезапуска сервера](img/config-php_05.png)

## Установка MySQL

Запустим скаченный установщик MySQL, где соглашаемся на условия использования:

![Первое окно мастера установки MySQL](img/install-mysql_01.png)

Выбираем тип установки `Custom`:

![Выбор типа Установки](img/install-mysql_02.png)

Добавляем MySQL Server для установки и устанавливаем:

![Выбор компонентов для установки](img/install-mysql_03.png)

![Список выбранных компонентов для установки](img/install-mysql_04.png)

![Установка](img/install-mysql_05.png)

![Окончание установки компонентов](img/install-mysql_06.png)

![Окно перед конфигурацией MySQL](img/install-mysql_07.png)

Начинаем конфигурировать MySQL:

![Выбор Group Replication](img/install-mysql_08.png)

![Выбор сетевых настроек](img/install-mysql_09.png)

Так как новый тип аутентификации пока не поддерживается в PHP, то выбираем старый способ аутентификации:

![Выбор типа аутентификации](img/install-mysql_10.png)

Вводим пароль для root пользователя. У меня для примера используется пароль `1234`:

![Выбор пароля для root пользователя](img/install-mysql_11.png)

![Настройка сервиса для Windows](img/install-mysql_12.png)

Применяем выбранную конфигурацию:

![Запускаем настройку конфигурации](img/install-mysql_13.png)

![Окончание конфигурации](img/install-mysql_14.png)

![Второй шаг окончания конфигурации](img/install-mysql_15.png)

![Окончание установки](img/install-mysql_16.png)

Проверим работу MySQL. Заменим содержимое файла `D:\Server\htdocs\www\index.php` на следующее:

```php
<?php
$db_conn = new mysqli("localhost", "root", "1234", "mysql");
if (mysqli_connect_errno()) {
  echo 'Connection to database failed:'.mysqli_connect_error();
  exit();
}
else {
  echo 'Ok';
}
?>
```

Вместо `1234` вставьте свой пароль. И перейдите на адрес `http://localhost/`.

Если вы видите `Ok`, то всё хорошо:

![Подключение к базе mysql прошло успешно](img/install-mysql_17.png)

## Установка phpMyAdmin

В папке `D:\Server\htdocs\phpmyadmin` удалим файл `index.html`.

И разархивируем в папку наш скаченный архив с phpmyadmin:

![Содержимое папки phpmyadmin](img/install-phpmyadmin_01.png)

Создайте текстовой файл `config.inc.php` со следующим содержимым:

```php
<?php

$i=0;
$i++;

$cfg['Servers'][$i]['user'] = 'root';
$cfg['Servers'][$i]['password'] = '1234';
$cfg['Servers'][$i]['auth_type'] = 'config';
$cfg['Servers'][$i]['host'] = 'localhost';
$cfg['Servers'][$i]['connect_type'] = 'tcp';
$cfg['Servers'][$i]['compress'] = false;
$cfg['Servers'][$i]['extension'] = 'mysqli';
$cfg['Servers'][$i]['AllowNoPassword'] = true;

?>
```

Разумеется, что пароль вы меняете на свой.

После этого файл сохраняется в папке `D:\Server\htdocs\phpmyadmin`.

Перейдите в браузере по адресу: `http://phpmyadmin`. Если вы увидите работающий phpMyAdmin, то всё работает отлично:

![Запущенный phpMyAdmin](img/install-phpmyadmin_02.png)

## Добавление своего виртуального хоста [дополнительно]

В статье показано как добавлен был виртуальный хост `phpmyadmin`, то есть по адресу `http://phpmyadmin` у вас в браузере открывается ваш подсайт. Аналогичным образом добавляете и другие свои локальные сайты.

В папке `C:\Server\htdocs` создаете папку `[Название вашего локального сайта]`. Туда кидаете файла своего сайта.

В файле `C:\Server\Apache24\conf\extra\httpd-vhosts.conf` добавляете строчки:

```xml
<VirtualHost *:80>
   DocumentRoot "D:/Server/htdocs/[Название вашего локального сайта]"
   ServerName [Название вашего локального сайта]
   ErrorLog "D:/Server/htdocs/[Название вашего локального сайта]/error.log"
   CustomLog "D:/Server/htdocs/[Название вашего локального сайта]/access.log" common
</VirtualHost&gt
```

В файле `C:\Windows\System32\drivers\etc\hosts` под администратором добавляете строчку:

```ini
127.0.0.1 [Название вашего локального сайта]
```

После этого перезагружаете апач сервер через `ApacheMonitor` или перезагрузкой компа.

После этого по адресу `http://[Название вашего локального сайта]` в браузере будет открываться локальный сайт.

## Удаление служб [дополнительно]

В процессе экспериментов по настройке сервера вы можете захотеть начать всё сначала. По крайней мере, у меня такое было часто. Для этого достаточно удалить папки `Server`, так как полноценной установки в Windows не производилось. Но перед этим нужно остановить и удалить службы Apache и MySQL. Ниже приводится алгоритм, как это сделать.

Вызываем программу `Службы`. Способов много. Можно просто через обычный поиск в Windows:

![Поиск программы «Службы»](img/delete-service_01.png)

Останавливаем нашу службу:

![Команда «Остановить службу»](img/delete-service_02.png)

Двойным щелчком по названию службы открываем подробности службы:

![Свойства службы](img/delete-service_03.png)

И копируем имя службы:

![Копирование имени службы](img/delete-service_04.png)

Запускаем от имени администратора командную строку:

![Командная строка](img/delete-service_05.png)

Теперь пропишите команду удаления службы:

```console
sc delete Apache2.4
```

И нажмите `Enter`. Служба удалена:

![Удаление службы](img/delete-service_06.png)

Возможно, придется перезагрузить комп, чтобы служба полностью удалилась. Один раз мне такое потребовалось.

Службу MySQL можно также удалить, но, если вы устанавливали MySQL через установщик, как в этой статье, то лучше просто деинсталлировать MySQL как обычную программу.
