---
date: 2018-09-29
categories:
  - it
  - programming
tags:
  - Dev C++
  - C++
  - Сложение двух чисел
  - Работа с файлами
author: Anton Sergienko
author-email: anton.b.sergienko@gmail.com
license: CC BY 4.0
license-url: https://github.com/Harrix/harrix.dev/blob/main/LICENSE.md
permalink-source: https://github.com/Harrix/harrix.dev-articles-2018/blob/main/add-2-num-file-devcpp/add-2-num-file-devcpp.md
permalink: https://harrix.dev/ru/articles/2018/add-2-num-file-devcpp/
lang: ru
attribution:
  - author: Remember the dot
    author-site: https://en.wikipedia.org/wiki/User:Remember_the_dot
    license: GNU General Public License
    license-url: https://en.wikipedia.org/wiki/GNU_General_Public_License
    permalink: https://commons.wikimedia.org/wiki/File:Dev-C%2B%2B_4.9.9.2_icon.png
    permalink-date: 2019-06-22
    name: Dev-C++ 4.9.9.2 icon.png
---

# Сложение двух чисел из файла в Dev-C++ (консольное приложение)

![Featured image](featured-image.svg)

В статье рассказывается как в Dev-C++ считать из файла два числа, сложить их, а результат записать в другой файл.

- [Создание проекта](#создание-проекта)
- [Код основной программы](#код-основной-программы)
- [Запуск программы](#запуск-программы)

## Создание проекта

Создайте файл исходного кода:

![Создание файла исходного кода](img/new-source_01.png)

_Рисунок 1 — Создание файла исходного кода_

Напишите болванку приложения:

```cpp
#include <iostream>

using namespace std;

int main () {

  return 0;
}
```

Сохраните где-нибудь файл:

![Сохранение файла исходного кода](img/new-source_02.png)

_Рисунок 2 — Сохранение файла исходного кода_

## Код основной программы

Подключите следующую библиотеку, работающую с файлами через потоки:

```cpp
#include <fstream>
```

А теле главной функции добавьте этот код:

```cpp
//Создаем файловые потоки на ввод и вывод
ifstream in("input.txt");
ofstream out("output.txt");

int a, b, c;

//Считываем из файла числа
in >> a >> b;

c = a + b;

//Записываем в файл числа
out << c;
```

![Код C++ в редакторе](img/cpp.png)

_Рисунок 3 — Код C++ в редакторе_

Обратите внимание, что я тут не использую в конце программы, например, `system("pause")`.

## Запуск программы

Разместите в папку с исходным кодом программы файл `input.txt` со следующим содержимым:

```text
1 3
```

![Файл с входными данными](img/input.png)

_Рисунок 4 — Файл с входными данными_

Запустите приложение:

![Запуск приложения](img/run_01.png)

_Рисунок 5 — Запуск приложения_

Появится черное окно консоли, которое можно закрыть:

![Запущенное приложение](img/run_02.png)

_Рисунок 6 — Запущенное приложение_

При этом в папке с исходным кодом программы появится файл `output.txt`:

![Файл с выходными данными](img/output.png)

_Рисунок 7 — Файл с выходными данными_

И в нем будет хранится результат сложения двух чисел:

```text
4
```
