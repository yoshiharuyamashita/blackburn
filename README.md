# Blackburn

Blackburn is a clear and responsive theme for [Hugo](//gohugo.io). You can see it in action on my personal website [here](//yoshiharuyamashita.com/).

## Overview

* Based on Yahoo's [Pure CSS] (//purecss.io/)
* Fixed sidebar with social links:
  * Twitter
  * Facebook
  * Instagram
  * GitHub
  * Stack Overflow
  * LinkedIn
* Client-side syntax highlighting by [Highlight.js](//highlightjs.org)
* Web analytics by Google Analytics
* Comments by Disqus
* Icons by Font Awesome

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
baseurl = "http://replace-this-with-your-hugo-site.com/"
title = "Your site title"
author = "Your name"
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
  # Link your social networking accouns to the side menu
  # by entering your username or ID.
  twitter = "*"
  facebook = "*"
  instagram = "*"
  github = "yoshiharuyamashita"
  stackoverflow = "*"
  linkedin = "*"
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

## License

* [MIT](//opensource.org/licenses/MIT)
