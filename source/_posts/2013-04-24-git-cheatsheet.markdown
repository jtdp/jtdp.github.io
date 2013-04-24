---
layout: post
title: "Git Cheatsheet"
date: 2013-04-24 00:57
comments: true
categories: [Git, Cheetsheets]
---
Random git snippets to make my life easier.

<!-- more -->

## Adding a submodule to a git repository
{% gist 5443442 %}

## Cloning a git repository with submodules
{% gist 5443429 %}

## Git remove file but keep local copy. 
> Note that when other repository clones pull from the same remote, their local copy of the file will be deleted unless they have modified it.
{% gist 5443305 %}

## Revert file permission changes in local git repository
Very useful when you change permissions due to working on a samba share. Lifted from [Stack Overflow](http://stackoverflow.com/questions/2517339/git-how-to-recover-the-file-permissions-git-thinks-the-file-should-be)
{% gist 5443498 %}

## See changes before pulling from remote git repository
{% gist 5443297 %}

## Change remote url of git repository
{% gist 5443290 %}