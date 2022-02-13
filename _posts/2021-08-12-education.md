---
title: Education
date: 2022-02-06 22:35:00 +00
categories: [Education, Languauges]
tags: [github, git, technical]     # TAG names should always be lowercase
---
Jekyll is a static site generator. Written in Ruby by Tom Preston-Werner, GitHub's co-founder, it is distributed under the open source MIT license. - [Wikipedia](https://en.wikipedia.org/wiki/Jekyll_(software))

[Learn markdown](https://www.markdowntutorial.com/)

#### HTML

```html
<li class="ml-1 mr-1">
    <a target="_blank" href="#">
    <i class="fab fa-twitter"></i>
    </a>
</li>
```

#### CSS

```css
.highlight .c {
    color: #999988;
    font-style: italic; 
}
.highlight .err {
    color: #a61717;
    background-color: #e3d2d2; 
}
```

#### JS

```js
// alertbar later
$(document).scroll(function () {
    var y = $(this).scrollTop();
    if (y > 280) {
        $('.alertbar').fadeIn();
    } else {
        $('.alertbar').fadeOut();
    }
});
```

#### Python

```python
print("Hello World")
```

#### Ruby

```ruby
require 'redcarpet'
markdown = Redcarpet.new("Hello World!")
puts markdown.to_html
```

#### C

```c
printf("Hello World");
```
