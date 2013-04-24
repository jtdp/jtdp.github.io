---
layout: post
title: "Installing Octopress On Windows 7"
date: 2013-04-23 20:21
comments: true
categories: octopress
---
[Octopress](http://octopress.org) is a pretty sweet blogging framework built on [Jekyll](http://jekyllrb.com/).  It's a nice bit of kit that can easily be set up to create and deploy a blog to Github or your own server / webhost.  I wanted to be able to use it from my Windows 7 laptop, so I googled around and figured out how to get everything set up.  For reference - and in the likely event that I forget how I did it, I'm posting my findings in this - my first Octopress post.  
<!-- more -->

## Git Installation
First up, we need git.  Grab github for windows from [github](https://help.github.com/articles/set-up-git) and run the install.  
I'm keeping my projects in _C:\Users\John\Documents\GitHub_.  Open up a cmd terminal, cd to wherever you set your git projects directory to be, and test that git is working. 
```
cd C:\<path-to-git-projects>
git --version
```

## Yari installation
[Yari](https://github.com/scottmuc/yari) is _Yet Another Ruby Installer_.  Basically, it helps you to install different versions of [Ruby](http://www.ruby-lang.org/) on your system and is very easy to use in a Windows environment.  
Installing Yari is pretty damn easy now we have git installed.  If you aren't there already, cd to your git projects directory and run:
```
cd C:\<path-to-git-projects>
git clone git://github.com/scottmuc/yari.git yari
```  
All you need to do now is add the yari executable to your path.  If you're not sure how to do this, follow the steps below:

 * Left click _Start_, right click _Computer_, left click _Properties_
 * Left click _Advanced system settings_
 * Left click _Environment Variables_
 * In the _System Variables_ list, find _Path_, select it and left click _Edit_
 * Add ```;C:\<path-to-git-projects>\yari\bin\yari``` to the end of it - not forgetting the semi-colon at the beginning and click _Ok_ to close the _Environment Variables_ window.
 * Click _Ok_ on the _Advanced system settings_ window to close that.  You can also close the _System_ window.
 * Close your terminal and reopen it to reload the changed path.  Type  _yari_ to test it is working.

## Ruby installation
Now we have yari, installing Ruby is superfantastically easy.  We're going to install version 1.9.3.  At the command prompt type:
```
yari 1.9.3
```
The first time this is run, it can take a few minutes as it will need to download and install that version of Ruby.  It doesn't give you much feedback while it does, so be patient!  Once done, check it worked with:
```
ruby --version
```

> Note: If you open a new terminal later on today, tomorrow or next week, you need to type yari 1.9.3 again to set the Ruby version for that session.  As it was already installed the first time the command was run, it takes no time at all when run on subsequent occasions.


## Octopress installation
Octopress is hosted on Github, so its just a matter of cloning it and running a few commands to get it rolling.  There's a [set up guide](http://octopress.org/docs/setup/) on the Octopress site which is worth a look if you need any help.
Clone the Repo
```
cd C:\<path-to-git-projects>
git clone git://github.com/imathis/octopress.git octopress
cd octopress
```
### Install Dependencies
```
gem install bundler
bundle install
```
### Set Up Octopress with the Default Theme
```
rake install
```
### Take a Look
At this point you have an empty Octopress blog.  To see what it looks like, we can fire up the built-in development webserver using the following command:
```
rake preview
```
Now, point your browser at [http://localhost:4000](http://localhost:4000) to see what all the fuss is about.


## The World Wide Web
The built-in development server is a super useful tool for developing your blog and previewing content before you publish it, but it ain't going to make you famous.  Fortunately, deploying this baby is a piece of proverbial cake.  I'm using [Github Pages](http://pages.github.com/) for hosting my Octopress blog: it's easy, they have a marginally better server stack than I have and it doesn't me cost a penny.  Again, there's a [guide](http://octopress.org/docs/deploying/github/) on Octopress about how to set this up.

### Get a Github Account
If you don't already have one, sign up [here](https://github.com/)

### Create a Repo
Create a repository to put your blog in.  As per [this page](https://help.github.com/articles/user-organization-and-project-pages), your repository should be named according to the scheme ```username/username.github.io```.  Your blog will be accessible at the url: _http://username.github.io_

### Do the Magic
From your Octopress project directory, run the following command:
```
rake setup_github_pages
```

When asked, enter your the repository url that you just created.  This will be in the form ```git@github.com:username/username.github.io.git```

To publish your blog to Github pages use:
```
rake generate
rake deploy
```

You should then be able to see it at your Github pages url: _http://username.github.io_

> Note: The ```rake generate``` command, takes the source code for the blog and turns it into good old html, css and javascript.  The ```rake deploy command``` fires the generated files up to the master branch of your git repository from where they are published in Git Pages.  

We also want to commit the source files for the blog to the source branch of the repository:
```
git add .
git commit -m 'your message'
git push origin source
```

## Do the Work
So far we've got an empty, uncustomized blog.  Time to make it yours and add some content.
Head over to the Octopress [Basic Configuration](http://octopress.org/docs/configuring) and [Blogging Basics](http://octopress.org/docs/blogging/) pages to get you going.  Just remember, when you've changed content or configuration and want to publish to your Github Pages site, run:
```
rake generate
rake deploy
```

 