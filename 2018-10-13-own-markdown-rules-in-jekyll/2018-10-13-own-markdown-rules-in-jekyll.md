---
categories: [it, web]
tags: [jekyll, markdown]
---

# Как добавить свои правила обработки Markdown в Jekyll

Markdown всем хорош, но некоторых возможностей в нем не хватает. Поэтому возникают разные разновидности в виде GFM, Kramdown и др. Но мне даже возможностей Kramdown не хватает. При этом Liquid тэги мне не нравятся. Что делать?

## Пример расширения Markdown

Допустим, вы хотите заменить GIF картинки MP4 аналогами. При этом хотите в Markdown использовать такой же синтаксис, как и для картинок:

```md
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
