---
date: 2018-08-02
categories: [it, os]
tags: [Windows]
author: Anton Sergienko
author-email: anton.b.sergienko@gmail.com
license: CC BY 4.0
license-url: https://github.com/Harrix/harrix.dev/blob/main/LICENSE.md
permalink-source: https://github.com/Harrix/harrix.dev-articles-2018/blob/main/disable-hide-extensions/disable-hide-extensions.md
permalink: https://harrix.dev/ru/articles/2018/disable-hide-extensions/
lang: ru
---

# Как сделать видимыми расширения файлов в Windows

![Featured image](featured-image.svg)

При установке Windows первоначально расширения у зарегистрированных типов файлов не показываются. В статье показывается, как это исправить на примере Windows 10.

## Параметры Проводника

Первоначально нужно попасть в `Параметры Проводника`:

![Параметры Проводника](img/folder-options.png)

_Рисунок 1 — Параметры Проводника_

### I способ

Заходим в классическую `Панель управления`, и там заходим в `Параметры Проводника`:

![Шаг 1](img/method-1_01.png)

_Рисунок 2 — Шаг 1_

![Шаг 2](img/method-1_02.png)

_Рисунок 3 — Шаг 2_

![Шаг 3](img/method-1_03.png)

_Рисунок 4 — Шаг 3_

### II способ

В новом приложении `Параметры` вводим `расширений` и открываем `Параметры Проводника`:

![Шаг 1](img/method-2_01.png)

_Рисунок 5 — Шаг 1_

![Шаг 2](img/method-2_02.png)

_Рисунок 6 — Шаг 2_

### III способ

Просто в проводнике идём `Вид` → `Параметры`:

![Шаг 1](img/method-3-1.png)

_Рисунок 7 — Шаг 1_

## Настройка

Теперь в вкладке `Вид` находим `Скрывать расширения для зарегистрированных типов файлов` и снимаем галочку:

![Снятие галочки](img/settings.png)

_Рисунок 8 — Снятие галочки_

Всё. Теперь все файлы в проводнике будут иметь свои расширения.

Было:

![Состояние «Было»](img/before.png)

_Рисунок 9 — Состояние «Было»_

Стало:

![Состояние «Стало»](img/after.png)

_Рисунок 10 — Состояние «Стало»_
