---
layout: post
title:  Mapping georeferenced photo points
date:   2021-04-16 00:00:00 +0800
categories: [GIS, Cartography]
tag: [ArcGIS, Python]
---

* content
{:toc}
  
### Result and Flow    {#flow}
![Flow Chart]({{ '/styles/images/20210416_01.png' | prepend: site.baseurl  }})
<sub>*This map is produced as a portion of the requirements of the Advanced GIS Program at the Centre of Geographic Sciences, NSCC, Lawrencetown, Nova Scotia. This product is unedited, unverified, and intended for educational purposes only. &copy;2020 COGS</sub>
<br>
<sub>**Scheme of map layout is from John Nelson ['How to Create a Global Map of Nautical Piracy'](How to Create a Global Map of Nautical Piracy)</sub>

### Cartography and Geoprocessing
<b>Cartography</b>
<br>
* Equal earth projection and modification
* Creating vignette with a single polygon
* Importing web-sourced ArcGIS Pro symbol style
* Graduated symbols on size and other tessellation style
* Stacking layers firefly symbols for stereo effect
<br>
<b>Geoprocessing</b>
* Generating tessellation and masking 
* Spatial join the tessellation with point data
