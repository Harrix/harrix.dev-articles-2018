---
date: 2018-08-02
categories: [it, os]
tags: [Windows]
author: Anton Sergienko
author-email: anton.b.sergienko@gmail.com
license: CC BY 4.0
license-url: https://github.com/Harrix/harrix.dev/blob/main/LICENSE.md
url-src: https://github.com/Harrix/harrix.dev-blog-2018/blob/main/disable-hide-extensions/disable-hide-extensions.md
url: https://harrix.dev/ru/blog/2018/disable-hide-extensions/
---

# Как сделать видимыми расширения файлов в Windows

При установке Windows первоначально расширения у зарегистрированных типов файлов не показываются. В статье показывается, как это исправить на примере Windows 10.

## Параметры Проводника

Первоначально нужно попасть в `Параметры Проводника`:

![Параметры Проводника](img/folder-options.png)

### I способ

Заходим в классическую `Панель управления`, и там заходим в `Параметры Проводника`:

![Шаг 1](img/method-1_01.png)

![Шаг 2](img/method-1_02.png)

![Шаг 3](img/method-1_03.png)

### II способ

В новом приложении `Параметры` вводим `расширений` и открываем `Параметры Проводника`:

![Шаг 1](img/method-2_01.png)

![Шаг 2](img/method-2_02.png)

### III способ

Просто в проводнике идём `Вид` → `Параметры`:

![Шаг 1](img/method-3-1.png)

## Настройка

Теперь в вкладке `Вид` находим `Скрывать расширения для зарегистрированных типов файлов` и снимаем галочку:

![Снятие галочки](img/settings.png)

Всё. Теперь все файлы в проводнике будут иметь свои расширения.

Было:

![Состояние «Было»](img/before.png)

Стало:

![Состояние «Стало»](img/after.png)
