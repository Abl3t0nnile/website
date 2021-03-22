---
title: "Host a GitHub Page with Hugo"
weight: 1
# bookFlatSection: false
# bookToc: false
# bookHidden: false
# bookCollapseSection: false
---

# Host a GitHub Page with Hugo

This is a brief tutorial on how to set up a [GitHub page](https://pages.github.com) with Hugo as a static content generator. It's a simple and easy solution to maintain a personal website and blog. Especially if your a coder and used to working with git and the command line.

{{< hint warning >}}

**Prerequisites**

The following topics are mandatory and won't be covered in this tutorial:

* A working installation of Hugo
* Basic git knowledge
* A GitHub account
* Markdown syntax

{{< /hint >}}

## 1 Hugo

Hugo is one of the key components for this project. [Hugo](https://gohugo.io) is a open-source static site generator. Once installed it can be used inside the command line to build static websites from markdown files. The tool comes with a powerful theme engine and is customizable using templates. Hugo builds the mandatory file system during project creation and is later configured using a `config.toml` file. Hugo lets you create your content as pure markdown files, extend them with a file header and publish them directly to your website, only from the command line. In combination with the right theme this is all you need, if you know your way around git and the terminal, to run your website. I find it a lot easier to deal with, then with wordpress and co.

Hugo has a lot more to offer, than this tutorial covers. For further reading, check the projects homepage.

## 2 Project creation

Before we can start configuring, styling and filling our page with content, we need to build a new Hugo project and set up the connection with github pages.

### 2.1 Github setup

A project like this consists of two github repositories. One so called `production` repo, which contains the static files, github pages will then host our site of, and one repository, I will call the `working` repo from now on, cause mine is named this way. If you're building a portfolio or some other kind of page feel free to use another name. The second repository will contain the actual code and configuration for the site. The `working` repo will later be linked by a submodule to the production repo, to push changes to the site directly to the live version. Go ahead an create two public repositories with no initial content:

* create `working` repo and name it as you like
* create `production` repo and name it `<username>.github.io`

Since we are using a personal github page for our project, the name of the `production` repo has to be `<github_username>.github.io`. Each account is limited to a single personal page, but each repo to a project can have its own site (the setup process is a little bit different though).

Next we have to clone the remote repository to our local drive. Since the root folder of the repo contains everything we will need, we can directly put it into our home directory like I did, since I will have to access it a lot in the future. My repo is called `website` so I'll go along with this name for the purpose of this tutorial.

Clone repository to local drive and cd into it:

```shell
~ $ git clone https://github.com/<username>/website.git
~ $ cd website
```

After cloning we will checkout `main` branch, add `README.md` and `.gitignore` and push the changes to origin:

```shell
# Create main branch an switch to it
~/website $ git checkout -b main
# Create files - Edit them now if you like
~/website $ touch README.md
~/website $ touch .gitignore
# Stage and commit changes
~/website $ git add .
~/website $ git commit -m 'initial commit'
# Push changes to origin/main
~/website $ git push origin main
```

We now have established a local version of our project folder and can continue with building the Hugo project and files.

### 2.2 Create Hugo project

Let's start by running `hugo new site` in our root folder:

```shell
# Hugo command to build a new project
hugo new site <website-name> // named code-monkey for this tutorial
```

The `hugo new site` command did all the heavy lifting for us, by creating a lot of boiler plate code, and the mandatory file structure, in order for hugo to work properly. The project structure should look something like this right now:

    .
    └── /website (git repository)
        ├── /code-monkey
        |   ├── /content
        |   └── lots of other Hugo files ...
        └── .git_files

### 2.3 Establish repository connection

When we're ready to build a version of our site into static HTML data, Hugo will put the resulting files into a folder called `public` inside our root directory. If we now add a submodule to our production repo inside this public folder, we will automatically update the live version of our site, when we commit changes to the submodule.

To add the submodule to the public folder, go to the command line and type the following:

```shell
# Create submodule from main branch of repo and clone it to the public folder
~/website $ git submodule add -b main <username>.github.io public
```

We now have a working connection between the two repositories, which enables us to update the site from our `working` repo.

## 3 Configure Hugo

The next step is to configure the pre build Hugo project, to make it our own. The first step of this process would be to choose a theme.

### 3.1 Choosing a theme

Choosing a theme is a key part of the creation process. I wanted to build a wiki style page, where I could easily manage content on different topics, present it in a clean and structured way, as well as beeing able to search the site for specific content. A blog to accompany the more in depth articles was also mandatory. The [Hugo Themes](https://themes.gohugo.io) page is a wonderful resource on all available themes. I went with [Hugo - Books](https://github.com/alex-shpak/hugo-book), cause it fits everything I need and I also liked the design a lot.

To install a Hugo theme, navigate to the themes github repo and copy its link to clone it into your project. This approach works for most themes. Otherwise the themes documentation will point out how to install it. It seems to be best practice to submodule the theme rather than simply cloning it. Some themes may have different installing instructions specified in their documentation.

```shell
~ /website cd code-monkey
~ //code-monkey $ git submodule add https://github.com/alex-shpak/hugo-book.git themes/book
```

This creates a submodule of the desired theme inside our blog repo. If the theme is later updated, we can simply pull changes from the original repository of the theme.

### 3.2 Configuration

The configuration of Hugo heavily depends on the theme used. In this article I will cover the configuration of the *Books* theme. Please see the documentation of your chosen theme for further instructions.

#### 3.2.1 Basic configuration

Hugo is configured using a `config` file in the root directory. It is possible to divide the configuration over multiple files, by using a `config` folder, but this will not be covered in this tutorial. For a more comprehensive guide check the official [documentation](https://gohugo.io/getting-started/configuration/).

The `config` file can be in either `.toml`, `.yaml` or `.json`. The example below shows the syntax of the first two options.

{{< tabs "config formats" >}}

{{< tab ".yaml" >}}

Hugo `config.yaml` syntax:

```yaml
baseURL: base URL of live version
title: Website Name
author: Website Author
keywords: ["keyA", "keyB", "etc."]
theme: theme-name

params:
  paramName: value
```

{{< /tab >}}

{{< tab ".toml" >}}

Hugo `config.toml` syntax:

```toml
baseURL = base URL of live version
title = Website Name
author = Website Author
keywords = ["keyA", "keyB", "etc."]
theme = theme-name

[params]
  paramName: value
```
 
{{< /tab >}}

{{< /tabs >}}

Some Hugo themes have extensive configuration options. Book on the other hand is luckily quite simple. The following example shows the complete configuration of this website and is annotated with comments for further details:

{{< details title="Book Theme Config" open=false >}}

```yaml
baseURL: https://abl3t0nnile.github.io/
title: a Coding Monkey
author: Gregor Minnemann
keywords: ["personal", "coding", "computer science", "swift", "python", "markdown", "blog", "abl3t0nnile"]
theme: book

# Book configuration
disablePathToLower: true
enableGitInfo: true

# Needed for mermaid/katex shortcodes
markup:
  goldmark:
    renderer:
      unsafe: true
  tableOfContents:
    startLevel: 1
  highlight:
    anchorLineNos: false
    codeFences: true
    guessSyntax: false
    hl_Lines: ""
    lineAnchors: ""
    lineNoStart: 1
    lineNos: true
    lineNumbersInTable: false
    noClasses: true
    style: native
    tabWidth: 4

# Multi-lingual mode config
# There are different options to translate files
# See https://gohugo.io/content-management/multilingual/#translation-by-filename
# And https://gohugo.io/content-management/multilingual/#translation-by-content-directory

#defaultContentLanguage: en

languages:
  en:
    languageName: English
    contentDir: content
    weight: 1
  de:
    languageName: German
    contentDir: content.de
    weight: 2

menu:
  # before: []
  after:
    - name: "Contact"
      url: "mailto:minnemann.g@gmail.com"
      weight: 10
    - name: "Github"
      url: "https://github.com/Abl3t0nnile"
      weight: 20

params:
  # (Optional, default light) Sets color theme: light, dark or auto.
  # Theme 'auto' switches between dark and light modes based on browser/os preferences
  BookTheme: "auto"

  # (Optional, default true) Controls table of contents visibility on right side of pages.
  # Start and end levels can be controlled with markup.tableOfContents setting.
  # You can also specify this parameter per page in front matter.
  BookToC: true

  # (Optional, default none) Set the path to a logo for the book. If the logo is
  # /static/logo.png then the path would be logo.png
  BookLogo: /logo.png

  # (Optional, default none) Set leaf bundle to render as side menu
  # When not specified file structure and weights will be used
  # BookMenuBundle: /menu

  # (Optional, default docs) Specify root page to render child pages as menu.
  # Page is resoled by .GetPage function: https://gohugo.io/functions/getpage/
  # For backward compatibility you can set '*' to render all sections to menu. Acts same as '/'
  BookSection: docs

  # Set source repository location.
  # Used for 'Last Modified' and 'Edit this page' links.
  BookRepo: https://github.com/Abl3t0nnile/website

  # Configure the date format used on the pages
  # - In git information
  # - In blog posts
  BookDateFormat: "January 2, 2006"

  # (Optional, default true) Enables search function with flexsearch,
  # Index is built on fly, therefore it might slowdown your website.
  # Configuration for indexing can be adjusted in i18n folder per language.
  BookSearch: true

  # (Optional, default true) Enables comments template on pages
  # By default partals/docs/comments.html includes Disqus template
  # See https://gohugo.io/content-management/comments/#configure-disqus
  # Can be overwritten by same param in page frontmatter
  BookComments: false

  # /!\ This is an experimental feature, might be removed or changed at any time
  # (Optional, experimental, default false) Enables portable links and link checks in markdown pages.
  # Portable links meant to work with text editors and let you write markdown without {{< relref >}} shortcode
  # Theme will print warning if page referenced in markdown does not exists.
  BookPortableLinks: true

  # /!\ This is an experimental feature, might be removed or changed at any time
  # (Optional, experimental, default false) Enables service worker that caches visited pages and resources for offline use.
  BookServiceWorker: true

  # /!\ This is an experimental feature, might be removed or changed at any time
  # (Optional, experimental, default false) Enables a drop-down menu for translations only if a translation is present.
  BookTranslatedOnly: false
```

{{< /details >}}

Now, that our site is configured, we can now take a first look. To test a page in Hugo, simply type `hugo server` into the command line, while in the project directory. Hugo now creates the website and runs it on a local host. The address will be shown in the command line. As long as you keep the server running, hugo will update the site on every change we make to the code.

Although it's empty our page is now complete. All we have to do, is create some content and push the changes to our production repo.

---

## 4 Content management

To be continued ...

## 5 Publication

To be continued ...
