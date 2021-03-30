+++
title = "Задания для ПМ 04.02"
description = "вариант 18"
tags = [
    "ispo"
]
date = "2014-04-02"
categories = [
    "Development",
    "golang",
]
image = "ispo.jpg"
+++

Вариант 18

##  Материалы в папке сайта

Исходные материалы сохранены в отдельной папке проекта.
Мультимедиа размещены на сайте.

## Логотип сайта

Надо сделац

## Шаблон HTML-документа

шапка - лого + заголовок
футер - ФИО + группа

## CSS-файл со стилями

Проверить HTML-код на валидность.

## Тема

На выбор.


```yaml
params:
  CopyrightHTML: "Copyright &#xA9; 2013 John Doe. All Rights Reserved."
  TwitterUser: "spf13"
  SidebarRecentLimit: 5
```

Within a footer layout, you might then declare a `<footer>` which is only
provided if the `CopyrightHTML` parameter is provided, and if it is given,
you would declare it to be HTML-safe, so that the HTML entity is not escaped
again.  This would let you easily update just your top-level config file each
January 1st, instead of hunting through your templates.

```
{{if .Site.Params.CopyrightHTML}}<footer>
<div class="text-center">{{.Site.Params.CopyrightHTML | safeHtml}}</div>
</footer>{{end}}
```

An alternative way of writing the "if" and then referencing the same value
is to use "with" instead. With rebinds the context `.` within its scope,
and skips the block if the variable is absent:

```
{{with .Site.Params.TwitterUser}}<span class="twitter">
<a href="https://twitter.com/{{.}}" rel="author">
<img src="/images/twitter.png" width="48" height="48" title="Twitter: {{.}}"
 alt="Twitter"></a>
</span>{{end}}
```

Finally, if you want to pull "magic constants" out of your layouts, you can do
so, such as in this example:

```
<nav class="recent">
  <h1>Recent Posts</h1>
  <ul>{{range first .Site.Params.SidebarRecentLimit .Site.Recent}}
    <li><a href="{{.RelPermalink}}">{{.Title}}</a></li>
  {{end}}</ul>
</nav>
```


[go]: https://golang.org/
[gohtmltemplate]: https://golang.org/pkg/html/template/
