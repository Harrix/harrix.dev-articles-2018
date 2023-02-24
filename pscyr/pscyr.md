---
date: 2018-08-03
categories: [it, tex]
tags: [LaTeX, Установка]
download: https://github.com/Harrix/harrix.dev-blog-2018/raw/main/pscyr/files/PSCyr.zip
latex: true
author: Anton Sergienko
author-email: anton.b.sergienko@gmail.com
license: CC BY 4.0
license-url: https://github.com/Harrix/harrix.dev/blob/main/LICENSE.md
url-src: https://github.com/Harrix/harrix.dev-blog-2018/blob/main/pscyr/pscyr.md
url: https://harrix.dev/ru/blog/2018/pscyr/
---

# Установка PSCyr для LaTeX

Использую связку TeXstudio 2.12.10 и MiKTeX 2.9.6753 для редактирования $\LaTeX$ файлов. Установка стандартная и вопросов не должна вызывать, но столкнулся с проблемой установки пакета PSCyr для отображения русских шрифтов. Плюс сервер с самим пакетом уже недоступен (как никак всё со времен 2005 года идет).

Статья обновлена и переписана в 2018 со статьи 2013 года.

Статья полезна тем, кто у себя получает ошибку вида: `` File `pscyr.sty' not found ``.

На всякий случай [ссылка](https://github.com/Harrix/harrix.dev-blog-2018/blob/main/install-latex/install-latex.md) на статью «Установка и настройка программ для редактирования LaTeX файлов».

## Пакеты

Скачиваем дистрибутивы пакета: [pscyr-0.4-beta9exp2-type1.tar](files/pscyr-0.4-beta9exp2-type1.tar.gz) и [pscyr-0.4-beta9exp2-tex.tar](files/pscyr-0.4-beta9exp2-tex.tar.gz).

Распаковываем их в одну папку. В итоге получаем папку `PSCyr`. Можно даже и не скачивать те два файла, а скачать сразу вот этот сборный файл: [PSCyr.zip](files/PSCyr.zip).

## Установка

Копируем в папку `MiKTeX`. У меня это `C:\Program Files\MiKTeX` (`C:\Program Files (x86)\MiKTeX` для 32 битной версии). Копируем не папку `PSCyr`, а ее содержимое. И заменяем все файлы, если спросит:

![Папка MiKTeX 2.9](img/install-pscyr_01.png)

На скриншотах папка называется `C:\Program Files\MiKTeX 2.9`, так как еще в 2018 года папка называлась с номером.

Нажимаем `Пуск` и `Выполнить`. Если используете стандартное меню `Пуск` в Windows 10, то просто в меню `Пуск` или поиске начните писать `Выполнить`.

Вводим там следующее:

```console
initexmf --edit-config-file dvips
```

![Выполнение первой команды](img/install-pscyr_02.png)

После нажатия на `OK` мелькнет черное окно и откроется пустой файл `config.ps`.

Вводим следующий текст и сохраняем:

```console
p +pscyr.map
```

![Ввод текста в блокнот](img/install-pscyr_03.png)

Комментарии, которые будут обозначены `%%` в файлах можно не трогать.

Аналогично вводим команду:

```console
initexmf --edit-config-file pdftex
```

В блокноте вводим и сохраняем текст:

```console
+pscyr.map
```

![Ввод команды](img/install-pscyr_04.png)

![Ввод текста в блокнот](img/install-pscyr_05.png)

Аналогично вводим команду:

```console
initexmf --edit-config-file updmap
```

В блокноте вводим и сохраняем текст:

```console
Map pscyr.map
```

![Ввод команды](img/install-pscyr_06.png)

![Ввод текста в блокнот](img/install-pscyr_07.png)

Вводим команду:

```console
updmap
```

Появится черное окно, и ждем, когда оно само закроется. В 2013 году процесс шел несколько минут, сейчас за секунду прошел:

![Ввод команды](img/install-pscyr_08.png)

![Черное окно консоли](img/install-pscyr_09.png)

Вводим команду:

```console
initexmf --edit-config-file dvipdfm
```

В блокноте вводим и сохраняем текст:

```console
f pscyr2.map
```

![Ввод команды](img/install-pscyr_10.png)

![Ввод текста в блокнот](img/install-pscyr_11.png)

Вводим команду:

```console
initexmf -u
```

Появится черное окно, и ждем, когда оно закроется. У меня прошло где-то полминуты:

![Ввод команды](img/install-pscyr_12.png)

![Черное окно консоли](img/install-pscyr_13.png)

Теперь нужно обновить базы данных в `MiKTeX`.

Раньше для этого использовался следующий способ.

Идем `Пуск` → `Все программы` → `MiKTeX 2.9` → `Maintenance(Admin)` → `Setting(Admin)`. Там в разделе `General` жмем `Refresh FNDB`.

Сейчас же в MiKTeX все настройки перешли в `MiKTeX Console`. [Dmitr](https://disqus.com/by/disqus_jfiMmRRSvq/) нашел как повторить нужные действия в новом варианте настроек.

Итак, `Пуск` → `MiKTeX 2.9` → `MiKTeX Console`:

![MiKTeX Console](img/miktex-console_01.png)

Перезапускаем под администратором эту программу:

![MiKTeX Console](img/miktex-console_02.png)

В главном меню идем `Tasks` → `Refresh file name database`. И ждем, когда всё обновиться:

![MiKTeX Console](img/miktex-console_03.png)

![MiKTeX Console](img/miktex-console_04.png)

Выполняем команду:

```console
mkfntmap
```

Появится черное окно, которое само через пару секунд исчезнет:

![MiKTeX Console](img/install-pscyr_14.png)

## Итог

Теперь можно будет использовать нормальные русские шрифты при добавлении пакета в `tex` файл:

```console
\usepackage{pscyr} % Нормальные шрифты
```

Было:

![Состояние «Было»](img/before.png)

Стало:

![Состояние «Стало»](img/after.png)

Пример тестового документа:

```tex
\documentclass{article}
\usepackage[utf8]{inputenc}
\usepackage[english, russian]{babel}
\usepackage{pscyr}
\begin{document}
Привет, мир!
\end{document}
```

Пример со скриншота:

```tex
\documentclass{article}
\usepackage[utf8]{inputenc}
\usepackage[english, russian]{babel}
\usepackage{pscyr}
\begin{document}
\LaTeX{} "--- это своего рода препроцессор текста для \TeX{} "---
программы компьютерной вёрстки. \LaTeX{} является программируемым и
расширяемым, что позволяет автоматизировать большую часть аспектов
набора, включая нумерацию, перекрёстные ссылки, таблицы и изображения
(их размещение и подписи к ним), общий вид страницы, библиографию и
многое-многое другое. \LaTeX{} был первоначально написан Лэсли Лампортом
в 1984-м году и стал наиболее популярным способом использования \TeX{}а;
очень мало людей сегодня пишут на оригинальном \TeX{}е. Текущей
версией является \LaTeXe.
\end{document}
```
