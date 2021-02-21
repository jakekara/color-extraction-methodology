# ColorBook

A color extraction project using modular notebooks

## Overview

This repository of notebooks is used both the production data processing code as well as a live, interactive methodology document for a color analysis project by the Digital Humanities Lab at Yale.

This code was originally used to process the entire Illuminated Books of William Blake, but this repository may be repurposed on any set of images.

## Modular Notebooks

This repository makes extensive use of modular notebooks — that is, notebooks which are imported into other notebooks the same way a `.py` file would be. This is made possible by the the library [margo-loader](https://github.com/margo-notebooks/margo-loader-py), and this repository is intended to demonstrate the potentially for organizing software into modules without moving code from Notebooks into `.py` files.

A more conventional approach to writing this methodology would be to either write the entire thing in one giant notebook that might be hard to follow, or to externalize a large portion of it into `.py` files, which are not as fun!

Because this methodology is written in modular notebooks, each component of the overall system is itself a standalone methodology document, so if you are only interested in one part of the code, you can focus on that. If you are interested in the entire methodology, being able to focus on individual components is useful to understanding the whole.

## Data processing tasks

There are four core tasks we need to accomplish. Because this project is organized in a modular fashion, you can jump to the parts that interest you. You can focus on the notebooks that interest you. You can jump into the notebooks for each color extraction algorithm and see how they work, or you can look at the notebooks that combine these components into the production data processign pipeline.

### Download data

In this stage we download a sample data set -- all of the images in the Metropolitan Museum of Art's API that appear to be created by William Blake.  

Notebooks for perfoming the data acquisition are found in the `data_acuisition` folder.

Here's an original input image. Note the very light area of paper around the edge. 

<img src="out/original/original-jerusalem.mpi.p22-51.100.jpg.png">

### Background deletion

In this stage we take a single image and "delete" any pixels that fall below a certain lightness threshold based on the pixel's HLS colorspace representation. By delete we actually just set their alpha channel to zero.  

Notebooks for performing this background deletion are in the `background_deletion` folder.

Here's an image after performing background deletion. Note that light paper area is gone.

<img src="out/no_background/no_background-jerusalem.mpi.p22-51.100.jpg.png">

### Extract color palette

In this stage we take an image that has had background pixels deleted and generate a summary palette for the image. We implement this approach using several different algorithms, so that the researcher can choose which one they prefer. Because this collection of notebooks is written as modules, these color palette extractors are all interchangeable, and even though we only used one algorithm, the code for all of the algorithms we tried is accessible in Notebooks.

Notebooks for performing color palette extraction are in the `color_extraction` folder.

The color palette we extract from an image looks like this. It is a JSON object where each key is an color represented as an RGB value, and each value is the count of pixels that were clustered into this bin of pixels. This allows us to constrct proprotional color palettes for each image.

```javascript
{"rgb(73,37,28)": 10, "rgb(150,67,42)": 27, "rgb(191,104,56)": 21, "rgb(96,82,92)": 1061, "rgb(184,55,57)": 80, "rgb(111,98,109)": 397, "rgb(151,44,48)": 619, "rgb(90,77,76)": 6630, "rgb(105,93,88)": 4306, "rgb(154,136,141)": 256, "rgb(103,74,72)": 17643, "rgb(48,17,39)": 3419, "rgb(66,25,45)": 4625, "rgb(167,150,135)": 1116, "rgb(122,87,80)": 22984, "rgb(127,111,102)": 5494, "rgb(78,54,60)": 38068, "rgb(152,114,101)": 23375, "rgb(193,152,129)": 8064}
```

When we use the summary palette to reconstruct an image, it looks like this:

<img src="out/quantized/quantized-jerusalem.mpi.p22-51.100.jpg.png">


### Process all of the images

In this stage we use the background deletion and color extraction components to create a complete data processing pipeline to process all of the images in our sample data set. We create one notebook to process a single image, and then we call the function defined in that notebook on every image in the sample data set.

Notebooks for performing the data processing are in the `data_processing` folder.
