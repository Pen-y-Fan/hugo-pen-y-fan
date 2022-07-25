---
title: "My first post using Hugo"
date: 2022-07-25T18:52:06+01:00
draft: true
---

This is my first post using [Hugo](https://gohugo.io/getting-started/) static site generator, as a possible replacement
for [hexo-pen-y-fan](https://github.com/Pen-y-Fan/hexo-pen-y-fan)

## Hexo

My previous static site was powered by [Hexo](https://hexo.io/), I originally started building the site 19 Apr 2020,
using Hexo.io version 4 and published my first blog 30 May 2020. I enjoyed the site for several years, but the site
theme is not maintained. I manually bumped jQuery to 3.5, but was unable to import the theme to v5, let along version 6!

GitHub was warning me about many security problems!

It was time to look around for an alternative. I wanted:

1. a fast static site generator
2. markdown
3. code syntax highlighting
4. easy to compile
5. light/dark theme

I would also like to keep the URL intact, as the original site has high SEO. Original links should still work.

## Hugo

Hugo was top of the recommendation list from [Tech radar](https://www.techradar.com/uk/best/static-site-generators),
looking at the theme and documentation it ticked all the boxes.

I had never used [Go](https://go.dev/) before, but looking at the documentation, once Go is installed
the [Hugo CLI](https://gohugo.io/commands/hugo/) manages the requirements for a dev server, adding a post and building
the site. I therefore don't need to learn any Go. I need to setup Go in my local development environment and add Hugo
executable to run everything.  

Challenge accepted!
