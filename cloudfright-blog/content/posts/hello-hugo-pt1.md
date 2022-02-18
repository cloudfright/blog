---
title: "Hello Hugo - part 1"
date: 2022-02-03T20:19:42Z
draft: false

summary: "What better way to start a blog than to talk about how I built it with the help of some great open source software!"
cover: 
    image: /hugo-how-to/hugo-logo.png
    alt: "hugo logo"

categories: ["coding"]
tags: ["hugo"]
series: ["Building a Hugo blog"]

params:
    ShowShareButtons: true
    ShowReadingTime: true

---

There are many popular blogging platforms out there such as [Wordpress](https://wordpress.com/create/), [Ghost](https://ghost.org/), or [Medium](https://medium.com/). They're all really easy to use and don't require any technical knowledge, but I thought it would be fun to create a blog that was based on a static site generator called [Hugo](https://gohugo.io/). Static sites are great for blogs because although the content is relatively basic, you still get a lot of functionality without needing a database to store the site content. They are also lightening fast to render. And in terms of hosting, it's as simple as it gets. 

Using Hugo, blog posts are created in [Markdown](https://www.markdownguide.org/) and then converted into static HTML, CSS and JavaScript during a build process. The Markdown files are stored in source code repository such as [GitHub](https://github.com/) and when the Markdown files are committed and pushed to the repository, an automated process such as [GitHub Actions](https://github.com/features/actions) can build the static content and deploy to your hosting platform of choice. 


So let's get started! 

## Installing Hugo

 First we need to to install Hugo, and there's a great getting started guide [here](https://gohugo.io/getting-started/quick-start/). I built this on MacOS and had previously installed a package manager called [Homebrew](https://docs.brew.sh/Installation). I'd  also used Homebrew to install [Git](https://git-scm.com/download/mac). I'm using [VSCode](https://code.visualstudio.com/) as my Markdown editor.

To install Hugo, it's as simple as 

```
brew install hugo
```

Next, you can create a new Hugo site with: 

```
hugo new site <name of site> -f yml
```

This command builds the Hugo folder structure and adds the templates and supporting files you'll need to build a static site. The ```hugo new``` command takes various [flags](https://gohugo.io/commands/hugo_new/).

Now we have Hugo installed and a new site created, we need to choose a Hugo theme. There's plenty to choose from the [gallery](https://themes.gohugo.io/) and sample sites.

I was looking for something visually minimal and so themes I liked were:
- [Github Style](https://themes.gohugo.io/themes/github-style/)
- [Bootstrap](https://themes.gohugo.io/themes/minimal-bootstrap-hugo-theme/) 
- [Pixyll](https://themes.gohugo.io/themes/hugo-theme-pixyll/)
- [Hyde](https://themes.gohugo.io/themes/hyde/) 
- [PaperMod](https://themes.gohugo.io/themes/hugo-papermod/)


I opted for PaperMod. There are a [couple of different ways](https://adityatelange.github.io/hugo-PaperMod/posts/papermod/papermod-installation/) to install a theme and I chose the git submodules approach. 

```
git submodule add https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod --depth=1
git submodule update --init --recursive 
```
The advantage of using git submodules is that you can easily keep the theme up to date when new changes are released. 

## Configuration

Hugo is driven by a [configuration file](https://www.engino.co.uk/content-text/configuration/) in yaml, toml, or JSON format. The configuration file defines global site properties along with menu structures and taxonomies. 

The [menu structure](https://gohugo.io/content-management/menus/) for the site is defined within the config file. For the blog, I wanted to something like this:

![menu structure](/hugo-how-to/blog-menu.jpg)

And the corresponding yaml config is:

```yaml
menu: 
  main:
    - name: Search
      url: /search/
      weight: 1
    - name: Categories
      url: /categories/
      weight: 5
    - name: Tags
      url: /tags/
      weight: 10
    - name: Series
      url: /series/
      weight: 15
    - name: Archive
      url: archives/
      weight: 20
    - name: About Me
      url: /about/whoami/
      weight: 25
  
```

The weight provides the ordering from left to right.
The **Tags**, **Categories** and **Series** taxonomies are baked in and work out of the box.
 To get the search functionality working, we just need to make a few small modifications.

 Add this to ```config.yml```
 ```
 outputs:
    home:
        - HTML
        - RSS
        - JSON # is necessary

 ```
Create search.md in the content folder with the front matter:

```
---
title: "Search" # in any language you want
layout: "search" # is necessary
# url: "/archive"
# description: "Description for Search"
summary: "search"
---
```

To enable archives, create archives.md in the content folder and add this front matter:

```
---
title: "Archive"
layout: "archives"
url: "/archives/"
summary: archives
---
```

## Writing a post

Now with our menu defined, let's create a first post using:

```
hugo new posts/hello-hugo-pt1.md
```

This is place the file in the content folder with the path you've provided.

Each post has a [front matter](https://gohugo.io/content-management/front-matter/) - a collection of configuration variables and metadata. 

When a new post is created, the front matter is initialised from a template in /archetypes/default.md which looks like this: 

```
---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
draft: true
---

```

You can customise this file to include other metadata you wish to initialise by default.

I've added some additional variables to this page.

```
---
title: "Hello Hugo - part 1"
date: 2022-02-03T20:19:42Z
draft: true
summary: "What better way to start a blog than to talk about how I built it with the help of some great open source software! "
cover: 
    image: /hugo-how-to/hugo-logo.png
    alt: "hugo logo"

categories: ["coding"]
tags: ["hugo"]
series: ["Building a Hugo blog"]

params:
    ShowShareButtons: true
    ShowReadingTime: true

---
```
You can find the variables specific to PaperMod [here](https://adityatelange.github.io/hugo-PaperMod/posts/papermod/papermod-variables/).


To check changes locally as you edit your Markdown, use Hugo's  server:

```
hugo server -D
```
This will start up a local server. Just open ```http://localhost:1313/``` in your browser. The -D option allows you to see [draft](https://gohugo.io/getting-started/usage/) posts.

Every time you save your Markdown files, the preview will automatically refresh. 

## Summary

That's all for part 1. We've installed hugo, added some basic configuration, created a first post and seen how we can use ```hugo server``` to build and preview the site locally.

You can find the github repository for this blog [here](https://github.com/cloudfright/blog).

In part 2, we'll explore some hosting options to make the blog content publicly accessible.