# Blackburn

Blackburn is a clear and responsive theme for [Hugo](//gohugo.io).

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
* Pagination
* Favicon

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
  brand = "Brand name"
  twitter = "Your Twitter username"
  facebook = "Your Facebook username"
  instagram = "Your Instagram username"
  github = "Your GitHub username"
  stackoverflow = "Your Stack Overflow user ID (number)"
  linkedin = "Your LinkedIn username"
  googleAnalytics = "Your Google Analytics tracking ID"
  disqus = "Your Disqus shortname"
  # CSS name for highlight.js
  highlightjs = "androidstudio"
```

## Usage

* Write Markdown files in `content/post`
* Add fixed pages (e.g., about.md) to the side menu by creating them in `content` and setting `sidemenu` to `true` in its front matter:

```toml
title = "About"
date = "2014-04-09"
sidemenu = "true"
description = "About me and this site"
```

## License

* [MIT](//opensource.org/licenses/MIT)
