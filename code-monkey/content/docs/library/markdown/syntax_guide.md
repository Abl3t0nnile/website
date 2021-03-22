---
title: "Markdown Syntax Guide"
weight: 1
# bookFlatSection: false
bookToc: true
# bookHidden: false
# bookCollapseSection: false
---
<div align="center">

# Markdown Syntax Guide

---

</div>

This article offers a sample of basic Markdown syntax that can be used in Hugo content files.

{{< hint info >}}

This article is a shortened adaption of the great [Grav original page](http://learn.getgrav.org/content/markdown).

For further details on the extended Markdown syntax of [Hugo](hugo_shortcodes.md) and [Books - Theme](books_shortcodes.md) see the corresponding articles.

{{< /hint >}}

Let's face it: Writing content for the Web is tiresome. WYSIWYG editors help alleviate this task, but they generally result in horrible code, or worse yet, ugly web pages.

**Markdown** is a better way to write **HTML**, without all the complexities and ugliness that usually accompanies it.

Some of the key benefits are:

1. Markdown is simple to learn, with minimal extra characters, so it's also quicker to write content.
2. Less chance of errors when writing in Markdown.
3. Produces valid XHTML output.
4. Keeps the content and the visual display separate, so you cannot mess up the look of your site.
5. Write in any text editor or Markdown application you like.
6. Markdown is a joy to use!

John Gruber, the author of Markdown, puts it like this:

> The overriding design goal for Markdown’s formatting syntax is to make it as readable as possible.
> The idea is that a Markdown-formatted document should be publishable as-is, as plain text,
> without looking like it’s been marked up with tags or formatting instructions.
> While Markdown’s syntax has been influenced by several existing text-to-HTML filters,
> the single biggest source of inspiration for Markdown’s syntax is the format of plain text email.
>
> -- John Gruber

Without further delay, let us go over the main elements of Markdown and what the resulting HTML looks like!

## 1 Headings

Headings from `h1` through `h6` are constructed with a `#` for each level:

```markdown
# h1 Heading
## h2 Heading
### h3 Heading
#### h4 Heading
##### h5 Heading
###### h6 Heading
```

## 2 Comments

Comments should be HTML compatible.

```html
<!--
This is a comment
-->
```

Comment below should **NOT** be seen:

<!--
This is a comment
-->

## 3 Horizontal Rules

The HTML `<hr>` element is for creating a "thematic break" between paragraph-level elements.
In Markdown, you can create a `<hr>` with any of the following:

* `___`: three consecutive underscores
* `---`: three consecutive dashes
* `***`: three consecutive asterisks

The rendered output looks like this:

___
---
***


## 4 Inline HTML

If you need a certain HTML tag (with a class) you can simply use HTML:

```html
Paragraph in Markdown.

<div class="class">
    This is <b>HTML</b>
</div>

Paragraph in Markdown.
```

## 5 Emphasis

### Bold

For emphasizing a snippet of text with a heavier font-weight.

The following snippet of text is **rendered as bold text**.

```markdown
**rendered as bold text**
__rendered as bold text__
```

### Italics

For emphasizing a snippet of text with italics.

The following snippet of text is _rendered as italicized text_.

```markdown
*rendered as italicized text*
_rendered as italicized text_
```

### Strikethrough

In [GitHub flavored Markdown](https://github.github.com/gfm/), which can be used on this site, you can do strikethroughs.

```markdown
~~Strike through this text.~~
```

The rendered output looks like this:

~~Strike through this text.~~


### Combination

Bold, italics, and strikethrough can be used in combination.

```markdown
***bold and italics***
~~**strikethrough and bold**~~
~~*strikethrough and italics*~~
~~***bold, italics and strikethrough***~~
```

The rendered output looks like this:

***bold and italics***

~~**strikethrough and bold**~~

~~*strikethrough and italics*~~

~~***bold, italics and strikethrough***~~

## 6 Blockquotes

For quoting blocks of content from another source within your document.

Add `>` before any text you want to quote:

```markdown
> **Fusion Drive** combines a hard drive with a flash storage (solid-state drive) 
> and presents it as a single logical volume with the space of both drives combined.
```

The rendered output looks like this:

> **Fusion Drive** combines a hard drive with a flash storage (solid-state drive) 
> and presents it as a single logical volume with the space of both drives combined.

Blockquotes can also be nested:

```markdown
> Donec massa lacus, ultricies a ullamcorper in, fermentum sed augue.
Nunc augue augue, aliquam non hendrerit ac, commodo vel nisi.
>> Sed adipiscing elit vitae augue consectetur a gravida nunc vehicula. Donec auctor
odio non est accumsan facilisis. Aliquam id turpis in dolor tincidunt mollis ac eu diam.
```

The rendered output looks like this:

> Donec massa lacus, ultricies a ullamcorper in, fermentum sed augue.
Nunc augue augue, aliquam non hendrerit ac, commodo vel nisi.
>> Sed adipiscing elit vitae augue consectetur a gravida nunc vehicula. Donec auctor
odio non est accumsan facilisis. Aliquam id turpis in dolor tincidunt mollis ac eu diam.

## 7 Lists

### Unordered

A list of items in which the order of the items does not explicitly matter.

You may use any of the following symbols to denote bullets for each list item:

```markdown
* valid bullet
- valid bullet
+ valid bullet
```

For example:

```markdown
* Lorem ipsum dolor sit amet
* Consectetur adipiscing elit
* Integer molestie lorem at massa
* Facilisis in pretium nisl aliquet
* Nulla volutpat aliquam velit
  * Phasellus iaculis neque
  * Purus sodales ultricies
  * Vestibulum laoreet porttitor sem
  * Ac tristique libero volutpat at
* Faucibus porta lacus fringilla vel
* Aenean sit amet erat nunc
* Eget porttitor lorem
```

The rendered output looks like this:

* Lorem ipsum dolor sit amet
* Consectetur adipiscing elit
* Integer molestie lorem at massa
* Facilisis in pretium nisl aliquet
* Nulla volutpat aliquam velit
  * Phasellus iaculis neque
  * Purus sodales ultricies
  * Vestibulum laoreet porttitor sem
  * Ac tristique libero volutpat at
* Faucibus porta lacus fringilla vel
* Aenean sit amet erat nunc
* Eget porttitor lorem

The HTML looks like this:

### Ordered

A list of items in which the order of items does explicitly matter.

```markdown
1. Lorem ipsum dolor sit amet
2. Consectetur adipiscing elit
3. Integer molestie lorem at massa
4. Facilisis in pretium nisl aliquet
5. Nulla volutpat aliquam velit
6. Faucibus porta lacus fringilla vel
7. Aenean sit amet erat nunc
8. Eget porttitor lorem
```

The rendered output looks like this:

1. Lorem ipsum dolor sit amet
2. Consectetur adipiscing elit
3. Integer molestie lorem at massa
4. Facilisis in pretium nisl aliquet
5. Nulla volutpat aliquam velit
6. Faucibus porta lacus fringilla vel
7. Aenean sit amet erat nunc
8. Eget porttitor lorem


{{< hint info >}}

If you just use `1.` for each number, Markdown will automatically number 
each item. For example:

```markdown
1. Lorem ipsum dolor sit amet
1. Consectetur adipiscing elit
1. Integer molestie lorem at massa
1. Facilisis in pretium nisl aliquet
1. Nulla volutpat aliquam velit
1. Faucibus porta lacus fringilla vel
1. Aenean sit amet erat nunc
1. Eget porttitor lorem
```

The rendered output looks like this:

1. Lorem ipsum dolor sit amet
1. Consectetur adipiscing elit
1. Integer molestie lorem at massa
1. Facilisis in pretium nisl aliquet
1. Nulla volutpat aliquam velit
1. Faucibus porta lacus fringilla vel
1. Aenean sit amet erat nunc
1. Eget porttitor lorem

{{< /hint >}}

### Task Lists

Task lists allow you to create a list of items with checkboxes. To create a task list, add dashes (`-`) and brackets with a space (`[ ]`) before task list items. To select a checkbox, add an x in between the brackets (`[x]`).

```markdown
- [x] Write the press release
- [ ] Update the website
- [ ] Contact the media
```

The rendered output looks like this:

- [x] Write the press release
- [ ] Update the website
- [ ] Contact the media

## 8 Code

### Inline Code

Wrap inline snippets of code with <code>`</code>.

```markdown
In this example, `<section></section>` should be wrapped as **code**.
```

The rendered output looks like this:

In this example, `<section></section>` should be wrapped as **code**.

### Indented Code

Or indent several lines of code by at least four spaces, as in:

```markdown
    // Some comments
    line 1 of code
    line 2 of code
    line 3 of code
```

The rendered output looks like this:

    // Some comments
    line 1 of code
    line 2 of code
    line 3 of code

### Block Fenced Code

Use "fences" <code>```</code> to block in multiple lines of code with a language attribute.

{{< highlight markdown >}}
```markdown
Sample text here...
```
{{< / highlight >}}

### Syntax Highlighting

[GFM]^(GitHub Flavored Markdown) also supports syntax highlighting.

To activate it, simply add the file extension of the language you want to use directly after the first code "fence", <code>```js</code>, and syntax highlighting will automatically be applied in the rendered HTML.

For example, to apply syntax highlighting to JavaScript code:

{{< highlight markdown >}}
```js
grunt.initConfig({
  assemble: {
    options: {
      assets: 'docs/assets',
      data: 'src/data/*.{json,yml}',
      helpers: 'src/custom-helpers.js',
      partials: ['src/partials/**/*.{hbs,md}']
    },
    pages: {
      options: {
        layout: 'default.hbs'
      },
      files: {
        './': ['src/templates/pages/index.hbs']
      }
    }
  }
};
```
{{< / highlight >}}

The rendered output looks like this:

```js
grunt.initConfig({
  assemble: {
    options: {
      assets: 'docs/assets',
      data: 'src/data/*.{json,yml}',
      helpers: 'src/custom-helpers.js',
      partials: ['src/partials/**/*.{hbs,md}']
    },
    pages: {
      options: {
        layout: 'default.hbs'
      },
      files: {
        './': ['src/templates/pages/index.hbs']
      }
    }
  }
};
```

{{< hint info >}}

[Syntax highlighting page](https://gohugo.io/content-management/syntax-highlighting/) 
in **Hugo** Docs introduces more about syntax highlighting, including highlight shortcode.

{{< /hint >}}

## 9 Tables

Tables are created by adding pipes as dividers between each cell, and by adding a line of dashes (also separated by bars) beneath the header. Note that the pipes do not need to be vertically aligned.

```markdown
| Option | Description |
| ------ | ----------- |
| data   | path to data files to supply the data that will be passed into templates. |
| engine | engine to be used for processing templates. Handlebars is the default. |
| ext    | extension to be used for dest files. |
```

The rendered output looks like this:

| Option | Description |
| ------ | ----------- |
| data   | path to data files to supply the data that will be passed into templates. |
| engine | engine to be used for processing templates. Handlebars is the default. |
| ext    | extension to be used for dest files. |

{{< details title='' open=true >}}

Adding a colon on the right side of the dashes below any heading will right align text for that column.

Adding colons on both sides of the dashes below any heading will center align text for that column.

```markdown
| Option | Description |
|:------:| -----------:|
| data   | path to data files to supply the data that will be passed into templates. |
| engine | engine to be used for processing templates. Handlebars is the default. |
| ext    | extension to be used for dest files. |
```

The rendered output looks like this:

| Option | Description |
|:------:| -----------:|
| data   | path to data files to supply the data that will be passed into templates. |
| engine | engine to be used for processing templates. Handlebars is the default. |
| ext    | extension to be used for dest files. |

{{< /details >}}

## 10 Links {#links}

### Basic Link

```markdown
<https://assemble.io>
<contact@revolunet.com>
[Assemble](https://assemble.io)
```

The rendered output looks like this (hover over the link, there is no tooltip):

<https://assemble.io>

<contact@revolunet.com>

[Assemble](https://assemble.io)

### Add a Title

```markdown
[Upstage](https://github.com/upstage/ "Visit Upstage!")
```

The rendered output looks like this (hover over the link, there should be a tooltip):

[Upstage](https://github.com/upstage/ "Visit Upstage!")

### Named Anchors

Named anchors enable you to jump to the specified anchor point on the same page. For example, each of these chapters:

```markdown
## Table of Contents
  * [Chapter 1](#chapter-1)
  * [Chapter 2](#chapter-2)
  * [Chapter 3](#chapter-3)
```

will jump to these sections:

```markdown
## Chapter 1 <a id="chapter-1"></a>
Content for chapter one.

## Chapter 2 <a id="chapter-2"></a>
Content for chapter one.

## Chapter 3 <a id="chapter-3"></a>
Content for chapter one.
```

{{< hint tip >}}

The specific placement of the anchor tag seems to be arbitrary. They are placed inline here since 
it seems to be unobtrusive, and it works.

{{< /hint >}}

## 11 Footnotes

Footnotes allow you to add notes and references without cluttering the body of the document. When you create a footnote, a superscript number with a link appears where you added the footnote reference. Readers can click the link to jump to the content of the footnote at the bottom of the page.

To create a footnote reference, add a caret and an identifier inside brackets (`[^1]`). Identifiers can be numbers or words, but they can’t contain spaces or tabs. Identifiers only correlate the footnote reference with the footnote itself — in the output, footnotes are numbered sequentially.

Add the footnote using another caret and number inside brackets with a colon and text (`[^1]: My footnote.`). You don’t have to put footnotes at the end of the document. You can put them anywhere except inside other elements like lists, block quotes, and tables.

```markdown
This is a digital footnote[^1].
This is a footnote with "label"[^label]

[^1]: This is a digital footnote
[^label]: This is a footnote with "label"
```

This is a digital footnote[^1].

This is a footnote with "label"[^label]

[^1]: This is a digital footnote
[^label]: This is a footnote with "label"

## 12 Images

Images have a similar syntax to links but include a preceding exclamation point.

```markdown
![Banana](/img/banana.png)
```

![Banana](/img/banana.png)

or:

```markdown
![Alt text](/img/monkey.png "The coding Monkey")
```

![Alt text](/img/monkey.png "The coding Monkey")
