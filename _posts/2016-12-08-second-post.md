---
layout: post
published: true
title: Creating a GitHub Blog and Sharing Jupyter Notebooks
category: blog
tags: howto

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
*  Finally, I wanted my posts to be organized with tags.  I used the method detailed in [Use Tags and Categories in your Jekyll based Github Pages without plugins]( https://codinfox.github.io/dev/2015/03/06/use-tags-and-categories-in-your-jekyll-based-github-pages/).
	*  This required a bit of tweaking to make it work with the basic site. I added the category.html and tag.html to the base folder with index.html.
	*  I changed the title of each to Categories and Tags and layout to default for both.
	*  I added Tags and Categories to the header.   This example is from the categories.html.

	<h1 class="page-title"><a href="/">Blog</a> | <a href="/tag/">Tags</a> | {{ page.title }}
	</h1>

	* For the links on the Category and Tag pages, I needed to use <code> instead of <small>.  This example is from the categories.html.'
	
	<li>
    <h3>
      <a href="{{ post.url }}">
        {{ post.title }}</a>
        &nbsp;<code class="highlighter-rouge">{{ post.date | date_to_string }}</code>
      
	  <!-- adds tags to the end of posts
	  {% for tag in post.tags %}
      <a class="codinfox-tag-mark" href="/blog/tag/#{{ tag | slugify }}">{{ tag }}</a>
      {% endfor %}-->

    </h3>
	</li>

	* Finally, I commented out the header used in the index to minimize clutter on the front page.