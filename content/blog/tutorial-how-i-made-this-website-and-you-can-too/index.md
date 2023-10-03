---
title: "Tutorial: How I Made This Website and You Can Too"
tags: [projects, hugo, github pages, tutorials]
date: 2023-01-03
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

draft: false
---

I wanted a simple blog website that was easy to set up and use, and also one where I had ownership and customization: the answer was a **Hugo static site hosted on GitHub Pages**. In this post, I will explain how I set it all up, some challenges I ran into, and how you can set up your own website like this one! 

![Me (illustrated as a duck) working on this website in my dorm.](thumb.jpg "Me (illustrated as a duck) working on this website in my dorm.")

## Table of Contents
1. High Level Overview
2. Downloading and Using Hugo
3. How to Learn Hugo and Use the Docs
4. Pushing to Github and creating a Github Pages Website
5. Bonus: Comments System

## 1. High Level Overview

This website is a **static site**, which means that the user sees the results of the fixed code that I write. Nothing will change unless I change something, so it's like a **brochure**. The benefits of a static site are that they are **simpler to set up and run super fast**; for my blog, I don't need anything more like a dynamic web page where I can add blog posts easily. If you have similar needs, I recommend Hugo to you.

To create the static site, I did not want to spend too much time playing with finicky HTML and CSS, so I opted to use Hugo. Hugo is an open source static site generator, where the user configures setting files and edits Markdown files, and then **Hugo generates the HTML and CSS for you** (you should still have an understanding of HTML and CSS to help debug in case you get stuck). You can read about Hugo here: https://gohugo.io/

{{< alert "circle-info" >}}
Hugo comes with a ton of usable **themes**, some of which are **perfect for blogs**, that help users save even more time. For this website, I used the Congo theme. You can explore themes here: https://themes.gohugo.io/
{{< /alert >}}

There are many places you can host websites online for free, some popular options being Netlify and **GitHub Pages**. For now, I decided to host my website on GitHub Pages, simply because the project was already in a repository on GitHub and you can make unlimited updates to your site. This meant it would be relatively easy to set up and make updates to my site later, such as creating new posts. GitHub pages is also good in that it is secured (HTTPS), which makes users less suspicious of your site.

By creating a repository named `[username].github.io`, you can create **a special GitHub page that doesn't exist on a subpage** (e.g. `[username].github.io/my-blog`). You can view my repository here: https://github.com/probablyalexzhu/probablyalexzhu.github.io

## 2. Downloading and Using Hugo

To use Hugo, you will need to download the **Go** programming language and **Git**. You can download Go at https://go.dev/dl/, and Git at https://git-scm.com/. To learn a little bit how Git works, check out my article: https://probablyalexzhu.github.io/blog/lightning-speed-tutorial-git-and-github/.

To install Hugo, visit https://gohugo.io/installation/windows/ for the information. You will need to use a package manager; personally, Chocolatey did not work, but **Scoop** worked seamlessly.

Once you have Hugo, you will need to create a site using a theme. Every theme has a slightly different setup method and format, but for all of them, you will need to start by creating a Hugo project. This video is really helpful for showing how to create your first Hugo project and teaching you how a Hugo project is structured:

{{< youtube "ZFL09qhKi5I" >}}

Then, follow the instructions in the theme docs to **download a theme**. For example, the Congo theme instructions can be found at https://themes.gohugo.io/themes/congo/. For Congo, it took me **three attempts** to download the theme correctly, so **don't give up**! What worked for me was downloading the config files from GitHub.

Once your theme is set up, simply run the command `hugo server` to create a **local web server** that serves from your computer's memory. This is basically a live preview of your code's changes, which makes it really easy to work on your website. Be careful that some changes won't be reflected, such as the site favicon and blog tags (in my experience).

## 3. How to Learn Hugo and Use the Docs

Hugo is incredibly powerful! Using Markdown and .toml configuration files, it makes it easy to make a good-looking website, with page templates, site-wide configuration, shortcodes, and more.

**90% of using Hugo is using its themes**. Every theme has its own documentation; try to choose a theme with good documentation. For instance, the Congo theme's docs were very complete! https://jpanther.github.io/congo/

Once I had the theme downloaded, I followed the docs in the order provided to configure everything. I was able to easily implement:
- recent posts showing on the home page
- choosing theme colors and a light/dark mode toggle
- header links, footer text, and author bio

just by changing some configuration settings.

Later, when I had my own ideas for improvements, I used the search feature on the Congo docs to find documentation related to my issue. The majority of issues are resolvable through the docs, and the rest can be solved with a quick internet search and by **extending the theme's existing settings**. In the future, I may add a page view counter using tutorials that can be found online.

{{< alert >}}
Make sure you understand your theme! Cross-reference resources for a deeper understanding of what you're actually doing (especially types of pages and folder structures).
{{< /alert >}}

If you do get stuck implementing something, look bigger picture. The error is likely high level, so check that your folder structures make sense and config files that affect the types of pages you're working with. **What you modify can have a lot of unforeseen consequences when it comes to Hugo generating your site.**

## 4. Pushing to Github and creating a GitHub Pages Website

There are a lot of tutorials on YouTube for this, but the simplest and most-straightforward one is by CodeNanshu. The video will show you how to add a .yml file in your Hugo project so that every time you push to GitHub using Git, **GitHub Actions** takes care of updating the site. A file named gh-pages.yml will be put in the folder .github/workflows 

{{< youtube "psyz4UPnGAA" >}}

This is great because after every update you make to your website locally, it only takes **a couple minutes** after a push for your change to be reflected online, and **it's all automated**!

{{< alert "circle-info" >}}
If you want your website to not be a subpage, remember to name your repo `[username].github.io` to create a special GitHub page!
{{< /alert >}}

## 5. Bonus: Commenting System

One of the coolest features to make a static website more alive is a commenting system. There are many options for getting comments on your Hugo website, such as Disqus, Cactus Comments, Commento, and more. Hugo provides a full list here: https://gohugo.io/content-management/comments/.

From my analysis, **Utteranc.es** is the best commenting system, as it runs using GitHub issues, so it is easy to set up, has **no tracking or advertisements** for users, and looks great too with its sleek customization options. The drawback is that website users need a GitHub account to comment, but for the target audience of this website, it shouldn't be an issue 👍.

To set up Utteranc.es comments, go to https://utteranc.es/ and **fill out the details required**. The website will provide a script that you can copy. Put this script in your theme's **layouts/partials/comments.html** file (you may have to create it). It should look like this, but modified:

```HTML
<script src="https://utteranc.es/client.js"
    repo="[ENTER REPO HERE]"
    issue-term="pathname"
    theme="github-light"
    crossorigin="anonymous"
    async>
</script>
```

After that, your blog posts should have comments at the bottom (look down)! I used this blog post by Michelle Scipioni to learn this in case you still have any more questions: https://mscipio.github.io/post/utterances-comment-engine/.

{{< alert "circle-info" >}}
Go with light theme comments if your site has toggleable light/dark mode, because dark comments stick out like a sore thumb on a light mode background.
{{< /alert >}}

## Conclusion

That's basically it for how I made this website and you can too; I hope this was a helpful starting point for you. Once you're set up, it's a ton of fun to customize settings and get to creating content. Hugo and GitHub pages are two great resources for making simple websites, and **I hope you enjoy making your own personal website!**