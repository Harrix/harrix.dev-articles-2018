---
date: 2018-08-16
categories: [it, program]
tags: [Установка, Android Studio, Android, Виртуализация, Эмулятор]
related-id: android-emulator
update: 2021-08-08
author: Anton Sergienko
author-email: anton.b.sergienko@gmail.com
license: CC BY 4.0
license-url: https://github.com/Harrix/harrix.dev/blob/main/LICENSE.md
permalink-source: https://github.com/Harrix/harrix.dev-blog-2018/blob/main/bluestacks-for-android-studio/bluestacks-for-android-studio.md
permalink: https://harrix.dev/ru/blog/2018/bluestacks-for-android-studio/
lang: ru
attribution:
  - author: TechWeek
    author-site: http://downloads.techweekeurope.co.uk/
    license: CC BY 3.0
    license-url: https://creativecommons.org/licenses/by/3.0/
    permalink: https://commons.wikimedia.org/wiki/File:BlueStacks-Logo.jpg
    permalink-date: 2019-06-22
    name: BlueStacks-Logo.jpg
---

# Эмулятор BlueStacks для Android Studio

![Featured image](featured-image.svg)

В статье рассказывается, как подключить BlueStacks эмулятор к Android Studio для запуска своих разрабатываемых приложений.

Стандартный эмулятор в Android Studio довольно прожорливое и капризное существо. И нормально работает на хороших компьютерах с Intel процессорами. Так что обладателям AMD процессоров вкупе со слабыми машинами приходится плохо. На помощь приходят сторонние эмуляторы. BlueStacks — один из них.

## Скачивание и установка

На сайте <https://www.bluestacks.com/ru/index.html> скачиваем установщик:

![Скачивание установщика](img/download.png)

_Рисунок 1 — Скачивание установщика_

Обратите внимание, что HyperV и Песочница Windows должны быть отключены на Windows 10 Pro. Обидно.

Установка проста:

![Первоначальное окно установщика](img/install_01.png)

_Рисунок 2 — Первоначальное окно установщика_

![Процесс установки](img/install_02.png)

_Рисунок 3 — Процесс установки_

Мы увидим работающий эмулятор:

![Эмулятор готов к работе](img/blue-stacks.png)

_Рисунок 4 — Эмулятор готов к работе_

Если нужно, то можете ввести данные своей учетки от Google, а можно и пропустить:

![Окончание установки](img/install_03.png)

_Рисунок 5 — Окончание установки_

Но пока его использовать в Android Studio не получится (хотя и будет его видеть). Перейдем в настройки эмулятора:

![Настройки эмулятора](img/settings_01.png)

_Рисунок 6 — Настройки эмулятора_

И включим Android Debug Bridge:

![Настройки эмулятора](img/settings_02.png)

_Рисунок 7 — Настройки эмулятора_

## Запуск приложения в Android Studio

Теперь в Android Studio появится новое устройство (эмулятор должен быть запущен):

![Выбор устройства в Android Studio](img/run_01.png)

_Рисунок 8 — Выбор устройства в Android Studio_

Выбираете его и в BlueStacks увидите запущенное своё приложение:

![Запущенное приложение](img/run_02.png)

_Рисунок 9 — Запущенное приложение_
