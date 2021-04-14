---
layout: post
title:  Elevation vector to contour matrice
date:   2021-04-12 00:00:00 +0800
categories: 
tag: [Matlab, ArcGIS]
---

### Processing steps		  {#contour}
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
   <br>
5. Contour plot
   * [C,h]=contour(X,Y,levels)
   * clabel(C, h, property-pair)
   * might need to use m_map function


Reference: ['Contour plot using three vectors'](https://www.mathworks.com/matlabcentral/answers/490616-contour-plot-using-three-vectors)


