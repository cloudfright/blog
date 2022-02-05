---
title: "Hello Hugo - part 1"
date: 2022-02-03T20:19:42Z
draft: true
cover: 

---

![hugo logo](/hugo-how-to/hugo-logo.png)
What better way to start a blog than to talk about how I built it with the help of some great open source software! I won't be going into every detail - this is more of a "here's how I did" it post.

There are many popular blogging platforms out there such as [Wordpress](https://wordpress.com/create/), [Ghost](https://ghost.org/), or [Medium](https://medium.com/). All really easy to use, but I thought it would be fun to create one that was based on a static site generator called [Hugo](https://gohugo.io/). Static sites are great for blogs because although the content is relatively basic, you can still get a lot of functionly e.g. searching, without resorting to a database to store the site content. So in terms of hosting, it's as simple as it gets.

With Hugo, blog posts are created in Markdown and then converted into static HTML, CSS and JavaScript during a build process. The Markdown files are stored in source code repository such as [GitHub](https://github.com/) and when Markdown files are committed and pushed to the repository, an automated process such as [GitHub Actions](https://github.com/features/actions) can automatically create the static content and deploy to your hosting platform of choice.


So let's get started! 

## Installing Hugo

 First we need to to install Hugo, and there's a great getting started guide [here](https://gohugo.io/getting-started/quick-start/). I built this on MacOS and I previously had installed [Homebrew](https://docs.brew.sh/Installation) and had also used that to install [Git](https://git-scm.com/download/mac). I'm using [VSCode](https://code.visualstudio.com/) as my Markdown editor.

To install Hugo, it's as simple as 

```
brew install hugo
```

Next, you can create a new Hugo site with 

```
hugo new site [path] [flags]
```
This command builds the Hugo folder structure and adds the templates and supporting files you'll need to build a static site. 

Now we have Hugo installed and new site created, we need to choose a Hugo theme. There's a gallery and some example sites [here](https://themes.gohugo.io/).

I was looking for something visually minimal and so themes I liked were 
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

Hugo is driven by configuration a [configuration file](https://www.engino.co.uk/content-text/configuration/) in yaml, toml, or JSON format. The configuration file, config.yaml defines gloabl site properites along with menu structure and taxonomies. There's a lot you can do with the configuration, so I'll just cover the basics. 

For my site, I wanted to start with a basic [menu structure](https://gohugo.io/content-management/menus/) so I choose this 

```yaml
menu: 
  main:
    - name: About Me
      url: /about/whoami/
      weight: 1
    - name: Archive
      url: archives/
      weight: 5
    - name: Tags
      url: tags
      weight: 10
    - name: Categories
      url: categories
      weight: 15
  
```

To create a new post use 

```
hugo new posts/newpost.md
```

Where newpost.md is the filename for your post.
To check changes locally as you edit your Markdown use Hugo's live server. 

```
hugo server -D
```
This will start up a local server that you can visit in your browser at http://localhost:1313/ with the -D option allowing you to see [draft](https://gohugo.io/getting-started/usage/) posts.

In part 2, we'll explore how we can host the blog content so that it's publicly accesssible.