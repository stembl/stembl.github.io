---
layout: post
published: true
title: Blog Introduction3
category: blog
tags: goals
---

This blog was built using a lot of different examples which I've tried to detail below.  This is all in windows using:

* [Anaconda](https://www.continuum.io/downloads) for Jupyter
* [GitHub Desktop](https://desktop.github.com/)
* [MarkdownPad 2](http://markdownpad.com/)

All of the files for this blog can be found on [GitHub](http://www.github.com/stembl).

## Goals
I had the following goals in mind while trying to piece together this blog.

* Static blog using GitHub Pages
* Clean and modern looking interface
* Easy to write, edit, and upload posts
* Ability to include Jupyter notebooks easily
* Search-able post tags

## Method

(Under Construction)

A list of the sites, blogs, and github directories that I used to create this site. This is not meant to be an instruction manual for creating a similar blog, but it should get you started.

### Building the Site
* I started with the [GitHub pages](https://pages.github.com/) tutorial.
* The majority of my blog was then forked from [Bruce Eckel's GitHub page](https://github.com/BruceEckel/BruceEckel.github.io) following his tutorial in [Using Github Pages for Blogging](http://bruceeckel.github.io/2014/11/19/using-github-pages/)
	* I needed to install easygui.py to get the newpost.bat program to work.
	* I made a few minor style tweaks I'll try to detail below.
	* I added tag and jupyter functionality.
* I used this post [Build A Blog With Jekyll And GitHub Pages](https://www.smashingmagazine.com/2014/08/build-blog-jekyll-github-pages/)and the fork above to get the site up and running.
* To add Jupyter notebooks I followed the steps on Brian Caffey's post, [Including Jupyter Notebooks in Jekyll blog posts](http://briancaffey.github.io/2016/03/14/ipynb-with-jekyll.html).
	*  I recommend adding the image files to a new folder with the path `/public/img/`.
	*  I need to create a python script to automate the path insertion. [[To-Do]](/todo/)
