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
url-src: https://github.com/Harrix/harrix.dev-blog-2018/blob/main/bluestacks-for-android-studio/bluestacks-for-android-studio.md
url: https://harrix.dev/ru/blog/2018/bluestacks-for-android-studio/
lang: ru
---

# Эмулятор BlueStacks для Android Studio

![Featured image](featured-image.svg)

В статье рассказывается, как подключить BlueStacks эмулятор к Android Studio для запуска своих разрабатываемых приложений.

Стандартный эмулятор в Android Studio довольно прожорливое и капризное существо. И нормально работает на хороших компьютерах с Intel процессорами. Так что обладателям AMD процессоров вкупе со слабыми машинами приходится плохо. На помощь приходят сторонние эмуляторы. BlueStacks — один из них.

## Скачивание и установка

На сайте <https://www.bluestacks.com/ru/index.html> скачиваем установщик:

![Скачивание установщика](img/download.png)

Обратите внимание, что HyperV и Песочница Windows должны быть отключены на Windows 10 Pro. Обидно.

Установка проста:

![Первоначальное окно установщика](img/install_01.png)

![Процесс установки](img/install_02.png)

Мы увидим работающий эмулятор:

![Эмулятор готов к работе](img/blue-stacks.png)

Если нужно, то можете ввести данные своей учетки от Google, а можно и пропустить:

![Окончание установки](img/install_03.png)

Но пока его использовать в Android Studio не получится (хотя и будет его видеть). Перейдем в настройки эмулятора:

![Настройки эмулятора](img/settings_01.png)

И включим Android Debug Bridge:

![Настройки эмулятора](img/settings_02.png)

## Запуск приложения в Android Studio

Теперь в Android Studio появится новое устройство (эмулятор должен быть запущен):

![Выбор устройства в Android Studio](img/run_01.png)

Выбираете его и в BlueStacks увидите запущенное своё приложение:

![Запущенное приложение](img/run_02.png)
