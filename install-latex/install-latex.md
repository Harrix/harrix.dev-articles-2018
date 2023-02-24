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
---

# Установка и настройка программ для редактирования LaTeX файлов

В данной инструкции даются подробные указания для установки связки MiKTeX + TeXstudio + pscyr на примере чистой системы Windows 7 64 bit (и замечаниями под Windows 8.1). После установки вы получите полноценную систему для редактирования и компиляции LaTeX файлов расширения `*.tex`.

Статья обновлена и переписана в 2021 со статьи 2013 года.

## Общие сведения

`MiKTeX` — программа для компилирования `*.tex` с целью превращения их в PDF файлы. После ее установки вы ее касаться не будете. Все действия будут выполняться через TeXstudio.

`TeXstudio` — редактор `*.tex` файлов. Через нее вы и будете работать почти всё время.

`pscyr` — пакет, с помощью которого подключаются некоторые русские шрифты. В поставке MiKTeX его нет, но бывает крайне полезен. После установки вы также можете про него забыть. Об его установке можно прочитать в статье «[Установка PSCyr для LaTeX](https://github.com/Harrix/harrix.dev-blog-2018/blob/main/pscyr/pscyr.md)».

## Установка MiKTeX

Переходим на сайт <http://www.miktex.org/download>.

И скачиваем установочный файл. Обратите внимание, что он должен быть под нужную «битность» системы. Я скачиваю себе версию для 64 бит:

![Скачивание MiKTeX](img/install-miktex_01.png)

А теперь немного про установку. Можно запустить установку с параметрами по умолчанию и наслаждаться процессом установки.

Но иногда при установке (как минимум на прошлых версиях MiKTeX) вылетает ошибка `The thread function could not be started` на **Windows 7** и **Windows 8.1**. Поэтому в спойлере описан один из способов решения проблемы, который у меня не вызывал такую ошибку, а стандартная установка вызывала.

---

**Если у вас ошибка при установке на примере Windows 7** <!-- !details -->

Щелкните правой кнопкой по файлу установщика и выберете пункт `Исправление неполадок совместимости`:

![Bug fix](img/bug-fix-windows-7_01.png)

Появится вот это окно:

![Bug fix](img/bug-fix-windows-7_02.png)

Отметьте следующие проблемы:

![Bug fix](img/bug-fix-windows-7_03.png)

Скажите, что в Windows Vista все запускалось хорошо:

![Bug fix](img/bug-fix-windows-7_04.png)

В следующем окне запустите программу для начала установки:

![Bug fix](img/bug-fix-windows-7_05.png)

---

---

**Если у вас ошибка при установке на примере Windows 8.1** <!-- !details -->

Щелкните правой кнопкой по файлу установщика и выберете пункт `Исправление неполадок совместимости`:

![Bug fix](img/bug-fix-windows-8.1_01.png)

Появится вот это окно:

![Bug fix](img/bug-fix-windows-8.1_02.png)

Отметьте следующие проблемы:

![Bug fix](img/bug-fix-windows-8.1_03.png)

Скажите, что в Windows Vista все запускалось хорошо:

![Bug fix](img/bug-fix-windows-8.1_04.png)

В следующем окне запустите программу для начала установки:

![Bug fix](img/bug-fix-windows-8.1_05.png)

---

Согласитесь с соглашением:

![Установка MiKTeX](img/install-miktex_02.png)

Программа может быть использована кем угодно:

![Установка MiKTeX](img/install-miktex_03.png)

Путь к программе можете оставить по умолчанию:

![Установка MiKTeX](img/install-miktex_04.png)

Рекомендую включить автоматическую подзагрузку недостающих пакетов:

![Установка MiKTeX](img/install-miktex_05.png)

После этого начинайте основной процесс установки:

![Установка MiKTeX](img/install-miktex_06.png)

![Установка MiKTeX](img/install-miktex_07.png)

Если все прошло хорошо, то установка завершится этим окном:

![Установка MiKTeX](img/install-miktex_08.png)

Пусть MiKTeX проверит наличие обновлений пакетов и себя:

![Установка MiKTeX](img/install-miktex_09.png)

![Установка MiKTeX](img/install-miktex_10.png)

Этот пункт нужен, если исправляли ошибку под спойлерами выше. После этого надо довершить процесс работы по устранению несовместимостей:

---

**Если у вас ошибка при установке, то сюда** <!-- !details -->

Если пользовались решениями, которые описаны выше спойлерами, тот тут два скриншота экранов, которые у вас появятся после установки:

![Bug fix](img/bug-fix-windows-7_06.png)

![Bug fix](img/bug-fix-windows-7_07.png)

---

Перезагрузите комп на всякий случай.

## Установка TeXstudio

Переходим на сайт <https://www.texstudio.org/>.

Нажимаем на кнопку скачивания:

![Скачивание TeXstudio](img/install-texstudio_01.png)

Проблем с установкой не должно возникнуть:

![Начало установки](img/install-texstudio_02.png)

![Установка TeXstudio](img/install-texstudio_03.png)

![Установка TeXstudio](img/install-texstudio_04.png)

![Установка TeXstudio](img/install-texstudio_05.png)

После установки запустите программу:

![TeXstudio](img/texstudio.png)

Создайте новый файл:

![Создание нового файла](img/texstudio-new-document_01.png)

Вставьте в окно редактирования следующий код:

```tex
\documentclass{article}
\begin{document}
Hello world!
\end{document}
```

![Ввод кода документа](img/texstudio-new-document_02.png)

Сохраните файл под каким-нибудь именем:

![Сохранение файла](img/texstudio-save.png)

Скомпилируйте файл:

![Компилирование файла](img/texstudio-run.png)

Справа появилось окно с отображением скомпилированного файла:

![Скомпилированный документ](img/texstudio-result_01.png)

Теперь в папке, где был сохранен `tex` файл, появилось еще несколько файлов. Один из них это конечный PDF файл. Откройте его:

![PDF файл](img/compiled-files_01.png)

Если в нем есть все что нужно, то, значит, процесс установки прошел успешно:

![Открытый PDF документ](img/compiled-files_02.png)

## Установка pscyr

Процесс установки `pscyr` долгий и сложный. Подробное описание процесса изложено в другой статье, а именно «[Установка PSCyr для LaTeX](https://github.com/Harrix/harrix.dev-blog-2018/blob/main/pscyr/pscyr.md)».

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

![Недостаточно памяти](img/error_02.png)

![Ошибка](img/error_03.png)

Поэтому надо произвести некоторые манипуляции.

Вначале увеличим объем памяти для компиляции отдельного графика.

Нажимаем `Пуск` → `Выполнить`:

![Окно «Выполнить»](img/texstudio-config_01.png)

Вводим там следующее:

```console
initexmf --edit-config-file=pdflatex
```

![Ввод команды](img/texstudio-config_02.png)

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

Появится черное окно, в котором начнет идти список файлов. Ничего не делаем и ждем, когда окно само закроется.

Всё. Теперь памяти для компиляции выделено гораздо больше.

Теперь сделаем так, чтобы каждый график компилировался отдельно:

Открываем `TeXstudio`.

Идем в настройки `Options` → `Configure TeXstudio…`:

![Ввод команды](img/texstudio-config_04.png)

Идем в настройки `Commands`. И там находим строчку `PdfLaTeX`:

![Ввод команды](img/texstudio-config_05.png)

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

![Стандартная система сборки библиографии](img/biblio_02.png)

![Измененная система сборки библиографии](img/biblio_03.png)

## Дополнительно

В статье [Проверка орфографии в TeXstudio](https://github.com/Harrix/harrix.dev-blog-2013/blob/main/spell-check-in-texstudio/spell-check-in-texstudio.md) рассказано как настроить проверку орфографии.

Еще по умолчанию в качестве отступа используется знак табуляции, которым в приличном обществе стараются не пользоваться. На скриншотах показано, как их поменять на 2 пробела (кто хочет, может оставить 4 пробела):

![Автоматическая замена табуляции на пробелы](img/tab_01.png)

![Отступ в два пробела](img/tab_02.png)

Вроде всё. После такой вот непростой установки у нас есть полноценная связка для работы с LaTeX файлами.

Если вдруг что-то не получается, то попробуйте снова всё переустановить, не забывая перезагружать компьютер. Например, когда я переписывал эту статью с варианта 2013 года, то по недосмотру допустил ошибку по собственной инструкции и долго её искал и пытался понять, почему ничего не компилируется.
