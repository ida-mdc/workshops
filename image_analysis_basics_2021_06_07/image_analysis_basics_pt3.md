# Image analysis basics (pt3)

The concepts we aim to address in this section are focused on finding
and quantifying *things* in your images, where *things* may be cells,
particles, dogs, unicorns, stars, etc.. 

To begin, let's start with our trusty `blobs` image:

`Fiji search: blobs`

![Example image from Fiji called blobs](img/blobs.png)

We see a collection of spots. How many spots are there? There are more
spots than fingers on our hands, so I'll have trouble counting
accurately. Let's do this the easy way!

## Thresholding

We want to threshold the image. This means we need to find a threshold
that allows us to say if a pixel belongs to one our blobs of interest
or not. 

`Fiji search: threshold`

Now we need to find a good threshold value. With this tool we can find
the threshold value either manually or automatically.

![Threshold window](img/threshold_window.png)

The sliders allow us to change the minimum and maximum value for
thresholding. However, we can also use an algorithm to automatically
find our threshold. 

![Threshold window with autothreshold highlighted](img/threshold_window_autothreshold.png)

Press `Apply` to make a binary mask of the image.

![Binary mask of blobs](img/blobs_binary.png)

## Binary Operations: erode, dilate

Binary operations are ways of processing a binary image that can
facilitate taking some measurements of the things that you've detected
in your image.

Now let's make a duplicate of the binary image so we have a copy for
experimenting with.

`Fiji menu: Image>Duplicate`

Now let's `erode` the image.

`Fiji menu: Process>Binary>Erode`

![Eroded binary mask of blobs](img/blobs_binary_erode.png)

Our blobs have now gotten smaller, and some of the smallest objects
have disappeared. The erode operation removes the boundary pixels of
a binary object.

Now let's `dilate` that same image.

`Fiji menu: Process>Binary>Dilate`

![Dilation of an eroded binary mask of
blobs](img/blobs_binary_erode_dilate.png)

Interestingly most of our blobs look almost like they did previously,
but the small blobs have disappeared. However, some shapes have become
more blocky. This is due to the fact that we lost some information
during the first erosion and we simply cannot recover it when we
perform the following dilation.

Let's inspect the difference.

`Fiji menu: Image>Color>Merge Channels`

![Merge channels window](img/merge_channels_window.png)

We end up with the following result, where we can see pixels that
belong to our original binary mask in cyan, and if there were any
pixels belonging to the processed binary mask then they would be shown
in magenta.

![Composite of binary masks from blobs](img/blobs_binary_composite.png)

## Taking measurements


## Connected Component Analysis


# References

- Pete Bankhead's [chapter on thresholding](https://petebankhead.gitbooks.io/imagej-intro)
