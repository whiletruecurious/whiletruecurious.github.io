# WhileTrueCurious

#### Yet Another Technical Blog..


```
<import something-cool-here>
```

This website is built with Jekyll and Mediumish template for Jekyll.

[//]: # ![jekyll template mediumish]({{site.baseurl}}/assets/images/mediumish-jekyll-template.png){: .shadow}

### Features

- Built for Jekyll
- Compatible with Github pages
- Featured Posts
- Index Pagination
- Post Share
- Post Categories
- Prev/Next Link
- Category Archives (this is not yet compatible with github pages though)
- Jumbotron Categories
- Integrations:
    - Disqus Comments
    - Google Analaytics
    - Mailchimp Integration
- Design Features:
    - Bootstrap v4.x
    - Font Awesome
    - Masonry
- Layouts:
    - Default
    - Post
    - Page
    - Archive


## Contribute (TODO!)

- [Clone the repo](https://github.com/whiletruecurious/whiletruecurious).
- Create a branch off of master and give it a meaningful name (e.g. my-new-wtc-post).
- Open a pull request on GitHub and describe the feature or fix.

    
### How to Use

If you aren't familiar with Jekyll yet, you should know that it is a static site generator. It will transform your plain text into static websites and blogs. No more databases, slow loading websites, risk of being hacked...just your content. And not only that, with Jekyll you get free hosting with GitHub Pages! This page itself is free hosted on Github with the help of Jekyll and Mediumish template that you're currently previewing. If you are a beginner we recommend you start with [Jekyll's Docs](https://jekyllrb.com/docs/installation/){:target="_blank"}.


#### Using WhileTrueCurious

Download or Fork *WhileTrueCurious for Jekyll*. 
- In your local project, open <code>_config.yml</code>. If your site is in root, for <code>baseurl</code>, make sure this is set to <code>baseurl: /</code>. Also, change your Google Analytics code, disqus username, authors, Mailchimp list etc.
- WhileTrueCurious requires 2 plugins: 
    - <code>$ gem install jekyll-paginate</code>
    - <code>$ gem install jekyll-archives</code>.
- Edit the menu and footer copyrights in <code>default.html</code>
- Start by adding your .md files in <code>_posts</code>. WhileTrueCurious already has a few as an example. 
- YAML front matter
    - featured post - <code>featured:true</code>
    - exclude featured post from "All stories" loop to avoid duplicated posts - <code>hidden:true</code>
    - post image - <code>image: assets/images/mypic.jpg</code>
    - external post image - <code>image: "https://externalwebsite.com/image4.jpg" </code>
    - page comments - <code>comments:true</code>
    - meta description (optional) - <code>description: "this is my meta description"</code>
    
YAML Post Example:
<pre>
---
layout: post
title:  "WhileTrueCurious sample post"
author: Mukul Dev
categories: [ Jekyll, tutorial ]
image: assets/images/5.jpg
featured: true
---
</pre>

YAML Page Example
<pre>
---
layout: page
title: WhileTrueCurious Template for Jekyll
comments: true
---
</pre>

