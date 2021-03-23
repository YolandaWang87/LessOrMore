---
layout: post
title:  Setting working directory
date:   2021-03-23 00:00:00 +0800
categories: 
tag: R
---

* content
{:toc}


Method List			{#env}
====================================
rm(list=ls())
<br>
getwd()
1. Using functions:
   * **setwd**(desiredDir), or
   * fileHandle <- **file.path**(desiredDir, fileName)
2. Using buttons:
   * open a file, and in the Session menu, use the *Set Working Directory - To Source File Location* command
   * in the Files tab, navigate to a directory, and *Set As Working Directory* in the 'More' dropdown list


Reference:
<br>
['ls() When invoked with no argument at the top level prompt, ls shows what data sets and functions a user has defined.'](https://www.rdocumentation.org/packages/base/versions/3.6.2/topics/ls)


