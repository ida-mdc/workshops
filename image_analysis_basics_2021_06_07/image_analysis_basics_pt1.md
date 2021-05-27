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
![img/fiji_toolbar.png](Image of the Fiji toolbar)

There are a few efficient ways of using this:

1. Most functionality is made available through menus. For example
   try:
   `File>Open Samples>Blobs`
   
2. The search is available in the bottom right of the toolbar.
![img/fiji_toolbar_search.png](Image of the Fiji toolbar with search
box highlighted)
Try typing `Blobs`

**Protip: when the Fiji window is active press the letter 'l' and this
will activate the toolbar, then simply type whatever
command/plugin/etc. you want to use**

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
```
Fiji: File>Open Samples>Hela Cells
```
