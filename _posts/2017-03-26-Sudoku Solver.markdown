---
layout: post
title:  "Sudoku Solver"
date:   2017-03-26 03:23:00 -0700
categories:
description:
  - OpenCV
  - TesseractOCR
---
This was an idea I had a few weeks ago. I just thought it would be a cool project to learn from and show off afterwards. It turns out, unsurprisingly, that it's actually quite a bit more difficult than I thought initially, so this will definitely be an ongoing post.

The idea is simple: to be able to input a Sudoku puzzle and use an algorithm to quickly solve it. Initially I wanted to make a mobile app but I figured I would start by implementing it on PC first to avoid the trouble of learning mobile at the same time.

virtualenv: `sudokupy`

from git bash: `workon sudokupy`


#### Original Image
This is just a sample sudoku puzzle image. It seems like it's actually really common, it's used in a lot of docs and tutorials on OpenCV.

![1]{:class="img-sudoku"}

#### Gray & Blurry
Next we convert the image to grayscale and apply a Gaussian blur in order to smooth out some of the noise.

![2]{:class="img-sudoku"}

#### Adaptive Threshold
Using an adaptive threshold we convert the image to full white or full black pixels in order to make contour detection easier.

![3]{:class="img-sudoku"}

#### Find Contours
Using OpenCV's `findcontours` function, we find all the contours in the image.

![4]{:class="img-sudoku"}

#### Find Largest Contour
Looping through all the contours, we find the biggest one and assume that it is the contour around the puzzle itself. (More about this assumption)

![5]{:class="img-sudoku"}

#### Warp
Once we have the contour around the puzzle, we adjust the image so that the puzzle is square and as flat as possible.

![6]{:class="img-sudoku"}

#### Adaptive Threshold & Find Lines
We use another adaptive threshold on the warped image in order to find all the lines on it.

![7]{:class="img-sudoku"}

#### Merge Similar Lines
Many of the lines we found actually represented the same line on the puzzle, so we loop through all the lines and combine ones that are close to each other. (Lots more mathy stuff here about how the lines are stored in normal form)

![8]{:class="img-sudoku"}

#### Extract Grid or something and somehow use TesseractOCR to recognize the digits

#### Algorithm to solve the puzzle

#### Couldn't get my webcam to work with OpenCV yet but if we could do this live and display the solution that would be pretty awesome.


[1]: {{site.url}}/assets/original.jpg
[2]: {{site.url}}/assets/gray_and_blurred.jpg
[3]: {{site.url}}/assets/adaptive_threshold.png
[4]: {{site.url}}/assets/all_contours.jpg
[5]: {{site.url}}/assets/biggest_contour.jpg
[6]: {{site.url}}/assets/warp.jpg
[7]: {{site.url}}/assets/all_lines.jpg
[8]: {{site.url}}/assets/merged_lines.jpg
