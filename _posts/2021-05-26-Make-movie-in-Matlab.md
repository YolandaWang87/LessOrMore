---
layout: post
title:  "Make Movie in Matlab"
date:   2021-05-20 00:00:00 +0800
categories: 
tag: Matlab
---
1. Collect Images by imread() into One Variable
Licensed and not free
```angular2html
images = cell(numImg,1);
```
2. Create Video Object
```
vObj = VideoWriter(vName);
vObj.FrameRate = fpsNum
```
fpsNum means how many frames per second.
3. Open Video Object and Write in Images
```angular2html
open(vObj);
for ki = 1:length(images)
    ki_frame = images(ki)
    writeVideo(vObj, ki_frame)
end
clear ki;
close(vObj);
```
4. Play Result with Matlab Video Player
```angular2html
implay(vName);
```
Reference: ['Create a movie from images'](https://www.mathworks.com/matlabcentral/answers/271490-create-a-movie-from-images)
