---
date: 2018-08-10
categories: [it, tex]
tags: [LaTeX, Установка]
latex: true
download: https://github.com/Harrix/harrix.dev-blog-2018/raw/main/pscyr-ttf-fonts/files/pscyr-ttf-fonts.zip
author: Anton Sergienko
author-email: anton.b.sergienko@gmail.com
license: CC BY 4.0
license-url: https://github.com/Harrix/harrix.dev/blob/main/LICENSE.md
---

# Шрифты PSCyr в варианте TTF

В заметке приведен архив шрифтов из пакета PSCyr в формате `.*ttf`, который понимает Windows.

Пакет [PSCyr](https://github.com/Harrix/harrix.dev-blog-2018/blob/main/pscyr/pscyr.md) — решение для нормального отображения русских букв в LaTex. Всё работает, всё хорошо. Но мне понабились шрифты из пакета установить на Windows (чтобы в Illustrator редактировать PDF файлы, скомпилированные в LaTeX с помощью PSCyr), а в пакете шрифты есть в нескольких вариантах, но ни один из них Windows не переваривает.

Сконвертировал файлы `*.pfb` в \*.ttf` помощью <https://onlinefontconverter.com/>. В архиве есть файлы следующих шрифтов:

- AcademyPSCyr Bold
- AcademyPSCyr Italic
- AcademyPSCyr Regular
- AdvertisementPSCyr
- AntiquaPSCyr Bold
- AntiquaPSCyr BoldItalic
- AntiquaPSCyr Italic
- AntiquaPSCyr Regular
- ArialMT Black
- ArialMT Bold
- ArialMT BoldItalic
- ArialMT Italic
- ArialMT Regular
- CollegePSCyr Bold
- CollegePSCyr Italic
- CollegePSCyr Regular
- CooperPSCyr
- CourierNewPSMT Bold
- CourierNewPSMT BoldItalic
- CourierNewPSMT Italic
- CourierNewPSMT Regular
- ERKurierPSCyr Bold
- ERKurierPSCyr BoldItalic
- ERKurierPSCyr Italic
- ERKurierPSCyr Regular
- HandbookPSCyr Bold
- HandbookPSCyr Italic
- HandbookPSCyr Regular
- JournalPSCyr Bold
- JournalPSCyr Italic
- JournalPSCyr Regular
- Lazurski
- MagazinePSCyr Bold
- MagazinePSCyr Italic
- MagazinePSCyr Regular
- SouvenirPSCyr Bold
- SouvenirPSCyr Regular
- TextbookPSCyr Bold
- TextbookPSCyr Italic
- TextbookPSCyr Regular
- TimesNewRomanPSMT Bold
- TimesNewRomanPSMT BoldItalic
- TimesNewRomanPSMT Italic
- TimesNewRomanPSMT Regular

Шрифты можно установить как обычные Windows шрифты, а также можно установить в папку шрифтов Adobe (если какие-то шрифты не видятся). Это папка `C:\Program Files\Common Files\Adobe\Fonts` на Windows 10 для Adobe Illustrator CC 2018. При этом папку `Fonts` в папке `C:\Program Files\Common Files\Adobe` пришлось создавать самому. Если же какие-то шрифты не будут видеться, то можно поступить так. Установить [PSCyr](https://github.com/Harrix/harrix.dev-blog-2018/blob/main/pscyr/pscyr.md) для MiKTeX. А после этого скопировать всё содержимое папки `C:\Program Files\MiKTeX 2.9\fonts` в папку `C:\Program Files\Common Files\Adobe\Fonts`.
