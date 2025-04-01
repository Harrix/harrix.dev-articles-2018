---
date: 2018-10-13
categories:
  - it
  - web
tags:
  - Jekyll
  - Markdown
author: Anton Sergienko
author-email: anton.b.sergienko@gmail.com
license: CC BY 4.0
license-url: https://github.com/Harrix/harrix.dev/blob/main/LICENSE.md
permalink-source: https://github.com/Harrix/harrix.dev-articles-2018/blob/main/own-markdown-rules-in-jekyll/own-markdown-rules-in-jekyll.md
permalink: https://harrix.dev/ru/articles/2018/own-markdown-rules-in-jekyll/
lang: ru
attribution:
  - author: Dustin Curtis
    author-site: https://github.com/dcurtis
    license: CC0
    license-url: https://github.com/dcurtis/markdown-mark/blob/master/LICENSE
    permalink: https://commons.wikimedia.org/wiki/File:Markdown-mark.svg
    permalink-date: 2019-03-19
    name: Markdown-mark.svg
  - author: Tom Preston-Werner
    author-site: https://github.com/jekyll/brand/
    license: CC BY 4.0
    license-url: https://creativecommons.org/licenses/by/4.0/
    permalink: https://commons.wikimedia.org/wiki/File:Jekyll_(software)_Logo.png
    permalink-date: 2019-06-22
    name: Jekyll (software) Logo.png
---

# Как добавить свои правила обработки Markdown в Jekyll

![Featured image](featured-image.svg)

Markdown всем хорош, но некоторых возможностей в нем не хватает. Поэтому возникают разные разновидности в виде GFM, Kramdown и др. Но мне даже возможностей Kramdown не хватает. При этом Liquid тэги мне не нравятся. Что делать?

<details>
<summary>📖 Содержание</summary>

## Содержание

- [Пример расширения Markdown](#пример-расширения-markdown)
- [Использование Converter](#использование-converter)
- [Использование Jekyll::Hook](#использование-jekyllhook)

</details>

## Пример расширения Markdown

Допустим, вы хотите заменить GIF картинки MP4 аналогами. При этом хотите в Markdown использовать такой же синтаксис, как и для картинок:

```markdown
![Alt text](img/result.mp4)
```

Но в этом случае они будут парситься как `<img>` тэг, а не как `<video>`. В общем, нам нужно получить такой HTML код:

```html
<video autoplay loop muted playsinline>
  <source src="img/result.mp4" type="video/mp4" />
  Alt text</video
>'
```

Это можно сделать через регулярные выражения на Ruby:

```ruby
def process_mp4 (content)
  regex = /!\[(.*)\]\((.*).(mp4|webm|ogg)\)/
  template = '<video autoplay loop muted playsinline><source src="\2.\3" type="video/\3">\1</video>'
  content.gsub(regex, template)
end
```

Теперь напишем Jekyll плагин, который поместим в папку `_plugins`.

## Использование Converter

Можно переопределить конвертер Markdown файлов, в котором вначале произвести свои манипуляции, а потом вызвать стандартный конвертер:

```ruby
module Jekyll
  class MyConverter < Converter
    safe false
    priority :high

    def matches(ext)
      ext =~ /^.(md|markdown)$/i
    end

    def output_ext(ext)
      ".html"
    end

    def process_mp4 (content)
      regex = /!\[(.*)\]\((.*).(mp4|webm|ogg)\)/
      template = '<video autoplay loop muted playsinline><source src="\2.\3" type="video/\3">\1</video>'
      content.gsub(regex, template)
    end

    def convert(content)
      content = process_mp4(content)

      # Вызов стандартного markdown конвертера
      site = Jekyll::Site.new(@config)
      converter = site.find_converter_instance(Jekyll::Converters::Markdown)
      converter.convert(content)
    end
  end
end
```

Минус этого подхода, что вы в конвертере не сможете получить информацию о посте и его YAML параметрах. По крайней мере у меня не получилось.

## Использование Jekyll::Hook

Можно использовать плагин-хук, который будет срабатывать до используемого Markdown конвертера:

```ruby
module Jekyll
  class MyHookProcess
    class << self
      def process_mp4(content)
        regex = /!\[(.*)\]\((.*).(mp4|webm|ogg)\)/
        template = '<video autoplay loop muted playsinline><source src="\2.\3" type="video/\3">\1</video>'
        content.gsub(regex, template)
      end
    end
  end
end

Jekyll::Hooks.register([:posts], :pre_render) do |post|
  #puts ("post.date = " + post.date)
  #puts ("post.path = " + post.path)
  #puts ("post.url = " + post.url)
  post.content = Jekyll::MyHookProcess.process_mp4(post.content)
end
```

При этом вы можете использовать в данном хуке данные поста: `post.url`, `post.date`, `post.path` и др.
