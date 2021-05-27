**Image analysis basics (pt1)**
Kyle Harrington, mdc@kyleharrington.com

# Getting setup

## HIPS

TBD

## Fiji

Download Fiji from
[https://imagej.net/Fiji/Downloads](https://imagej.net/Fiji/Downloads)

# Introduction

[Basic
concepts](https://datacarpentry.org/image-processing/01-introduction/index.html)
from Data Carpentry workshop  
[Pixels and file formats](https://datacarpentry.org/image-processing/02-image-basics/index.html)

# Getting started with Fiji

When you open Fiji you will get the following toolbar:
![Image of the Fiji toolbar](img/fiji_toolbar.png)

There are a few efficient ways of using this:

1. Most functionality is made available through menus. For example
   try:
   `File>Open Samples>Blobs`
   
2. The search is available in the bottom right of the toolbar.
![Image of the Fiji toolbar with search box highlighted](img/fiji_toolbar_search.png)
Try typing `Blobs`

**Protip: when the Fiji window is active press the letter 'l' and this
will activate the toolbar, then simply type whatever
command/plugin/etc. you want to use.**

Many of the example commands in this workshop will be listed as:  
`Fiji search: <some phrase>`

3. Finally there are some basic icons shown on the toolbar
   itself. These may be familiar from other image editing tools you've used.

## Image Representation

Pixels of an image may be represented in different ways. This relates
to how much *memory* is used by the image, and affects the range of
values that can be represented in pixels. 

- 8-bit (0-255), integer only
- 16-bit (0-65536), integer only
- 32-bit, floating point, decimal
- RGB, 32-bit with 8-bit for each color

There can be other pixel types with higher/lower resolutions and
representing different types of data, but these are the key types in Fiji.

**Activity:**

`Fiji search: hela cells`

Note that there is a horizontal scroll bar at the bottom of the screen
now which shows the currently active channel. This is for the red,
green, and blue channels of the image.

![HeLa cells example image from Fiji](img/hela_cells.png)

Note that the active channel is shown at the top of the image (in this
example in blue)

Also note, that as you move your mouse over the image the location and
pixel value is shown on the Fiji toolbar:

![Showing that Fiji shows pixel location and value when mousing over
image data](img/mouse_over_pixel_location_value.png)

`Fiji search: brightnesscontrast`

You should get a window like this (the color may be different if you
played around with the channel selection scroll bar)

![The brightness/contrast adjustment window](img/brightness_contrast.png)

Adjust the channels to get a sense about how the visual representation
of the image changes. Note that as you adjust the
minimum/maximum/brightness/contrast the `value` of the pixel does not
change only the visual representation.



