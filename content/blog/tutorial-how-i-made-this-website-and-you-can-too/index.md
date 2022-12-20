---
title: "Tutorial: How I Made This Website and You Can Too"
tags: [projects, hugo, github pages, tutorials]
date: 2022-12-08
showDate: true
showWordCount: true
showReadingTime: true

# summary: "Hi! My name is Alex Zhu."
showSummary: true
showAuthor: true
showTableOfContents: false
showComments: true
showPagination: true
invertPagination: true
showTaxonomies: true

draft: true
---

I wanted a simple blog website that was easy to set up and use, and also one where I had ownership and customization: the answer was a Hugo generated static site hosted on GitHub Pages. In this post, I will explain how I set it all up, some challenges I ran into, and how you can set up your own website like this one! 

![Me (illustrated as a duck) working on this website in my dorm.](thumb.jpg "Me (illustrated as a duck) working on this website in my dorm.")

## Table of Contents
1. High Level Overview
2. Downloading and Using Hugo
3. How to Learn Hugo and Use the Docs. Lots of things u can set up, remember to crossreference resources and understand your theme
4. Pushing to Github and creating a Github Pages Website (including .yml file, Github Actions for every automated updates)
5. Bonus: Comments System (link to other article)

## High Level Overview

This website is a static site, which means that the user sees the results of the fixed code that I write. Nothing will change unless I change something, so it's like a brochure. The benefits of a static site are that they are simpler to set up and run super fast; for my blog, I don't need anything more like a dynamic web page.

To create the static site, I did not want to spend too much time playing with finicky HTML and CSS, so I opted to use Hugo. Hugo is an open source static site generator, where the user configures setting files and edits Markdown files, and then Hugo generates the HTML and CSS for you. You can read about Hugo here: https://gohugo.io/

Hugo comes with a ton of usable themes, some of which are perfect for blogs, that help users save even more time. For this website, I used the Congo theme. You can explore themes here: https://themes.gohugo.io/

There are many places you can host websites online for free, one of the most popular being GitHub pages. For now, I decided to host my website on GitHub pages, simply because the project was already in a repository on GitHub. This meant it would be relatively easy to set up and make updates to my site later, such as creating new posts. GitHub pages is also good in that it is secured (HTTPS), which makes users less suspicious of your site. By creating a repository named `[username].github.io`, you can create a special GitHub page that doesn't exist on a subpage (e.g. `[username].github.io/my-blog`). You can view my repository here: https://github.com/probablyalexzhu/probablyalexzhu.github.io

## Downloading and Using Hugo
(with emphasis on setup, link to useful tutorial). It took me 3 tries so don't give up