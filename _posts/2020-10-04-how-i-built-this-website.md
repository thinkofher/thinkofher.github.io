---
title: "How I built this website"
subtitle: "TLDR: jekyll + w3.css + github pages"
author: thinkofher
website: "https://github.com/thinkofher"
tags: web github html css
layout: post
---

It's simple, responsive and easy in maintenance. Also it's free! As a bear and as a speech (you can check source code through navigation bar). You don't have to own server if you want to have the website like this and you can plug in your own domain. And yes: you've got ssl out of the box.

That's what we call "static website". It is built from plaint text files and portion of html flavoured with some fancy processing language for some static data, that you can use to generate more html. But hey, let assume that you want to build website like this from scratch. Where should you start?

### Github

You have to own at least one Github account. Everything starting from this point is so easy and accessible thanks to folks from Github. Huge respect! Let's create account, if you don't have one, and initialize new repository with name fulfills following pattern: `${username}.github.io`. Now add some `index.html` file to the root directory of the project. Commit, push and reach your brand new webpage through web browser with the same url as the repository name. That's pretty much it. Now you have your own website. Your own place in the web, where you can share you thoughts and whatever you'd like to with the rest of the world. It's called [Github Pages](https://pages.github.com/) and it's really awesome. It's very common for open source projects to use that feature for documentation hosting.


### Jekyll

The thing that process data, posts and generates web pages from templates is called [jekyll](https://jekyllrb.com/). It's static site generator, probably the most popular one. I highly recommend you to install it on your machine and use it for prototyping your website. I am using `Fedora` machine as daily driver so all what I had to do was:

    $ sudo dnf install jekyll
    $ jekyll serve --livereload

in the root of the repository. I strongly believe that it's very easy to install it on other `Linux` distributions or `OS X`.

If you aren't familiar with template engines (like jinja2 or DTL) for HTML files, you should start with writing plain HTML and then extend them with [layouts](https://jekyllrb.com/docs/layouts/) whenever some pattern occurs. You may also use [includes](https://jekyllrb.com/docs/includes/) for things like navigation bar or footer (that's what I am using includes for). What I am describing now are just my suggestions as whole system is very flexible and you can use it as you like. If you still are not feeling confident with the whole idea, just follow the [tutorial](https://jekyllrb.com/docs/step-by-step/01-setup/) and take a look at the `jekyll` [documentation](https://jekyllrb.com/docs/).

### W3.CSS

Unfortunately I'm not the best web designer. I like tweaking JavaScript, I also enjoy working with HTML and different text templating engines. But I was always struggling with writing CSS. I never enjoyed it. I am aware that you can accomplish great things with it and I wish that one day I won't fall asleep when forcing myself to write CSS, but today I'm afraid my websites will continue to look... ugly.

But hey, I am programmer. I can try to make my websites look little less uglier with the help of existing style sheets, that people smarter than me crated to reuse.

There are a lot of CSS frameworks out there. It's hard to choose one. We have also classless style sheets for very minimalistic sites. And there is [W3.CSS](https://www.w3schools.com/w3css/).

Seriously. Why it isn't popular? It's minimalistic, lightweight and responsive CSS framework inspired by material design, without any JavaScript dependencies. It's also free to use without any license. It's well documented with many functional examples that you can use in your website and great looking templates for starting your work from a little higher level.

It really caught my attention and I will recommend it to everyone that need something small for building your site from scratch without need to write a lot of boilerplate CSS.
