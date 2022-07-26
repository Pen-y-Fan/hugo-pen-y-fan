---
title: "Migrating my Hexo blog to Hugo"
date: 2022-07-25T18:52:06+01:00
draft: false
tags: [Hugo, Static site, GitHub, Git, Resource, Go]
url: 2022/07/25/migrating-my-hexo-blog-to-hugo
summary: "This is my first post using Hugo static site generator, following the successful migration of my hexo site to
Hugo"
---

![LUMA Tower](images/clemens-van-lay-UEXRxxaR1DM-unsplash.jpg "LUMA Tower")
Photo
by [Clemens van Lay](https://unsplash.com/@clemensvanlay?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)
on [Unsplash](https://unsplash.com/s/photos/hugo?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText).

This is my first post using [Hugo](https://gohugo.io/getting-started/) static site generator, following the successful
migration of my [hexo site](https://github.com/Pen-y-Fan/hexo-pen-y-fan) to Hugo

## Hexo

My previous static site was powered by [Hexo](https://hexo.io/), I originally started building the site 19 Apr 2020,
using Hexo.io version 4 and published my first blog 30 May 2020. I enjoyed the site for several years, but the site
theme is not maintained. I manually bumped jQuery to 3.5, but was unable to import the theme to v5, let along version 6!

GitHub was warning me about many security problems!

I was not "making the time" to blog, even though I had a lot of ideas, as it felt off-putting.

It was time to look around for an alternative. I wanted:

1. a fast static site generator
2. markdown
3. code syntax highlighting
4. easy to compile
5. light/dark theme
6. I would also like to keep the URL intact, as the original site has high SEO. Original links should still work.

## Hugo

Hugo was top of the recommendation list from [Tech radar](https://www.techradar.com/uk/best/static-site-generators),
looking at the theme and documentation it ticked all the boxes.

I had never used [Go](https://go.dev/) before, but looking at the documentation, once Go is installed
the [Hugo CLI](https://gohugo.io/commands/hugo/) manages the requirements for a dev server, adding a post and building
the site. I therefore don't need to learn any Go. I need to setup Go in my local development environment and add Hugo
executable to run everything.

Challenge accepted!

### Fast static site generator

Hugo ticked that box and is highly recommended, go has a good reputation for fast processing.

### Markdown

Hugo has markdown and other options as standard

### Code syntax highlighting

Yep, although I don't think as good as the theme used in Hexo, it is acceptable.

### Easy to compile

Hugo has three easy to follow CLI commands for, new, serve and build.

This command will create a new post with a title of "My first post"

```shell
hugo new posts/my-first-post.md
```

This command will serve hugo in a developer environment, including draft posts

```shell
hugo server -D
```

The website can be accessed from <localhost:1313>

Deploying is as simple as running the following command

```shell
hugo -D
```

All static assets will be published to the public folder.

### Light/dark theme

I found a nice theme called [Congo](https://github.com/jpanther/congo) built with tailwind css.

### Keep the URL

This took some investigation, but in the end was as simple as adding `url =` to the front matter.

Some of my post have high SEO, for example a search for setting up MySQL on wsl gives a high result. I have no idea how
many people view my blog, as I don't have or want analytics. Seeing a high SEO is good enough for me 😀

## Research

I
watched [Hugo - Static Site Generator | Tutorial](https://youtube.com/playlist?list=PLLAZ4kZ9dFpOnyRlyS-liKL5ReHDcj4G3)
by Mike Dane, which was the same person I watched several years ago which I picked Hexo. I had a good overview of Hugo,
although I am not intending to design my own theme, just consume an existing one.

I also found the documentation for [Hugo](https://gohugo.io/getting-started/)
and [Congo theme](https://jpanther.github.io/congo/docs/) to be very useful.

### Go

Go or Golang is a zip file which I could download and
place [Golang inside Laragon](https://forum.laragon.org/topic/1004/tutorial-how-to-add-golang-to-laragon). Hexo is built
on Go, as a local developer dependency. The site will be static, HTML, CSS and JavaScript.

### Hugo

Hugo is an executable, which can be downloaded and placed in laragon's usr bin folder, which means its executable from
any terminal.

## Local site

Now Go and Hugo are in place I just need to update my Windows PATH, Laragon makes this simple **Menu > Tools > PATH
environment variable > Add Laragon to Path**, log off and back on for this to be available in all terminals.

It didn't take long to read the Congo documentation, chapter by chapter and set up my site as I required.

### Import the markdown

Now I could copy the existing markdown files, configure Hugo to keep the same url. As I had less than 15 posts I
manually added the url to the front matter. If I had much more, I would have considered some form of search and replace.

### Fix images

Next the images needed to be displayed in [Hugo's specific way](https://gohugo.io/content-management/image-processing/),
the posts that had been uploaded to imgur.com automatically displayed, it was the posts that had local images which
needed to be updated.

After a bit of moving files into folder and renaming them index.md, then creating an images folder, the images dropped
in place, my IDE, PhpStorm, handled much of refactoring.

## Deploy

