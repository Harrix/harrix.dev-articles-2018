---
date: 2018-10-07
categories: [it, programming]
tags: [Qt, C++, Сложение двух чисел]
author: Anton Sergienko
author-email: anton.b.sergienko@gmail.com
license: CC BY 4.0
license-url: https://github.com/Harrix/harrix.dev/blob/main/LICENSE.md
---

# Сложение двух чисел в Qt 5.12.0 на C++ (консольное приложение)

В статье рассказывается как создать консольное приложение сложения двух чисел в Qt 5.4.0 с использованием библиотеки Qt (то есть с использованием moc компилятора).

В статье [Сложение двух чисел в Qt 5.4.0 на C++ (консольное приложение c moc компилятором)](https://github.com/Harrix/harrix.dev-blog-2015/blob/main/add-2-num-qt-moc-console/add-2-num-qt-moc-console.md) рассказывается, как создать консольное приложение с использованием библиотек Qt.

## Приготовления

В статье [Установка Qt](https://github.com/Harrix/harrix.dev-blog-2018/blob/main/install-qt-mingw/install-qt-mingw.md) и в статье [Установка Qt под Visual Studio, MinGW и для разработки под Android](https://github.com/Harrix/harrix.dev-blog-2018/blob/main/install-qt-advanced/install-qt-advanced.md) узнаете, как всё установить и настроить.

## Создание проекта

![Создание нового проекта](img/new-project_01.png)

Выбираем тип проекта, не основанного на библиотеках Qt:

![Выбор типа нового проекта](img/new-project_02.png)

![Выбор названия проекта](img/new-project_03.png)

![Выбор системы сборки](img/new-project_04.png)

У меня установлено несколько компиляторов, так что для тестирования я выбираю как MinGW, так и Visual Studio. Вы можете выбрать какой-нибудь один:

![Выбор компилятора](img/new-project_05.png)

![Дополнительная настройка проекта](img/new-project_06.png)

![Созданный проект](img/new-project_07.png)

## Болванка приложения C++

Пропишем подключение библиотек:

Пропишем пространство имен стандартной библиотеки, чтобы потом нужно было меньше прописывать кода:

```cpp
using namespace std;//Подключение стандартной библиотеки функций
```

В функции `main` пропишем строчки кода, чтобы русский язык отображался корректно (строчка `setlocale(LC_ALL, "RUSSIAN");` не сработает):

```cpp
setlocale(LC_ALL, "ru_RU.UTF-8");
```

И удалим строчку с выводом `Hello World!`

В итоге получаем готовую болванку программы на C++:

```cpp
#include <iostream>

using namespace std;

int main()
{
  setlocale(LC_ALL, "ru_RU.UTF-8");

  // Тут пишем код

  return 0;
}
```

## Написание кода основной программы

А теперь пропишем основной код нашей программы, где через `cin` мы считываем в переменные наши числа, а через `cout` выводим текст в консоль:

```cpp
int a, b, c;

cout << "Введите первое число:" << endl;
cin >> a;

cout << "Введите второе число:" << endl;
cin >> b;

c = a + b;

cout << "Сумма = " << c << endl;
```

Полная программа будет выглядеть так:

```cpp
#include <iostream>

using namespace std;

int main()
{
  setlocale(LC_ALL, "ru_RU.UTF-8");

  int a, b, c;

  cout << "Введите первое число:" << endl;
  cin >> a;

  cout << "Введите второе число:" << endl;
  cin >> b;

  c = a + b;

  cout << "Сумма = " << c << endl;

  return 0;
}
```

Если вы не хотите использовать русские буквы, то код будет немного проще:

```cpp
#include <iostream>

using namespace std;

int main()
{
  int a, b, c;

  cout << "Input first number:" << endl;
  cin >> a;

  cout << "Input second number:" << endl;
  cin >> b;

  c = a + b;

  cout << "Sum = " << c << endl;

  return 0;
}
```

## Запуск программы

![Запуск программы](img/run_01.png)

При вводе наших чисел получим вот это:

![Результат выполнения программы](img/run_02.png)
