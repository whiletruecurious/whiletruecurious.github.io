---
layout: post
title:  "Creating a new static website with Jekyll"
author: dev
categories: [Jekyll, website, static-website-generator, static-website, tech]
image: assets/images/13.jpg
featured: false
hidden: false
---

No more databases, comment moderation, or pesky updates to install-just your content. Markdown, Liquid, HTML & CSS go in. Static sites come out ready for deployment. Permalinks, categories, pages, posts, and custom layouts are all first-class citizens here.

Sick of dealing with hosting companies? GitHub Pages are powered by Jekyll, so you can easily deploy your site using GitHub for free-custom domain name and all.

## What is Jekyll?

tl;dr: Jekyll is a simple, blog-aware, static site generator.  

If you aren't familiar with Jekyll yet, you should know that it is a static site generator. It will transform your plain text into static websites and blogs. No more databases, slow loading websites, risk of being hacked...just your content. And not only that, with Jekyll you get free hosting with GitHub Pages! This page itself is free hosted on Github with the help of Jekyll and Mediumish template that you're currently previewing. If you are a beginner we recommend you start with [Jekyll's Docs](https://jekyllrb.com/docs/installation/){:target="_blank"}.


You create your content as text files (Markdown), and organize them into folders. Then, you build the shell of your site using Liquid-enhanced HTML templates. Jekyll automatically stitches the content and templates together, generating a website made entirely of static assets, suitable for uploading to any server.

Jekyll happens to be the engine behind GitHub Pages, so you can host your project’s Jekyll page/blog/website on GitHub’s servers for free.

## Quick Start Guide


If you already have a full Ruby development environment with all headers and RubyGems installed (see Jekyll’s requirements), you can create a new Jekyll site by doing the following:

```ruby
# Install Jekyll and Bundler gems through RubyGems
gem install jekyll bundler

# Create a new Jekyll site at ./myblog
jekyll new myblog

# Change into your new directory
cd myblog

# Build the site on the preview server
bundle exec jekyll serve

# Now browse to http://localhost:4000
```

`jekyll new <PATH>` installs a new Jekyll site at the path specified (relative to current directory). In this case, Jekyll will be installed in a directory called `myblog`. Here are some additional details:

- To install the Jekyll site into the directory you're currently in, run `jekyll new` . If the existing directory isn't empty, you can pass the --force option with jekyll new . --force.
- `jekyll new` automatically initiates `bundle install` to install the dependencies required. (If you don't want Bundler to install the gems, use `jekyll new myblog --skip-bundle`.)
- By default, the Jekyll site installed by `jekyll new` uses a gem-based theme called Minima. With gem-based themes, some of the directories and files are stored in the theme-gem, hidden from your immediate view.
- We recommend setting up Jekyll with a gem-based theme but if you want to start with a blank slate, use `jekyll new myblog --blank`
- To learn about other parameters you can include with `jekyll new`, type `jekyll new --help`.

## About Bundler

`gem install bundler` installs the bundler gem through RubyGems. You only need to install it once - not every time you create a new Jekyll project. Here are some additional details:

`bundler` is a gem that manages other Ruby gems. It makes sure your gems and gem versions are compatible, and that you have all necessary dependencies each gem requires.

The `Gemfile` and `Gemfile.lock` files inform `Bundler` about the gem requirements in your site. If your site doesn’t have these Gemfiles, you can omit `bundle exec` and just `run jekyll serve`.

When you run `bundle exec jekyll serve`, `Bundler` uses the gems and versions as specified in `Gemfile.lock` to ensure your Jekyll site builds with no compatibility or dependency conflicts.

For more information about how to use `Bundler` in your Jekyll project, this tutorial should provide answers to the most common questions and explain how to get up and running quickly.
