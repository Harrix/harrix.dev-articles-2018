---
date: 2018-08-03
categories: [it, tex]
tags: [LaTeX, Установка]
latex: true
update: 2021-07-24
author: Anton Sergienko
author-email: anton.b.sergienko@gmail.com
license: CC BY 4.0
license-url: https://github.com/Harrix/harrix.dev/blob/main/LICENSE.md
permalink-source: https://github.com/Harrix/harrix.dev-articles-2018/blob/main/install-latex/install-latex.md
permalink: https://harrix.dev/ru/articles/2018/install-latex/
lang: ru
attribution:
  - { author: EmilJ, author-site: "https://commons.wikimedia.org/wiki/User:EmilJ", license: GNU
        General Public License, license-url: "https://en.wikipedia.org/wiki/GNU_General_Public_License", permalink: "https://commons.wikimedia.org/wiki/File:LaTeX_logo.svg", permalink-date: 2019-03-17, name: LaTeX logo.svg }
---

# Установка и настройка программ для редактирования LaTeX файлов

![Featured image](featured-image.svg)

В данной инструкции даются подробные указания для установки связки MiKTeX + TeXstudio + pscyr на примере чистой системы Windows 7 64 bit (и замечаниями под Windows 8.1). После установки вы получите полноценную систему для редактирования и компиляции LaTeX файлов расширения `*.tex`.

Статья обновлена и переписана в 2021 со статьи 2013 года.

## Общие сведения

`MiKTeX` — программа для компилирования `*.tex` с целью превращения их в PDF файлы. После ее установки вы ее касаться не будете. Все действия будут выполняться через TeXstudio.

`TeXstudio` — редактор `*.tex` файлов. Через нее вы и будете работать почти всё время.

