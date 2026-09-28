# Object Removal and Inpainting Overview

Inpainting is a technique that fills in plausible backgrounds after an object is removed from a photograph.  This repo attempted to replicate the results of the exemplar-based inpainting following the methods described in the Criminisi et al (2004)’s [paper](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/criminisi_cvpr2003.pdf) 

![Python](https://img.shields.io/badge/Python-3.11-3776AB?logo=python&logoColor=white)
![Status](https://img.shields.io/badge/status-complete-2EA44F)

## Object Removal & Inpainting 
I photographed this grey heron in the Kamo River, Kyoto, Japan in September 2024.  This graphic uses my own photo to show how my inpainting algorithm removes an object, from the original image and mask through intermediate steps to the final result. 

<p align="center">
  <img src="inpainting_graphic.png" width="100%" alt="Photo 1">

</p>


## Algorithm (Criminisi et al)
The methodology that this paper tried to implement came
from Anotonio Criminisi et al’s paper ”Region Filling and
Object Removal by Exemplar-Based Image Inpainting.” Since
removing an object is relatively easy, such as by using a
mask of the object that is to be removed, the focus was on
filling the image after the object was removed with specified
patches determined by window size (or pixel height and width)
that come from the image with the object removed called the
source. There are multiple steps in Criminisi’s algorithm, such
as identifying the edges of the object that was removed. Each
time the algorithm loops through and a patch is placed in the
area that needs to be filled or the target, the new edge is again
identified.
Identifying the edges of the removed object, or the fill front,
is important because it is from this region that the inpainting
begins and where each pixel is evaluated. A priority function
is computed for each priority patch or window (9x9), which is
the product of the confidence level and data term divided by
the alpha normalization factor (which is 255 for gray images).
The confidence metric measures the number of pixels in the
patch that are already filled over the total area (the patch). The
data term measures how great the isophote is in reaching the
fill front and linear structures are prioritized. The data term is
the product of the isophote and a unit vector orthogonal to the
fill front from each point p (each point p being in the fill front).
Once priorities are computed for each pixel in their respective
patches, the pixel with the maximum priority is identified,
since this pixel patch will be the area to be filled on the fill
front first.
Once the patch to be filled on the fill front is identified, the
next step is to sample the source image to identify the best
patch to replace the priority patch in the fill front. There are
various ways to sample, but the sample population excludes
the target region. We sampled the entire image, excluding the
target region, and calculated the sum of square differences of
each potential source patch from the target patch. The source
patch with the lowest sum of square distance was chosen to
replace the target patch.
One the priority patch is replaced with the source patch,
all values in the matrices are updated. This includes the
confidence term which is updated with the priority pixel of
the fill front’s confidence. The mask is also updated to reflect
that the previously unfilled patch has been filled (we used a
binary mask with 0 to indicate source areas). The confidence
values and the mask being updated allows the algorithm to
loop through its entirety once more.

## Source Code

The final report and source code are maintained privately in accordance with university academic integrity requirements.



