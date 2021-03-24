---
layout: post
title:  Frequently used git commands
date:   2021-03-24 00:00:00 +0800
categories: 
tag: Git
---

First, create ssh key and copy public key to Github
<hr>
### Clone repository to local
```
rm -rf prevGitDir
git clone repositoryPathUsingSSH
```
### Upon new modification
```
git commit -am 'message'
git push
```
### Change to another remote branch
```
git fetch
git checkout newBranch
```
### Regular check
```angular2html
git status
git branch
```


