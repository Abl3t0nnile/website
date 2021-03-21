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

{{< details title="Prerequisites" open=true >}}

{{< hint warning >}}

The following topics are mandatory and won't be covered in this tutorial:

* A working installation of Hugo
* Basic git knowledge
* A GitHub account
* Markdown syntax

{{< /hint >}}

{{< /details >}}

## 1 Hugo

Hugo is one of the key components for this project. [Hugo](https://gohugo.io) is a open-source static site generator. Once installed it can be used inside the command line to build static websites from markdown files. The tool comes with a powerful theme engine and is customizable using templates. Hugo builds the mandatory file system during project creation and is later configured using a `config.toml` file. Hugo lets you create your content as pure markdown files, extend them with a file header and publish them directly to your website, only from the command line. In combination with the right theme this is all you need, if you know your way around git and the terminal, to run your website. I find it a lot easier to deal with, then with wordpress and co.

Hugo has a lot more to offer, than this tutorial covers. For further reading, check the projects homepage.

## 2 Project creation

Before we can start configuring, styling and filling our page with content, we need to build a new Hugo project and set up the connection with github pages.

### 2.1 Github setup

A project like this consists of two github repositories. One so called *production repo*, which contains the static files, github pages will then host our site of, and one repository, I will call the `blog` repo from now on, cause mine is named this way. If you're building a portfolio or some other kind of page feel free to use another name. The second repository will contain the actual code and configuration for the site. The `blog` repo will later be linked by a submodule to the production repo, to push changes to the site directly to the live version. Go ahead an create two public repositories with no initial content:

* create code repo and name it as you like
* create production repo and name it `<username>.github.io`

Since we are using a personal github page for our project, the name of the production repo has to be `<github_username>.github.io`. Each account is limited to a single personal page, but each repo to a project can have its own site (the setup process is a little bit different).

Create a project folder for your local files. I put mine directly into my home directory, since I will have to access it a lot in the future and named it `webpage`.

```shell
~ $ mkdir webpage
~ $ cd webpage
```

This folder will contain the local versions of both repositories and will act as the root directory of the project. Here you can create folders for other files, that are project related, but not part or content of the actual site. Im keeping the photoshop files for feature image templates here for instance. Data outside the two cloned repository folders, is not part of any git repository. Let's continue by actually cloning the two repos:

```shell
~/webpage $ git clone https://github.com/<username>/blog.git
~/webpage $ git clone https://github.com/<username>/<username>.github.io.git
```

After cloning the repos we will checkout the `main` branch, add `README.md` and `.gitignore` to both of them and push the changes to origin.

```shell
~/webpage $ cd blog
# Create main branch an switch to it
~//blog $ git checkout -b main
# Create files
~//blog $ touch README.md
~//blog $ touch .gitignore
# Stage and commit changes
~//blog $ git add .
~//blog $ git commit -m 'initial commit'
# Push changes to origin/main
~//blog $ git push origin main
```

Repeat these steps for the production repo and you're good to go for the next step.

### 2.2 Create Hugo project

Let's start building our Hugo project, by changing to the `blog` folder and create a new Hugo project there:

```shell
~/webpage $ cd blog
# Hugo command to build a new project
hugo new site <website-name>
```

The `hugo new site` command did all the heavy lifting for us, by creating a lot of boiler plate code, and the mandatory file structure, in order for hugo to work properly. The project structure should look something like this right now:

```txt
.
└── /webpage
    └── /blog (git repository)
    |   ├── /project
    |   |   ├── /content
    |   |   └── lots of other Hugo files ...
    |   └── .git_files
    ├── /production (git repository) <-- named <username>.github.io
    |   └── .git_files
    └── /resources
```

The names for these folders will be used consistently in this tutorial from now on, since they are the naming conventions my live version follows.

### 2.3 Establish repository connection

The final setup step is to connect the `blog` repository to the `production` repo. In order to do so, we have to create a submodule of `production` inside `blog` and store it inside a folder called `public`.

```shell
~/webpage $ cd blog
# Switch to the directory of the hugo project
~//blog $ cd project
# Create submodule from main branch of repo and clone it to the public folder
~///project $ git submodule add -b main <username>.github.io public
```

Since Hugo will later save the generated static files into the public folder, we now have created a direct link to our live version of the page. Whenever we add or change files in our `blog` repo and update the page with Hugo, we only have to push the changes, made to `webpage/blog/project/public`, to origin, to update the live web-site. We can now continue by establishing our local file system and setting up Hugo.

## 3 Configure Hugo

We now have everything set up correctly and can start building the actual page and filling it with content.

### 3.1 Choosing a theme

Choosing a theme is a key part of the creation process. I wanted a site, where I can easily manage my content and sort it by categories. My goal is to build a resource page for myself, where I can look up things I already learned. By creating these posts I will settle my new knowledge. I found that [uBlogger](https://ublogger.netlify.app) fits the needs I have the most, but there are tons of other themes on the [Hugo Themes](https://themes.gohugo.io) page. If you want to follow along, go with uBlogger, otherwise choose a different theme, but the configuration and content management principles may vary from theme to theme.

For most themes navigate to the themes github repo and copy its link to clone it into your project. It seems to be best practice to submodule the theme rather than simply cloning it. Some themes may have different installing instructions specified in their documentation.

```shell
~//blog $ cd project
~//blog $ git submodule add https://github.com/upagge/uBlogger.git themes/uBlogger
```

This creates a submodule of the desired theme inside our blog repo. If the theme is later updated, we can simply pull changes from the original repository of the theme. In order to apply the theme to the page, change its name and further personalize it, we need to dive into the configuration process.

### 3.2 Configuration

The configuration process is a big part of the page setup and personalization process. I will add further details about the different parts of the config, as I tweak this page. For now a complete example with comments should do it.

{{< details "Example configuration" "..." >}}

```toml
# -----------------------
# PAGE CONFIGURATION FILE
# -----------------------
#
# --------------------
# Global configuration
# --------------------
#
# website title
title = "a coding monkey"
# site description
description = "A personal blog about coding and learning to do so."
# site keywords
keywords = ["personal", "blog", "coding", "swift", "python", "abl3t0nnile"]
# [en, zh-cn, fr, pl, ...] determines default content language
defaultContentLanguage = "en"
# Base URL of the final site
baseURL = "http://abl3t0nnile.github.io"
# theme
theme = "uBlogger"
# whether to use robots.txt
enableRobotsTXT = true
# whether to use git commit log
# This helps to update the last modified data on posts based on the commit history
enableGitInfo = true
# Sets how many posts are shown on a single page
paginate = 10
#
# Author config
# This pulls informatio abou the aouther from data/authors/filename
[author]
  name = "codemonkey"
# Menu config
[menu]
  [[menu.main]]
    identifier = "posts"
    # you can add extra information before the name 
    # (HTML format is supported), such as icons
    pre = ""
    # you can add extra information after the name 
    # (HTML format is supported), such as icons
    post = ""
    name = "Posts"
    url = "/posts/"
    # title will be shown when you hover on this menu link.
    title = ""
    weight = 1
  [[menu.main]]
    identifier = "tags"
    pre = ""
    post = ""
    name = "Tags"
    url = "/tags/"
    title = ""
    weight = 2
  [[menu.main]]
    identifier = "categories"
    pre = ""
    post = ""
    name = "Categories"
    url = "/categories/"
    title = ""
    weight = 3
  [[menu.main]]
    identifier = "about"
    pre = ""
    post = ""
    name = "About"
    url = "/about/"
    title = ""
    weight = 4
# Taxonomies
[taxonomies]
  tag = "tags"
  category = "categories"
# Markup related configuration in Hugo
[markup]
  # Syntax Highlighting 
  # (https://gohugo.io/content-management/syntax-highlighting)
  [markup.highlight]
    codeFences = true
    guessSyntax = true
    lineNos = true
    lineNumbersInTable = true
    noClasses = false
  # Goldmark is from Hugo 0.60 the default library used for Markdown
  [markup.goldmark]
    [markup.goldmark.extensions]
      definitionList = true
      footnote = true
      linkify = true
      strikethrough = true
      table = true
      taskList = true
      typographer = true
    [markup.goldmark.renderer]
      # whether to use HTML tags directly in the document
      unsafe = true
  # Table Of Contents settings
  [markup.tableOfContents]
    startLevel = 2
    endLevel = 6
# Sitemap config
[sitemap]
  changefreq = "weekly"
  filename = "sitemap.xml"
  priority = 0.5

# Permalinks config 
# (https://gohugo.io/content-management/urls/#permalinks)
[Permalinks]
  # posts = ":year/:month/:filename"
  posts = ":filename"
# Options to make output .md files
[mediaTypes]
  [mediaTypes."text/plain"]
    suffixes = ["md"]
# Options to make output .md files
[outputFormats.MarkDown]
  mediaType = "text/plain"
  isPlainText = true
  isHTML = false
# Options to make hugo output files
[outputs]
  home = ["HTML", "RSS", "JSON"]
  page = ["HTML", "MarkDown"]
  section = ["HTML", "RSS"]
  taxonomy = ["HTML", "RSS"]
  taxonomyTerm = ["HTML"]
#
# ----------------------------
# Theme specific configuration
# ----------------------------
#
[params]
  # uBlogger theme version
  version = "2.0.X"
  # site default theme ("light", "dark", "auto")
  defaultTheme = "auto"
  # public git repo url only then enableGitInfo is true
  gitRepo = "https://github.com/abl3t0nnile/blog"
  # date format
  dateFormat = "2006-01-02"
  # Header config
  [params.header]
    # desktop header mode ("fixed", "normal", "auto")
    desktopMode = "fixed"
    # mobile header mode ("fixed", "normal", "auto")
    mobileMode = "auto"
    # Header title config
    [params.header.title]
      # URL of the LOGO
      logo = ""
      # title name
      name = "a Coding Monkey"
      # you can add extra information before the name 
      # (HTML format is supported), such as icons
      pre = ""
      # you can add extra information after the name 
      # (HTML format is supported), such as icons
      post = ""
  # Footer config
  [params.footer]
    enable = true
    # Custom content (HTML format is supported)
    custom = ''
    # whether to show Hugo and theme info
    hugo = true
    # whether to show copyright info
    copyright = true
    # whether to show the author
    author = true
    # site creation time
    since = 2021
    # license info (HTML format is supported)
    license= '<a rel="license external nofollow noopener noreffer" 
              href="https://creativecommons.org/licenses/by-nc/4.0/" 
              target="_blank">CC BY-NC 4.0</a>'
  # Home page config
  [params.home]
    # amount of RSS pages
    rss = 10
    # Home page profile
    [params.home.profile]
      enable = true
      # Gravatar Email for preferred avatar in home page
      gravatarEmail = ""
      # URL of avatar shown in home page
      avatarURL = "/img/avatar.png"
      # title shown in home page (HTML format is supported)
      title = "a Coding Monkey"
      # subtitle shown in home page (HTML format is supported)
      subtitle = "A personal blog about coding and learning to do so."
      # whether to show social links
      social = true
      # disclaimer (HTML format is supported)
      disclaimer = "Written by a monkey in front of a computer ..."
    # Home page posts
    [params.home.posts]
      enable = true
      # special amount of posts in each home posts page
      paginate = 4
    # Social config in home page
  [params.social]
    GitHub = "Abl3t0nnile"
    Email = "minnemann.g@gmail.com"
    RSS = false
  
  
  # Section (all posts) page config
  [params.section]
    # special amount of posts in each section page
    paginate = 20
    # date format (month and day)
    dateFormat = "01-02"
    # amount of RSS pages
    rss = 10
  # List (category or tag) page config
  [params.list]
    # special amount of posts in each list page
    paginate = 20
    # date format (month and day)
    dateFormat = "01-02"
    # amount of RSS pages
    rss = 10
  # Comment config
  [params.comment]
    enable = false
  # Page config
  [params.page]
    theme = "full"
    # whether to hide a page from home page
    hiddenFromHomePage = false
    # whether to hide a page from search results
    hiddenFromSearch = false
    # whether to enable twemoji
    twemoji = false
    # whether to enable the ruby extended syntax
    ruby = true
    # whether to enable the fraction extended syntax
    fraction = true
    # whether to enable the fontawesome extended syntax
    fontawesome = true
    # whether to show link to Raw Markdown content of the content
    linkToMarkdown = true
    # whether to show the full text content in RSS
    rssFullText = false
    # Table of the contents config
    [params.page.toc]
      # whether to enable the table of the contents
      enable = true
      # whether to keep the static table of the contents in front of the post
      keepStatic = false
      # whether to make the table of the contents in the sidebar
      # automatically collapsed
      auto = true
    # Code config
    [params.page.code]
      # whether to show the copy button of the code block
      copy = true
      # the maximum number of lines of displayed code by default
      maxShownLines = 10
    # Social share links in post page
    [params.page.share]
      enable = false
  #Search config
  [params.search]
    enable = true
    # type of search engine ("lunr", "algolia")
    type = "lunr"
    # max index length of the chunked content
    contentLength = 4000
    # placeholder of the search bar
    placeholder = ""
    # uBlogger NEW | 0.2.1 max number of results length
    maxResultLength = 10
    # uBlogger NEW | 0.2.3 snippet length of the result
    snippetLength = 30
    # uBlogger NEW | 0.2.1 HTML tag name of the highlight part in results
    highlightTag = "em"
    # uBlogger NEW | 0.2.4 whether to use the absolute URL based on the
    # baseURL in search index
    absoluteURL = false
```
{{< /details >}}

We can now take a first look on our new page. To test a page in Hugo, simply type `hugo server` into the command line, while in the project directory. Hugo now creates the website and runs it on a local host. The address will be shown in the command line. As long as you keep the server running, hugo will update the site on every change we make to the code. Now we can finally start with personalizing our page.

Although it's empty our page is now complete. All we have to do, is create some content and push the changes to our production repo.

---

## 4 Content management

To be continued ...

## 5 Publication

To be continued ...

## 6 Automation

To be continued ...
