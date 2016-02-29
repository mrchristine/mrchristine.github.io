---
layout: post
title: Getting Started with GitHub Pages
---


I've been trying to start a blog for a while now, but constantly postpone it due to procrastination. I've finally put my own foot down and will document the process to get started. This technology is new-ish to me so I hope that what I learn can help others get started as well. 

I started a simple [GitHub Pages](https://pages.github.com/) example and noticed that it was a very simple way to get started. I contemplated using WordPress, but GitHub is more of a natural fit for me since I use Git at work. 

I noticed that there were a lot of themes that you can install in this platform, and tried to research a few different ones. GitHub provides a few standard templates to get installed quickly. They have a workflow that copies the template into your repository to get you up and running fast.  

I decided to go a different route and wanted something with a minimalistic look. I found the [poole/lanyon](https://github.com/poole/lanyon) theme and thought it fit my aesthetic. 

I deleted my repo to start fresh. I forked a copy of the [lanyon](https://github.com/poole/lanyon) repository. 

~~~bash
git clone https://github.com/git-username/git-username.github.io
git clone https://github.com/poole/lanyon.git
cd lanyon
cp -R * ../git-username.github.io
cd !$
git add -all
git commit -a -m "Initial commit to install lanyon theme"
git push
~~~

The blog **should** now have a working example. 
I found the docs to be a bit outdated, and the latest version of jekyll (v3.1.1) doesn't support relative_permalinks any longer. Removing the following `relative_permalinks: true` from the `_config.yml` configuration file fixed this issue.  
It was interesting to see that GitHub does send a notification e-mail to explain the issue. Users can also go to the "Settings" tab of their repo to see if there are any issues publishing the repo. This helped me understand the root cause of the issue. 

A few tips I found useful while debugging the syntax and features of GitHub Pages. 

* They use [kramdown](http://kramdown.gettalong.org/syntax.html) as the markdown parsing library. Use the documentation to understand proper syntax for code blocks, and code syntax highlighting. 
* To start a local server to test and review the posts, you can run the following:  
  * You can change files, and the server will notice the changes and deploy it to the localhost server automatically.   

~~~
	$ jekyll serve
~~~

* To look for specific text within the repo, you can use `git grep` to find the files with the reference text. 
* Do **_not_** add '/' as the `baseurl:` config parameter in _config.yml. This breaks the theme without any explicit error. I read a users blog post that stated that it was necessary, but it didn't work for me. 
