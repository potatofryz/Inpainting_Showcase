# Object Removal and Inpainting Overview

Inpainting is a technique that fills in plausible backgrounds after an object is removed from a photograph.  This repo attempted to replicate the results of the exemplar-based inpainting following the methods described in the Criminisi et al (2004)’s [paper](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/criminisi_cvpr2003.pdf) 

![Python](https://img.shields.io/badge/Python-3.11-3776AB?logo=python&logoColor=white)
![Status](https://img.shields.io/badge/status-complete-2EA44F)

## Object Removal & Inpainting 
I photographed this grey heron in the Kamo River, Kyoto, Japan in September 2024.  This graphic uses my own photo to show how my inpainting algorithm removes an object, from the original image and mask through intermediate steps to the final result. 

<p align="center">
  <img src="inpainting_graphic.png" width="100%" alt="Photo 1">

</p>


## General Summary of Criminisi et al's Algorithm & My Implementation
Following Anotonio Criminisi et al’s paper ”Region Filling and Object Removal by Exemplar-Based Image Inpainting," I attempted the replicate the algorithm.  Removing an object is relatively easy, such as using a mask of the object that is to be removed.  Thus, the focus is every step afterward.  After the object is masked, the target region is filled with patches taken from the known parts of the image called the source region. The patch size is set by a window’s height and width. In each iteration, the algorithm identifies the current boundary of the target region, selects a patch along that boundary, and fills it with content from a matching source patch. It then updates the boundary and repeats until the target region is filled. 


## Source Code

The final report and source code are maintained privately in accordance with university academic integrity requirements.



