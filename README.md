# Object Removal and Inpainting Overview

Inpainting is a technique that fills in plausible backgrounds after an object is removed from a photograph.  This repo attempted to replicate the results of the exemplar-based inpainting following the methods described in the Criminisi et al (2004)’s [paper](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/criminisi_cvpr2003.pdf) 

![Python](https://img.shields.io/badge/Python-3.11-3776AB?logo=python&logoColor=white)
![Status](https://img.shields.io/badge/status-complete-2EA44F)

## Object Removal & Inpainting 
I photographed this grey heron in the Kamo River, Kyoto, Japan in September 2024.  This overview graphic uses my own photo to demonstrate how my inpainting algorithm implementation removes the selected object from the final photograph.

<p align="center">
  <img src="inpainting_graphic.png" width="100%" alt="Photo 1">

</p>


## General Algorithm Summary
Following Anotonio Criminisi et al’s paper ”Region Filling and Object Removal by Exemplar-Based Image Inpainting," I attempted to replicate the algorithm.  Removing an object is relatively easy - one only needs to use a binary mask of the object that is to be removed.  Thus, the focus is every step afterward.  After the object is masked, the target region is filled with patches taken from the known parts of the image called the source region. The patch size is set by a window’s height and width. In each iteration, the algorithm identifies the current boundary of the target region, selects a patch along that boundary according to its priority that it should be filled, and fills it with content from a matching source patch. The source patch is determined by sampling the entire image excluding the target region, calculated by the sum of square differences of each potential source patch from the target patch.  The boundary is updated and the algorithm repeats until the target region is filled. 


## Source Code

The final report and source code are maintained privately in accordance with university academic integrity requirements.