`pscyr` — пакет, с помощью которого подключаются некоторые русские шрифты. В поставке MiKTeX его нет, но бывает крайне полезен. После установки вы также можете про него забыть. Об его установке можно прочитать в статье «[Установка PSCyr для LaTeX](https://github.com/Harrix/harrix.dev-articles-2018/blob/main/pscyr/pscyr.md)<!-- https://harrix.dev/ru/articles/2018/pscyr/ -->».

## Установка MiKTeX

Переходим на сайт <http://www.miktex.org/download>.

И скачиваем установочный файл. Обратите внимание, что он должен быть под нужную «битность» системы. Я скачиваю себе версию для 64 бит:

![Скачивание MiKTeX](img/install-miktex_01.png)

_Рисунок 1 — Скачивание MiKTeX_

А теперь немного про установку. Можно запустить установку с параметрами по умолчанию и наслаждаться процессом установки.

Но иногда при установке (как минимум на прошлых версиях MiKTeX) вылетает ошибка `The thread function could not be started` на **Windows 7** и **Windows 8.1**. Поэтому в спойлере описан один из способов решения проблемы, который у меня не вызывал такую ошибку, а стандартная установка вызывала.

---

**Если у вас ошибка при установке на примере Windows 7** <!-- !details -->

Щелкните правой кнопкой по файлу установщика и выберете пункт `Исправление неполадок совместимости`:

![Bug fix](img/bug-fix-windows-7_01.png)

_Рисунок 2 — Bug fix_

Появится вот это окно:

![Bug fix](img/bug-fix-windows-7_02.png)

_Рисунок 3 — Bug fix_

Отметьте следующие проблемы:

![Bug fix](img/bug-fix-windows-7_03.png)

_Рисунок 4 — Bug fix_

Скажите, что в Windows Vista все запускалось хорошо:

![Bug fix](img/bug-fix-windows-7_04.png)

_Рисунок 5 — Bug fix_

В следующем окне запустите программу для начала установки:

![Bug fix](img/bug-fix-windows-7_05.png)

_Рисунок 6 — Bug fix_

---

---

**Если у вас ошибка при установке на примере Windows 8.1** <!-- !details -->

Щелкните правой кнопкой по файлу установщика и выберете пункт `Исправление неполадок совместимости`:

![Bug fix](img/bug-fix-windows-8.1_01.png)

_Рисунок 7 — Bug fix_

Появится вот это окно:

![Bug fix](img/bug-fix-windows-8.1_02.png)

_Рисунок 8 — Bug fix_

Отметьте следующие проблемы:

![Bug fix](img/bug-fix-windows-8.1_03.png)

_Рисунок 9 — Bug fix_

Скажите, что в Windows Vista все запускалось хорошо:

![Bug fix](img/bug-fix-windows-8.1_04.png)

_Рисунок 10 — Bug fix_

В следующем окне запустите программу для начала установки:

![Bug fix](img/bug-fix-windows-8.1_05.png)

_Рисунок 11 — Bug fix_

---

Согласитесь с соглашением:

![Установка MiKTeX](img/install-miktex_02.png)

_Рисунок 12 — Установка MiKTeX_

Программа может быть использована кем угодно:

![Установка MiKTeX](img/install-miktex_03.png)

_Рисунок 13 — Установка MiKTeX_

Путь к программе можете оставить по умолчанию:

![Установка MiKTeX](img/install-miktex_04.png)

_Рисунок 14 — Установка MiKTeX_

Рекомендую включить автоматическую подзагрузку недостающих пакетов:

![Установка MiKTeX](img/install-miktex_05.png)

_Рисунок 15 — Установка MiKTeX_

После этого начинайте основной процесс установки:

![Установка MiKTeX](img/install-miktex_06.png)

_Рисунок 16 — Установка MiKTeX_

![Установка MiKTeX](img/install-miktex_07.png)

_Рисунок 17 — Установка MiKTeX_

Если все прошло хорошо, то установка завершится этим окном:

![Установка MiKTeX](img/install-miktex_08.png)

_Рисунок 18 — Установка MiKTeX_

Пусть MiKTeX проверит наличие обновлений пакетов и себя:

![Установка MiKTeX](img/install-miktex_09.png)

_Рисунок 19 — Установка MiKTeX_

![Установка MiKTeX](img/install-miktex_10.png)

_Рисунок 20 — Установка MiKTeX_

Этот пункт нужен, если исправляли ошибку под спойлерами выше. После этого надо довершить процесс работы по устранению несовместимостей:

---

**Если у вас ошибка при установке, то сюда** <!-- !details -->

Если пользовались решениями, которые описаны выше спойлерами, тот тут два скриншота экранов, которые у вас появятся после установки:

![Bug fix](img/bug-fix-windows-7_06.png)

_Рисунок 21 — Bug fix_

![Bug fix](img/bug-fix-windows-7_07.png)

_Рисунок 22 — Bug fix_

---

Перезагрузите комп на всякий случай.

## Установка TeXstudio

Переходим на сайт <https://www.texstudio.org/>.

Нажимаем на кнопку скачивания:

![Скачивание TeXstudio](img/install-texstudio_01.png)

_Рисунок 23 — Скачивание TeXstudio_

Проблем с установкой не должно возникнуть:

![Начало установки](img/install-texstudio_02.png)

_Рисунок 24 — Начало установки_

![Установка TeXstudio](img/install-texstudio_03.png)

_Рисунок 25 — Установка TeXstudio_

![Установка TeXstudio](img/install-texstudio_04.png)

_Рисунок 26 — Установка TeXstudio_

![Установка TeXstudio](img/install-texstudio_05.png)

_Рисунок 27 — Установка TeXstudio_

После установки запустите программу:

![TeXstudio](img/texstudio.png)

_Рисунок 28 — TeXstudio_

Создайте новый файл:

![Создание нового файла](img/texstudio-new-document_01.png)

_Рисунок 29 — Создание нового файла_

Вставьте в окно редактирования следующий код:

```tex
\documentclass{article}
\begin{document}
Hello world!
\end{document}
```

![Ввод кода документа](img/texstudio-new-document_02.png)

_Рисунок 30 — Ввод кода документа_

Сохраните файл под каким-нибудь именем:

![Сохранение файла](img/texstudio-save.png)

_Рисунок 31 — Сохранение файла_

Скомпилируйте файл:

![Компилирование файла](img/texstudio-run.png)

_Рисунок 32 — Компилирование файла_

Справа появилось окно с отображением скомпилированного файла:

![Скомпилированный документ](img/texstudio-result_01.png)

_Рисунок 33 — Скомпилированный документ_

Теперь в папке, где был сохранен `tex` файл, появилось еще несколько файлов. Один из них это конечный PDF файл. Откройте его:

![PDF файл](img/compiled-files_01.png)

_Рисунок 34 — PDF файл_

Если в нем есть все что нужно, то, значит, процесс установки прошел успешно:

![Открытый PDF документ](img/compiled-files_02.png)

_Рисунок 35 — Открытый PDF документ_

## Установка pscyr

Процесс установки `pscyr` долгий и сложный. Подробное описание процесса изложено в другой статье, а именно «[Установка PSCyr для LaTeX](https://github.com/Harrix/harrix.dev-articles-2018/blob/main/pscyr/pscyr.md)<!-- https://harrix.dev/ru/articles/2018/pscyr/ -->».

## Настройка установленных программ

Осталось немного настроить программы. Дело в том, что если работать при текущих настройках, то при рисовании графиков через пакет `pgfplots` памяти, выделяемой для компиляции, будет не хватать.

Например, данный документ не скомпилируется. Как с раскомментированными двумя строчками, так и без:

```tex
\documentclass[a4paper,12pt]{report}

\usepackage{geometry}
\usepackage{cmap}
\usepackage[utf8]{inputenc}
\usepackage[english, russian]{babel}
\usepackage{pgfplots}

\geometry{a4paper,top=2cm,bottom=2cm,left=2.5cm,right=1cm}

%\usepgfplotslibrary{external}
%\tikzexternalize[prefix=TikzPictures/]

\begin{document}

  \begin{tikzpicture}
  \begin{axis}[view/h=70]
  \addplot3[
  surf,
  shader=flat,
  samples=60,
  domain=-3:3,y domain=-2:2]
  {sin(deg(x+y^2))};
  \end{axis}
  \end{tikzpicture}

  \begin{tikzpicture}
  \begin{axis}[view/h=70]
  \addplot3[
  surf,
  shader=flat,
  samples=60,
  domain=-3:3,y domain=-2:2]
  {sin(deg(x+y^2))};
  \end{axis}
  \end{tikzpicture}

  \begin{tikzpicture}
  \begin{axis}[view/h=70]
  \addplot3[
  surf,
  shader=flat,
  samples=60,
  domain=-3:3,y domain=-2:2]
  {sin(deg(x+y^2))};
  \end{axis}
  \end{tikzpicture}

\end{document}
```

Вы будете видеть при компиляции подобные ошибки:

![Недостаточно памяти](img/error_01.png)

_Рисунок 36 — Недостаточно памяти_

![Недостаточно памяти](img/error_02.png)

_Рисунок 37 — Недостаточно памяти_

![Ошибка](img/error_03.png)

_Рисунок 38 — Ошибка_

Поэтому надо произвести некоторые манипуляции.

Вначале увеличим объем памяти для компиляции отдельного графика.

Нажимаем `Пуск` → `Выполнить`:

![Окно «Выполнить»](img/texstudio-config_01.png)

_Рисунок 39 — Окно «Выполнить»_

Вводим там следующее:

```console
initexmf --edit-config-file=pdflatex
```

![Ввод команды](img/texstudio-config_02.png)

_Рисунок 40 — Ввод команды_

После нажатия на `Ok` мелькнет черное окно и откроется пустой файл `pdflatex.ini`.

Вводим следующий текст и сохраняем, закрываем, сохраняя:

```console
main_memory=30000000
```

Обратите внимание, что вы здесь можете ввести свой объем памяти, нужный для генерации одного графика. Раньше я вводил в три раза меньше `main_memory=10000000`.

Аналогично вводим команду:

```console
initexmf --dump=pdflatex
```

![Ввод команды](img/texstudio-config_03.png)

_Рисунок 41 — Ввод команды_

Появится черное окно, в котором начнет идти список файлов. Ничего не делаем и ждем, когда окно само закроется.

Всё. Теперь памяти для компиляции выделено гораздо больше.

Теперь сделаем так, чтобы каждый график компилировался отдельно:

Открываем `TeXstudio`.

Идем в настройки `Options` → `Configure TeXstudio…`:

![Ввод команды](img/texstudio-config_04.png)

_Рисунок 42 — Ввод команды_

Идем в настройки `Commands`. И там находим строчку `PdfLaTeX`:

![Ввод команды](img/texstudio-config_05.png)

_Рисунок 43 — Ввод команды_

Меняем содержимое строчки:

```console
pdflatex.exe -synctex=1 -interaction=nonstopmode %.tex
```

Измененная строчка:

```console
pdflatex -shell-escape -interaction=nonstopmode %.tex
```

И нажмите на `Ok`.

Всё. Теперь при компиляции следующего документа мы не получим сообщение об ошибке:

```tex
\documentclass[a4paper,12pt]{report}

\usepackage{geometry}
\usepackage{cmap}
\usepackage[utf8]{inputenc}
\usepackage[english, russian]{babel}
\usepackage{pgfplots}

\geometry{a4paper,top=2cm,bottom=2cm,left=2.5cm,right=1cm}

\usepgfplotslibrary{external}
\tikzexternalize[prefix=TikzPictures/]

\begin{document}

  \begin{tikzpicture}
  \begin{axis}[view/h=70]
  \addplot3[
  surf,
  shader=flat,
  samples=60,
  domain=-3:3,y domain=-2:2]
  {sin(deg(x+y^2))};
  \end{axis}
  \end{tikzpicture}

  \begin{tikzpicture}
  \begin{axis}[view/h=70]
  \addplot3[
  surf,
  shader=flat,
  samples=60,
  domain=-3:3,y domain=-2:2]
  {sin(deg(x+y^2))};
  \end{axis}
  \end{tikzpicture}

  \begin{tikzpicture}
  \begin{axis}[view/h=70]
  \addplot3[
  surf,
  shader=flat,
  samples=60,
  domain=-3:3,y domain=-2:2]
  {sin(deg(x+y^2))};
  \end{axis}
  \end{tikzpicture}

\end{document}
```

![Скомпилированный документ с тремя графиками](img/texstudio-result_02.png)

_Рисунок 44 — Скомпилированный документ с тремя графиками_

Это достигается тем, что при таких настройках каждый рисунок компилируется отдельно, а потом добавляется в итоговый PDF файл.

Обратите внимание, что разделение на отдельные файлы достигается не только изменением настроек программы, но и строчками:

```tex
\usepgfplotslibrary{external}
\tikzexternalize[prefix=TikzPictures/]
```

На всякий случай перезагрузите компьютер.

## Настройка сборки библиографии

Если вы будете использовать для библиографии `Biber`, а не `BibTeX` (например, в [Russian-Phd-LaTeX-Dissertation-Template](https://github.com/AndreyAkinshin/Russian-Phd-LaTeX-Dissertation-Template)), то поменяйте систему сборки библиографии в настройках:

![Настройки TeXstudio](img/biblio_01.png)

_Рисунок 45 — Настройки TeXstudio_

![Стандартная система сборки библиографии](img/biblio_02.png)

_Рисунок 46 — Стандартная система сборки библиографии_

![Измененная система сборки библиографии](img/biblio_03.png)

_Рисунок 47 — Измененная система сборки библиографии_

## Дополнительно

В статье [Проверка орфографии в TeXstudio](https://github.com/Harrix/harrix.dev-articles-2013/blob/main/spell-check-in-texstudio/spell-check-in-texstudio.md)<!-- https://harrix.dev/ru/articles/2013/spell-check-in-texstudio/ --> рассказано как настроить проверку орфографии.

Еще по умолчанию в качестве отступа используется знак табуляции, которым в приличном обществе стараются не пользоваться. На скриншотах показано, как их поменять на 2 пробела (кто хочет, может оставить 4 пробела):

![Автоматическая замена табуляции на пробелы](img/tab_01.png)

_Рисунок 48 — Автоматическая замена табуляции на пробелы_

![Отступ в два пробела](img/tab_02.png)

_Рисунок 49 — Отступ в два пробела_

Вроде всё. После такой вот непростой установки у нас есть полноценная связка для работы с LaTeX файлами.

Если вдруг что-то не получается, то попробуйте снова всё переустановить, не забывая перезагружать компьютер. Например, когда я переписывал эту статью с варианта 2013 года, то по недосмотру допустил ошибку по собственной инструкции и долго её искал и пытался понять, почему ничего не компилируется.
