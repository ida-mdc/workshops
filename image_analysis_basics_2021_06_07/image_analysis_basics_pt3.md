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

Now let's take some measurements.

`Fiji menu: Analyze>Analyze Particles`

![Analyze particles window](img/analyze_particles_window.png)

There are a few different things that we can do in this window that
are useful in practice. 

It is very common to want to filter your particles by their area. This
is a threshold on the number of pixels in the particle, where the
range `0-infinity` will include all possible particles.

We have checked a few options:

- `Display results` will display results for each particle that is
  measured
- `Summarize` will record summary statistics of particles measured in
  a given image. This can be useful for quickly comparing measurements between
  images. 
  
`Show` gives us a way to generate image outputs. It can be useful to
show `Count Masks` which stores the number of pixels in each particle
as the value of the mask. Try mousing over a small blob and a big blob
while looking at the pixel values in the status bar.

![Color map of count mask](img/blobs_binary_count_glasbyinvert.png)

Here we have changed the color map of the count mask to the `glasby
invert` LUT. We do this by first selecting our image with the count
masks and then changing the `LUT` of the image.

![Fiji window with LUT selected](img/fiji_toolbar_LUT.png)

# References

- Pete Bankhead's [chapter on thresholding](https://petebankhead.gitbooks.io/imagej-intro)
