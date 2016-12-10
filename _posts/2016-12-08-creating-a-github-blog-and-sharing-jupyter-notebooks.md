---
layout: post
published: true
title: Creating a GitHub Blog and Sharing Jupyter Notebooks
category: blog
tags: [howto, todo]
---

This blog was built using a lot of different examples which I've tried to detail below.  This is all in Windows using:

* [Anaconda](https://www.continuum.io/downloads)
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
A list of the sites, blogs, and github directories that I used to create this site. This is not meant to be an instruction manual for creating a similar blog, but it should get you started.

### Building the Site
* I started with the [GitHub pages](https://pages.github.com/) tutorial.
* The majority of my blog was then forked from [Bruce Eckel's GitHub page](https://github.com/BruceEckel/BruceEckel.github.io) following his tutorial in [Using Github Pages for Blogging](http://bruceeckel.github.io/2014/11/19/using-github-pages/)
	* I needed to install easygui.py to get the newpost.bat program to work.
	* I made a few minor style tweaks I'll try to detail below.
	* I added tag and jupyter functionality.
* I used this post [Build A Blog With Jekyll And GitHub Pages](https://www.smashingmagazine.com/2014/08/build-blog-jekyll-github-pages/) and the fork above to get the site up and running.
* To add Jupyter notebooks I followed the steps on Brian Caffey's post, [Including Jupyter Notebooks in Jekyll blog posts](http://briancaffey.github.io/2016/03/14/ipynb-with-jekyll.html).
	*  I recommend adding the image files to a new folder with the path `/public/img/`.
	*  I need to create a python script to automate the path insertion. [[To-Do]](/todo/)
*  Finally, I wanted my posts to be organized with tags.  I used the method detailed in [Use Tags and Categories in your Jekyll based Github Pages without plugins]( https://codinfox.github.io/dev/2015/03/06/use-tags-and-categories-in-your-jekyll-based-github-pages/).
	*  This required a bit of tweaking to make it work with the basic site. I added the category.html and tag.html to the base folder with index.html.
	*  I changed the title of each to Categories and Tags and layout to default for both.
	*  I added Tags and Categories to the header.
	*  <script src="https://gist.github.com/stembl/2cec025eaf3739508bbbd44b67e05250.js"></script>
	* For the links on the Category and Tag pages, I needed to use `<code>` instead of `<small>`.
	* <script src="https://gist.github.com/stembl/b3e10eb14fbaf0429a4b831889ec6c48.js"></script>
	* Finally, I commented out the header used in the index to minimize clutter on the front page.


### Tips and Tricks
* The theme can be modified by changing the body class in the `default.html`. Available themes and other options can be found on the [Lanyon GitHub page](https://github.com/poole/lanyon).
* I modified my sidebar to use a table for the links at the top as opposed to the original simple list.  This let me keep them centered.
	* I needed to pull the theme background color from the index and input it into the `<td>` field to overwrite the existing table highlighting.  This breaks the ability to add a hover feature to `<td>`.
* I referenced [this site](http://www.w3schools.com/css/css_table.asp) often when tweaking my tables in the sidebar.
* I used Powerpoint to create my simple favicon (website icon).  Then I used the online [Favicon & App Icon Generator](http://www.favicon-generator.org/). This site was simple and easy to use.  I did notice that the icon did not work on my Android phone and I need to investigate the cause. [[To-Do]](/todo/) Take these images and extract them to your `/public/` path.  It took a while for the old favicon to be replaced by the new one. Consider checking with a different web browser.
* For troubleshooting elements of the blog, I would make small changes and commit them.  Then I would open the website in incognito mode to prevent my browser from storing any of the data.  This allowed me to check features pretty quickly.
	* Be careful when modifying the header of posts. Adding returns seems to break the post.
* I ran into a lot of problems trying to display the HTML code within this post. Many of the methods I tried ended up breaking the post causing it to not display. I would then receive an email from GitHub with "The value 'nil' was passed to a date-related filter that expects valid dates...".  The solution I used was to submit [Gists](https://gist.github.com/) and embed the generated `<script src=...` code.
* To make the code look nice and add some style to the Tag and Category pages I used `<code class="highlighter-rouge">...</code>`
	