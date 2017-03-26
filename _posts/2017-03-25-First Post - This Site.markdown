---
layout: post
title:  "First Post - This Site"
date:   2017-03-25 23:32:29 -0700
categories:
description: "Jekyll, Twitter Bootstrap, GitHub Pages"
---

Started creating this site ~4 hours ago and now it's up and running on GitHub pages! I've been working a lot more on projects lately and I felt like it would be a good idea to document them, for me to reference in the future.

And the first project I'll write about on here is this site itself! Just a few hours ago I first started looking into how to create a blog and what to use (Flask, Django, Node, React...). But I didn't want WordPress or anything like that because I've used it before and I wanted more customizability and I also wanted to learn more about how to create one from scratch. I found Jekyll, which I had heard of before, and seemed interesting and simple enough. I like that it's still a static site so I don't need to set up a web server.

Steps:

1. Setup
  * [setting up jekyll on windows](http://jekyll-windows.juthilo.com/)
  * [jekyll docs](https://jekyllrb.com/docs)

2. Incorporating Bootstrap
  * [tutorial](http://veithen.github.io/2015/03/26/jekyll-bootstrap.html)

Everything went pretty smoothly, never got stuck on any big issues. I copied the default theme (minima) from the gem into the local folder so I could modify it.

* replaced navbar with bootstrap navbar
* removed footer
* increased $content-width in main.scss to 1200
* inspired by [this theme][1] to change font-family to consolas

This is pretty much exactly what I wanted! It allows me to focus on content when I want to write content, without doing nasty html copy pasting and writing tags all over the place. But at the same time, when I want to customize the html I can! I'm kinda surprised how smooth and easy this was to set up actually.
___
### For reference:
___

`jekyll serve` or `bundle exec jekyll serve` - launches web server

`_posts` directory convention: `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter

code snippet example:

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

[Markdown docs][markdown-docs]

[Markdown cheat sheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)

[Jekyll docs][jekyll-docs]


[markdown-docs]: https://daringfireball.net/projects/markdown/syntax
[jekyll-docs]: https://jekyllrb.com/docs/home
[1]: http://themes.jekyllbootstrap.com/preview/the-program/
