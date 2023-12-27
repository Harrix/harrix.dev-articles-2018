---
date: 2018-04-16
categories: [it, web]
tags: [Node.js]
author: Anton Sergienko
author-email: anton.b.sergienko@gmail.com
license: CC BY 4.0
license-url: https://github.com/Harrix/harrix.dev/blob/main/LICENSE.md
permalink-source: https://github.com/Harrix/harrix.dev-blog-2018/blob/main/why-npm-check-updates/why-npm-check-updates.md
permalink: https://harrix.dev/ru/blog/2018/why-npm-check-updates/
lang: ru
attribution:
  - {
      author: node.js authors,
      author-site: "https://nodejs.org/",
      license: Public domain,
      license-url: "https://en.wikipedia.org/wiki/Public_domain",
      permalink: "https://commons.wikimedia.org/wiki/File:Node.js_logo.svg",
      permalink-date: 2019-06-21,
      name: Node.js logo.svg,
    }
---

# Зачем нужен npm-check-updates

![Featured image](featured-image.svg)

Для работы с Node.js использую утилиту [npm-check-updates](https://www.npmjs.com/package/npm-check-updates). Она предназначена для поиска новых версий пакетов вашего проекта.

Зачем она нужна, если есть команда `npm update`, которая обновляет пакеты проекта? Дело в том, что не всегда данная команда видит недавно обновившиеся пакеты (или я что-то делаю не так).

Вот яркий пример для чего нужна данная утилита:

![Результат выполнения утилиты ncu](img/ncu-console.png)

_Рисунок 1 — Результат выполнения утилиты ncu_

Команда `npm update` ничего не обновила, но `ncu` увидела, что есть два новых пакета.

Итак, вначале проверяем наличие новых версий пакетов:

```console
ncu
```

После этого принудительно обновляем файл `package.json` и обновляем пакеты уже согласно изменившемуся пакету:

```console
ncu -u
npm i
```
