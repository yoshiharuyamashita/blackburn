# DW-Favored-Blackburn

Since the [original repo](https://github.com/yoshiharuyamashita/blackburn) is not updated for a long time, I decide to fork this theme and modify it for my website.  

The changelog is too long to list.

## [Blackburn](https://github.com/yoshiharuyamashita/blackburn)

a clear and responsive theme for [Hugo](//gohugo.io).

## Overview

* Based on Yahoo's [Pure CSS](http://purecss.io/) (v1.0.0)
* Social links: (I delete a lot link lol)
  * LinkedIn
  - LeetCode
  * GitHub

* Client-side syntax highlighting by [Highlight.js](//highlightjs.org)
* Web analytics by Google Analytics
* Comments by Disqus
* Icons by Font Awesome

## [Demo](https://dwy6626.github.io/)

![screenshot](./demo.png)

## Installation

In your Hugo site directory, run:

```shell
$ mkdir themes
$ cd themes
$ git submodule add https://github.com/dwy6626/dw-favored-blackburn.git themes/dw-favored-blackburn
```

See [Hugo Quickstart Guide](//gohugo.io/overview/quickstart/) for more information.

## Configuration

**TODO**

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

* Override the theme by linking to custom CSS files or URLs:

```toml
[params]
  custom_css = ["css/my.css"]
```

* Add new behaviours by linking to custom JS files or URLs:

```toml
[params]
  custom_js = ["js/my.js", "https://cdnjs.cloudflare.com/ajax/libs/zooming/1.4.2/zooming.min.js"]
```

## Shortcodes

### pure_table
```
{{< pure_table
  "columnName1|columnName2|...|columnName99"
  "dataValue1|dataValue2|...|dataValue99"
  "dataValue1|dataValue2|...|dataValue99"
  "dataValue1|dataValue2|...|dataValue99"
  "... and so on"
>}}
```

where each positional parameter is separated by the vertical bar (i.e., |). The resulting `<table>` is set to have `class="pure-table pure-table-striped"`.

### fluid_imgs

```
{{< fluid_imgs
  "class|src|alt"
  "class|src|alt"
  "... and so on"
>}}
```

where each positional parameter is separated by the vertical bar (i.e., |).

- `class`: specifies a Pure CSS unit class name (**required**)
- `src`: specifies the URL of an image (**required**)
- `alt`: specifies an alternate text for an image (optional)

See [here](http://yoshiharuyamashita.com/post/hugo-shortcode-to-show-multiple-images/) for examples.

### fluid_img (obsolete)

#### Positional

```
{{% fluid_img "/path/to/img" %}}
```

#### Named

```
{{% fluid_img class="pure-u-1-2" src="/path/to/img" alt="img description" %}}
{{% fluid_img class="pure-u-1-3" src="/path/to/img" caption="img description" %}}
```

* `class`, `alt` and `caption` are optional.
* See [Pure CSS Grids](http://purecss.io/grids/) for possible `class` values.

## License

* [MIT](//opensource.org/licenses/MIT)
