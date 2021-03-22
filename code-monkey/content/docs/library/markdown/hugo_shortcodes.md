---
title: "Hugo Markdown Shortcodes"
weight: 2
# bookFlatSection: false
# bookToc: false
# bookHidden: false
# bookCollapseSection: false
---

# Hugo Shortcodes

This is a quick roundup on hugo shortcodes. These are snippets you can drop into your markdown, to further style a page. This article only covers the ones I find usefull. For additional instructions read the official [Documentation](https://gohugo.io/content-management/shortcodes/).

## 1 Figure

`figure` is an extension of the basic Markdown figure implementation. It provides a lot more options then the basic Markdown one.

The following syntax is used to place a figure inside a document:

```markdown
{{</* figure src="/images/computer.png" title="Retro Machine" */>}}
```

The root folder of the `src` parameter points to the `/static` folder inside the projects root folder, but it's possible to define a specific path, using a standard relative path notation `../../folder/folder/file.jpeg`.

The rendered output looks like this:

{{< figure src="/img/computer.png" title="Retro Machine" >}}

The `figure` shortcode provides a variety of additional parameter, which can be set in the opening tag. These are:

{{< hint info >}}

* `src` - URL of the image to be displayed.
* `link` - If the image needs to be hyperlinked, URL of the destination.
* `target` - Optional target attribute for the URL if link parameter is set.
* `rel` - Optional rel attribute for the URL if link parameter is set.
* `alt` - Alternate text for the image if the image cannot be displayed.
* `title` - Image title.
* `caption` - Image caption. Markdown within the value of caption will be rendered.
* `class` - class attribute of the HTML figure tag.
* `height` - height attribute of the image.
* `width` - width attribute of the image.
* `attr` - Image attribution text. Markdown within the value of attr will be rendered.
* `attrlink` - If the attribution text needs to be hyperlinked, URL of the destination.

{{< /hint >}}

### Styled images

A `figure` can be styled using the **height** and **width** parameters in combination with in line HTML. Let's shrink the image above, center it on the screen and provide it with a better caption.

```markdown
<div align="center">
{{</* figure src="/images/computer.png" caption="### Retro Machine" width="250 px"*/>}}
< /div >
```

The rendered output looks like this:

<div align="center">
{{< figure src="/img/computer.png" caption="## ***Retro Machine***" width="250 px">}}
<br>
</div>

This looks much nicer now! Note how standard Markdown syntax worked on the styling of the caption inside the figure tag.

## 2 Highlight

Similar to the figure shortcode, the standard Markdown capabilities on syntax highlighting are extended with Hugo's own `highlight` shortcode. This shortcode takes exactly one required parameter for the programming language to highlight. The following is an example of the basic syntax:

```markdown
{{</* highlight language */>}}
// ... code
{{</* / highlight */>}}
```

The output renders as follows:

{{< highlight python >}}
def foo() -> string:
    return 'bar'
{{< / highlight >}}

The `highlight` shortcode also has additional parameters, to further style it. These are given as a string of key, value pairs. The following options are available:

{{< hint info >}}

* `linenos` - configure line numbers. Valid values are `true`, `false`, `table`, or `inline`. false will turn off line numbers if it’s configured to be on in site config. New in v0.60.0 table will give copy-and-paste friendly code blocks.
* `hl_lines` - lists a set of line numbers or line number ranges to be highlighted.
* `linenostart=int` - starts the line number count from the given number.
* `anchorlinenos` - Configure anchors on line numbers. Valid values are true or false;
* `lineanchors` - Configure a prefix for the anchors on line numbers. Will be suffixed with -, so linking to the line number 1 with the option 
* `lineanchors=prefix` - adds the anchor prefix-1 to the page.

{{< /hint >}}

Details about `highlight` configuration inside `config.toml` can be found [here](https://gohugo.io/getting-started/configuration-markup/#highlight).

## 3 Ref and Relref

Since I came across no restrictions on internal and external linking, with the standard [Markdown syntax](syntax_guide.md), I see no use for this shortcode.

## 4 Youtube

Hugo supports direct embedding of a Youtube player on the page, with its own shortcode. All it needs is the videos ID. Taken the following URL `https://www.youtube.com/watch?v=w7Ft2ymGmfc` for instance, the syntax would look like this:

```markdown
{{</* youtube w7Ft2ymGmfc */>}}
```

and the corresponding output as follows:

{{< youtube w7Ft2ymGmfc >}}
