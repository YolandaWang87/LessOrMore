---
layout: post
title:  Setting working directory
date:   2021-04-12 00:00:00 +0800
categories: 
tag: Matlab
---

* content
{:toc}


Processing steps		  {#contour}
====================================
1. Making vector of x and y:
   * xv = min(ori_x):max(ori_x);
   <br>
2. Making matrix of X and Y:
   * [X,Y] = ndgrid(xv, yv)
   * Pay attention of order of x/y when the grid is geographic
   <br>
3. Making elevation surface/matrix
   * Z = griddata(xv, yv, zv, X, Y)
   * Tried scatteredInterpolant() and got no better result for one instance
   <br>
4. Mask away land area
   * boundary(x, y, shrink), might not generate the most precise boundary
   * vertex-to-points tool in ArcGIS will generate precise boundary but too many points; might consider to thin


Reference:
<br>
['ls() When invoked with no argument at the top level prompt, ls shows what data sets and functions a user has defined.'](https://www.rdocumentation.org/packages/base/versions/3.6.2/topics/ls)


