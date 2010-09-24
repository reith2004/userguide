# Общие настройки

[!!] TODO: описание преимуществ статических свойств конфигурации

## Настройки ядра

Первой задачей конфигурирования новой установки Kohana является изменение параметров [Kohana::init] в `application/bootstrap.php`. Вот эти параметры:

`boolean` errors
:   Использование встроенного обработчика ошибок и исключений. (По-умолчанию: `TRUE`) Установите в `FALSE`, чтобы отменить перехват ошибок и исключений фреймворком.

`boolean` profile
:   Использовать возможности встроенного бенчмаркинга. (По-умолчанию: `TRUE`) Установите в `FALSE`, чтобы отменить профилирование. Для увеличения производительности на стадии production данный параметр рекомендуется отключать.

`boolean` caching
:   Кэширование информации о расположении файлов между запросами. (По-умолчанию: `FALSE`) Установите в `TRUE`, чтобы включить кэширование значений абсолютных путей исполняемых файлов. Это значительно ускоряет [Кохана::find_file] и может иногда оказать серьезное влияние на производительность. Используйте на этапе production или для тестирования.

`string` charset
:   Кодировка, используемая во всех операциях ввода-вывода. (По-умолчанию: `"utf-8"`) Должна поддерживаться как [htmlspecialchars](http://php.net/htmlspecialchars), так и [iconv](http://php.net/iconv).

`string` base_url
:   Базовый URL для приложения. (По-умолчанию: `"/"`) Может быть как абсолютным, так и относительным URL. Например, "http://example.com/kohana/" или просто "/kohana/": подходят оба варианта.

`string` index_file
:   Имя PHP файла, который запускает приложение (фронтенд). (По-умолчанию: `"index.php"`) Установите в `FALSE`, если намереваетесь использовать URL rewriting.

`string` cache_dir
:   Директория для хранения файлового кэша. (По-умолчанию: `"application/cache"`) Директория должна быть **доступна для записи**.

## Настройки Cookie

Перед запуском production-версии сайта следует установить значения некоторых статических свойств [Cookie] класса.

`string` salt
:   Уникальная строка salt-значения, которая используется для работы [cookies](security.cookies)

`integer` expiration
:   По-умолчанию: время жизни cookies в секундах

`string` path
:   URL, ограничивающий доступ к cookies

`string` domain
:   Домен, ограничивающий доступ к cookies

`boolean` secure
:   Позволить использовать cookies только по протоколу HTTPS

`boolean` httponly
:   Позволить использовать cookies только по протоколу HTTP (также закрывается доступ через Javascript)

# Конфигурационные файлы

Настройки хранятся в виде PHP файлов примерно такого вида:

~~~
<?php defined('SYSPATH') or die('No direct script access.');

return array(
    'setting' => 'value',
    'options' => array(
        'foo' => 'bar',
    ),
);
~~~

Если конфигурационный файл был назван `myconf.php`, то для доступа к нему можно использовать следующий код:

~~~
$config = Kohana::config('myconf');
$options = $config['options'];
~~~

[Kohana::config] позволяет так же использовать "пути с точкой" для доступа к отдельным ключам конфигурационного массива.

Для получения массива "options":

~~~
$options = Kohana::config('myconf.options');
~~~

Для получения значения ключа "foo" массива "options":

~~~
$foo = Kohana::config('myconf.options.foo');
~~~

Вы можете работать с настроечными массивами как с объектами, если это будет удобнее:

~~~
$options = Kohana::config('myconf')->options;
~~~