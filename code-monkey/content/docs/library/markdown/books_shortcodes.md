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

Columns are the perfect tool for additional page styling. They provide a handy method to combine pictures and text. A good example for this is the homepage of this project. The syntax for this shortcode looks like this:

```markdown
{{</* columns */>}} <!-- begin columns block -->
// Content goes here ...
<---> <!-- magic separator, between columns -->
// Content goes here ...
<---> <!-- magic separator, between columns -->
// Content goes here ...
{{</* /columns */>}}
```

{{< columns >}}

## Left Block

Here is some text inside the left column.

<--->

## Middle Block

{{< figure src="/img/question.png" width="100px">}}

<--->

## Right Block

Here is some text inside the right column.

{{< /columns >}}

There is no specific limitation to the number of columns used. Like shown in the next example,columns can even be used to realize something like a grid layout.

{{< columns >}}

{{< figure src="/img/video.png" width="250px">}}

<--->

{{< figure src="/img/terminal.png" width="250px">}}

<--->

{{< figure src="/img/doc.png" width="250px">}}

<--->

{{< figure src="/img/banana.png" width="250px">}}

<--->

{{< figure src="/img/git.png" width="250px">}}

<--->

{{< figure src="/img/guide.png" width="250px">}}

<--->

{{< figure src="/img/info.png" width="250px">}}

<--->

{{< figure src="/img/check.png" width="250px">}}

{{< /columns >}}



## 2 Details

The `details` shortcode is used to highlight content. It provides a caption to the block and makes the content expandable. The behavior can configured with arguments. The basic syntax is the following:

```markdown
{{</* details title="Title" open=true */>}}
// Content goes here ...
{{</* /details */>}}
```

This a rendered example:

{{< details title="Expanded detail box" open=true >}}

This is something I want to highlight!

{{< /details >}}

A closed one looks like this:

{{< details title="Folded detail box" open=false >}}

This is something not so important you can look up.

{{< /details >}}

## 3 Hints

Hints are a good way to highlight content as either a coloroed `warning`, `danger` or `info` box. The basic syntax is:

```markdown
{{</* hint type */>}}
// Content goes here ...
{{</* /hint */>}}
```

The rendered options look like this:

{{< hint info >}}
**This is an Info**  
This is some thing I want to point out.
{{< /hint >}}

{{< hint warning>}}
**This is a Warning!**  
Be aware of the following ... Spoilers ahead!
{{< /hint >}}

{{< hint danger >}}
**Danger!!!**  
Don't do the following, or the application will crash!
{{< /hint >}}

## 4 Tabs

Sometimes content has to be ordered into different categories. A good example is different use cases in terms of operating systems. Create a tab box with the following syntax:

```markdown
{{</* tabs uniqueid */>}}

{{</* tab name >*/}} 
// Tab Content ... 
{{</* /tab */>}}

{{</* /tabs */>}}
```

A rendered example looks like this:

{{< tabs "operatinSystems" >}}

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
