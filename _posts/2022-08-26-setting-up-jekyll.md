---
title: "Setting Up Jekyll Chirpy"
date: '2022-08-26'
categories: [blog]
tags: [blog,technical]
published: true
---

# Why Jekyll?

Jekyll offers an easy setup for a website that can be easily customized. Every page can altered, and you are able to (relatively) easily add new features to your website. Pages are written in Markdown, which is easy to learn (little coding needed for a basic webpage.) But because you can use HTML/CSS/JS in the pages (see documentation), any page is capable of complex behaviors and designs.

## Jekyll + Chirpy theme

This site is built with [jekyll-chirpy-theme](https://github.com/cotes2020/jekyll-theme-chirpy). When I was building the site, I ran into several issues. so for anyone wanting to use this theme themselves, here is a step by step guide to deploying the Jekyll + Chirpy theme. 

1) Go to the [chirpy starter]() repository and generate your own repository.

2) Clone the repository onto your own computer

3) If you do not have `Ruby`, `RubyGems`, `Jekyll`, and `Bundler` installed, visit the [Jekyll Docs](https://jekyllrb.com/docs/installation/) site now to install them, as they are required for the next steps.

4) Open the downloaded repository root in a terminal and run:
```console
$ bundle install
``` 
5) As of 01/8/23, this theme did not work at this stage of deployment for me. Some tutorials I have seen did not need to do this step, but I did. I was required to add support for 32 & 64 bit linux.
```console
$ bundle lock --add-platform x86_64-linux
$ bundle
```
6) If you were required to do step 5, then you likely need to do this step. As of 01/8/23, x86_64-linux support and ruby versions >= ruby 3.2. are not compatible. In the file `./.github/workflows/pages-deploy.ymal`, specify the ruby version to be less then 3.2.<br> For me, this is what it looks like. It is apart of the "Setup Ruby" step.
```yaml
42:      - name: Setup Ruby
43:        uses: ruby/setup-ruby@v1
44:        with:
45:          ruby-version: 3.1.3 
46:          bundler-cache: true
```

7) Commit and push your changes, and your site should be up at [gh-username].github.com

8) Unique changes can be made in the `./_config.yaml` file

Changes you should make:
* title
* tagline
* url
* social
* comments

This covers the basic setup of the site. For additional information, follow the instructions that comes with the [theme](https://jekyllrb.com/docs/installation/) or watch [Techno Tim](https://www.youtube.com/watch?v=F8iOU1ci19Q&t=614s) set the site up for himself.

## Bonus : Jekyll Compose

I also recommend [jekyll-compose](https://github.com/jekyll/jekyll-compose) as it simplifies creating new jekyll posts. Follow the instructions at the link to install it on your site.

Here is a generic command I use:
```console
bundle exec jekyll post "[TITLE]" --timestamp-format "%Y-%m-%d"
```



