---
title: "Books - Theme Shortcodes"
weight: 3
# bookFlatSection: false
# bookToc: false
# bookHidden: false
# bookCollapseSection: false
---

# Books - Theme Shortcodes

This article gives a brief overview about special shortcodes, implemented by the Books - Theme for Hugo. The examples in this article are taken from the [projects website](https://themes.gohugo.io//theme/hugo-book/docs/shortcodes/columns/). Since I don't need all of the available options, I will only list those, being used on this page.

## 1 Columns

{{< columns >}} <!-- begin columns block -->
# Left Content
Lorem markdownum insigne...

<---> <!-- magic separator, between columns -->

# Mid Content
Lorem markdownum insigne...

<---> <!-- magic separator, between columns -->

# Right Content
Lorem markdownum insigne...
{{< /columns >}}

## 2 Details

{{< details title="Title" open=true >}}
## Markdown content
Lorem markdownum insigne...
{{< /details >}}

## 3 Hints

{{< hint info >}}
**Markdown content**  
Lorem markdownum insigne. Olympo signis Delphis! Retexi Nereius nova develat
stringit, frustra Saturnius uteroque inter! Oculis non ritibus Telethusa
{{< /hint >}}

{{< hint warning>}}
**Markdown content**  
Lorem markdownum insigne. Olympo signis Delphis! Retexi Nereius nova develat
stringit, frustra Saturnius uteroque inter! Oculis non ritibus Telethusa
{{< /hint >}}

{{< hint danger >}}
**Markdown content**  
Lorem markdownum insigne. Olympo signis Delphis! Retexi Nereius nova develat
stringit, frustra Saturnius uteroque inter! Oculis non ritibus Telethusa
{{< /hint >}}

## 4 Tabs

{{< tabs "uniqueid" >}}

{{< tab "MacOS" >}} 

### MacOS Content 

{{< /tab >}}

{{< tab "Linux" >}}

 ### Linux Content 
 
{{< /tab >}}

{{< tab "Windows" >}}

 ### Windows Content 
 
{{< /tab >}}

{{< /tabs >}}
