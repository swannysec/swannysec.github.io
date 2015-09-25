---
published: true
title: Blog Setup
layout: post
tags: [Blogging, Tools]
---
**On choosing a blogging platform and setting up a no-nonsense blog.**

When I decided to begin this endeavor, I almost decided not to blog the experience.  I don't enjoy narrative writing outside incident reports; it reminds me too much of my B.A. in Political Science.  I'm also not a fan of most blogging platforms.  Finding one that is a balance of ease of use, feature completeness, security (looking at you, Wordpress), and cost effectiveness can be a challenge.

I'm a big fan of clean and simple blogs.  Brian Warehime's [Nullsecure.org](http://nullsecure.org/) is a prime example of what I like in a blog and served in large part as inspiration for this one.  So initially I looked at the platform he chose, [Ghost](https://ghost.org/).  Ghost is quite polished and preaches simplicity.  It also seemed great from a feature standpoint, but as I dug in, it looked like many of the benefits were derived by subscribing as a Pro member, for $8/month.  I'm a public sector employee working in education; needless to say, I don't make a ton of money, so the idea of spending monthly just to host a blog didn't sound appealing.  I'd rather spend what I can on technical resources.  Ghost does allow self-hosting for free, with fewer features, but I decided against that due to added complexity and a clunkier install process.

At that point, I went on the standard blog tour of many of the common names in the business such as Blogger and Wordpress, as well as some newer options like Medium.  Ultimately, I stumbled into [Tinypress](https://tinypress.co).  Tinypress offered dead-simple setup with a few clean themes, easy markdown drafting, and an Android app to boot.  What I didn't realize until I signed up was that it utilized [GitHub Pages](https://pages.github.com/) for hosting and [Jekyll](https://jekyllrb.com/) under the hood.  

The setup process to get to a point where I could begin posting was no more than five minutes.  Unfortunately, I quickly discovered the featureset for Jekyll running on GitHub Pages is somewhat limited due to the small number of GitHub Pages-friendly plugins.  Basic things like social sharing buttons and tags are non-existent.  So what did I do about it?

For social buttons, I initially looked at the buttons provided by the various social networks, but decided against these based on their need for javascript, the tracking inherently built-in to them, and their generally clunky nature.  In the end, I chose the HTML button set provided by the kind folks over at [SimpleShareButtons](https://simplesharebuttons.com/html-share-buttons/).  These were easy to set up, they're simple to add and format, and they do the job nicely without compromising anyone's privacy.  Check them out, they're at the bottom of this post!

Getting tags up and running was a somewhat harrier proposition.  There are loads of posts scattered across the internet regarding tag solutions and GitHub Pages.  If you're running a straight-up Jekyll instance, there are plugins for the purpose.  As you might have guessed, GitHub doesn't support these.  After trying a number of solutions for GitHub-friendly tagging without any success, I found the solution provided by Sungjin Han over at meinside.pe.kr [here](http://blog.meinside.pe.kr/Adding-tag-cloud-and-archives-page-to-Jekyll/).  Again, straightforward and simple to set up with good results, mission accomplished!

My general impression of the Tinypress/GitHub Pages/Jekyll experience is that it's a perfect option for either of two scenarios:

1. You want a dead-simple no-frills blog free of any social integration or advanced features that can be easily edited and set up in minutes.
2. You want a clean, straightforward blog and you're willing to get your hands dirty with HTML, markdown (which is actually kramdown for those curious), and maybe some javascript to add in additional features such as social integration and post categorization that would otherwise be common to most blog platforms.

Overall I'm pleased with the results.  I have a few minor issues to clean up, including a mixed content issue that appears to have been part of the Tinypress template I chose, but otherwise I'm satisfied with what I got for an evening's worth of effort.