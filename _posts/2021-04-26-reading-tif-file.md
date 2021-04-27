---
layout: post
title:  "Reading .tif File"
date:   2021-04-26 00:00:00 +0800
categories: 
tag: Matlab
---
### Mablab Mapping Toolbox&#174; 
Licensed and not free

### imread() and imshow()
```
[value] = imread(tifFile);
cmap = colormap;
imshow(value, 'Colormap', cmap);
```
### readgeoraster()
```angular2html
[A, R, cmap] = readgeoraster(tifFile);
```
mapshow(A, cmap, R) does not work for my case. Need to configure coordinates and map with pcolor()


