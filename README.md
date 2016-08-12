# Blackburn

Blackburn is a clear and responsive theme for [Hugo](//gohugo.io).

## Overview

* Based on Yahoo's [Pure CSS] (http://purecss.io/) (v0.6.0)
* Fixed sidebar with social links:
  * Twitter
  * GNU social
  * Facebook
  * Google+
  * Weibo
  * Instagram
  * Flickr
  * Pinterest
  * YouTube
  * Vimeo
  * Vine
  * SlideShare
  * LinkedIn
  * Xing
  * Reddit
  * Hacker News
  * GitHub
  * Bitbucket
  * Stack Overflow
  * Server Fault
  * Steam
  * Last.fm
  * Keybase
* Client-side syntax highlighting by [Highlight.js](//highlightjs.org) (v9.1.0)
* Web analytics by Google Analytics
* Comments by Disqus
* Icons by Font Awesome (v4.5.0)

## Demo

* [Demo](http://themes.gohugo.io/theme/blackburn/)
* You can also see it in action on my personal website [here](http://yoshiharuyamashita.com/)

## Screenshots

![screenshot](/images/screenshot.png)

## Installation

In your Hugo site directory, run:

```shell
$ mkdir themes
$ cd themes
$ git clone https://github.com/yoshiharuyamashita/blackburn.git
```

or download from [here](//github.com/yoshiharuyamashita/blackburn/archive/master.zip).

See [Hugo Quickstart Guide](//gohugo.io/overview/quickstart/) for more information.

## Configuration

Example config.toml:

```toml
baseurl = "http://example.com/"
languageCode = "en-us"
title = "Blackburn Theme Demo"
theme = "blackburn"
author = "Yoshiharu Yamashita"
# Shown in the side menu
copyright = "&copy; 2016. All rights reserved."
canonifyurls = true
paginate = 10

[indexes]
  tag = "tags"
  topic = "topics"

[params]
  # Shown in the home page
  subtitle = "A Hugo Theme"
  brand = "Blackburn"
  googleAnalytics = "Your Google Analytics tracking ID"
  disqus = "Your Disqus shortname"
  # CSS name for highlight.js
  highlightjs = "androidstudio"
  dateFormat = "02 Jan 2006, 15:04"

[menu]
  # Shown in the side menu.
  [[menu.main]]
    name = "Home"
    pre = "<i class='fa fa-home fa-fw'></i>"
    weight = 0
    identifier = "home"
    url = "/"
  [[menu.main]]
    name = "Posts"
    pre = "<i class='fa fa-list fa-fw'></i>"
    weight = 1
    identifier = "post"
    url = "/post/"
  [[menu.main]]
    name = "About"
    pre = "<i class='fa fa-user fa-fw'></i>"
    weight = 2
    identifier = "about"
    url = "/about/"
  [[menu.main]]
    name = "Contact"
    pre = "<i class='fa fa-phone fa-fw'></i>"
    weight = 3
    url = "/contact/"

[social]
  # Link your social networking accounts to the side menu
  # by entering your username or ID.

  # SNS microblogging
  twitter = "*"
  # gnusocial = "*" # Specify href (e.g. https://quitter.se/yourusername)
  facebook = "*"
  # googleplus = "*"
  # weibo = "*"

  # SNS photo/video sharing
  instagram = "*"
  # flickr = "*"
  # pinterest = "*"
  # youtube = "*"
  # vimeo = "*"
  # vine = "*"
  # slideshare = "*"

  # SNS career oriented
  # linkedin = "*"
  # xing = "*"

  # SNS news
  # reddit = "*"
  # hackernews = "*"

  # Techie
  github = "yoshiharuyamashita"
  # bitbucket = "*"
  # stackoverflow = "*"
  # serverfault = "*"

  # Gaming
  # steam = "*"

  # Music
  # lastfm = "*"

  # Other
  # keybase = "*"
```

## Usage

* Write Markdown files in `content/post`
* Add fixed pages (e.g., about.md) to the side menu by defining them under `[menu]` in the config.toml:

```toml
[[menu.main]]
  name = "About"
  pre = "<i class='fa fa-user fa-fw'></i>"
  weight = 2
  identifier = "about"
  url = "/about/"
```

## Shortcodes

### Positional

```
{{% fluid_img "/path/to/img" %}}
```

### Named

```
{{% fluid_img class="pure-u-1-2" src="/path/to/img" alt="img description" %}}
{{% fluid_img class="pure-u-1-3" src="/path/to/img" caption="img description" %}}
```

* `class`, `alt` and `caption` are optional.
* See [Pure CSS Grids](http://purecss.io/grids/) for possible `class` values.

## License

* [MIT](//opensource.org/licenses/MIT)
