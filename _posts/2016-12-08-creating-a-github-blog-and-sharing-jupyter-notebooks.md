---
layout: post
published: true
title: Creating a GitHub Blog and Sharing Jupyter Notebooks
category: blog
tags: [howto]
---

This blog was hacked together using a lot of different examples which I've attempted to detail below.  This was built with a  Windows machine using:

* [Anaconda](https://www.continuum.io/downloads)
* [GitHub Desktop](https://desktop.github.com/)
* [MarkdownPad 2](http://markdownpad.com/)

All of the files for this blog can be found on my [GitHub](http://www.github.com/stembl).

## Goals
I had the following goals in mind while trying to piece together this blog.

* Static blog using GitHub Pages
* Clean and modern looking interface
* Easy to write, edit, and upload posts
* Ability to include Jupyter notebooks easily
* Search-able post tags

## Method
A list of the sites, blogs, and github directories that I used to create this site. This is not meant to be an instruction manual for creating a similar blog, but it should get you started.

### Getting Started
* I started with the [GitHub pages](https://pages.github.com/) tutorial.
* The majority of my blog was then forked from [Bruce Eckel's GitHub page](https://github.com/BruceEckel/BruceEckel.github.io) following his tutorial in [Using Github Pages for Blogging](http://bruceeckel.github.io/2014/11/19/using-github-pages/)
	* I needed to install [easygui.py](http://easygui.sourceforge.net/sourceforge_site_as_of_2014_11_21/download/version_0.96/index.html#installingEasyguiOnWindows) to get the newpost.bat program to work. 
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
	* I need to modify the newpost.bat to include tags and categories. [[To-Do]](/todo/)
	* I would like to add icons for categories, tags, email, linked, and github. [[To-Do]](/todo/)


### Tips and Tricks
* The theme can be modified by changing the body class in the `default.html`. Available themes and other options can be found on the [Lanyon GitHub page](https://github.com/poole/lanyon).
* I modified my sidebar to use a table for the links at the top as opposed to the original simple list.  This let me keep them centered.
	* I needed to pull the theme background color from the index and input it into the `<td>` field to overwrite the existing table highlighting.  This breaks the ability to add a hover feature to `<td>`.
* I referenced [this site](http://www.w3schools.com/css/css_table.asp) often when tweaking my tables in the sidebar.
* I used Powerpoint to create my simple favicon (website icon).  Then I used the online [Favicon & App Icon Generator](http://www.favicon-generator.org/) and [Favicon Generator. For real.](http://realfavicongenerator.net/). The first generator creates more icons and the second gives you more control over how the icons will look on mobile devices. Both sites was simple and easy to use. Take these images and extract them to your `/public/icon/` path.  Update your `head.html` file to include the icon locations as detailed by the generator sites.  Make sure to update the generic locations with `public/icon`.  Open `public/icon/manifest.json` and add you name as it should be displayed on a mobile device, `"name": "Site Name Here"`. Finally, add the `browserconfig.xml` to the root directory. It took a while for the old favicon to be replaced by the new one, try checking with a different web browser or clearing your cache.
* For troubleshooting elements of the blog, I would make small changes and commit them.  Then I would open the website in incognito mode to prevent my browser from storing any of the data.  This allowed me to check features pretty quickly.
	* Be careful when modifying the header of posts. Adding returns seems to break the post.
* I ran into a lot of problems trying to display the HTML code within this post. Many of the methods I tried ended up breaking the post causing it to not display. I would then receive an email from GitHub with "The value 'nil' was passed to a date-related filter that expects valid dates...".  The solution I used was to submit [Gists](https://gist.github.com/) and embed the generated `<script src=...` code.
* To make the code look nice and add some style to the Tag and Category pages I used `<code class="highlighter-rouge">...</code>`. Adding the code block inside `<a href>...</a>`  results in a different color than adding it to the outside.  I used this to differentiate between the tags and the dates.
* I thought it would be fun to convert my [resume](/resume) to markdown and included it in the sidebar. I used the example detailed in blm.io's [Building an academic CV in markdown](http://blm.io/blog/markdown-academic-cv/).
* A reference I have up constantly is daringfireball.net's [Markdown: Syntax](https://daringfireball.net/projects/markdown/syntax/).
* A tool that generates color pallets at [ColorHexa](http://colorhexa.com).


	