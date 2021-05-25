# Image analysis basics (pt2)

### Talk contents:

- What is Fiji/ImageJ?
- Opening images, stacks, series' & metadata'
- Magnifier, hand, selection tools (points, angles, lines & shapes), annotation & drawing tools.
- Handling stack dimensions (x,y,z,t,ch): Stacks & Hyperstacks
- Manipulating stack dimensions: Slice keeper/remover, Z-Projection, Split & Merge channels
- Positions & their pixel values
- Switching bit depths, look Up tables & their associated issues
- Adjusting brightness & histograms
- Show info (ctrl+i), Set scale, Set Measurements, Measure
- What is a filter?
- Mean, Median and Gaussian filters (smoothing/denoising)
- Edge detection - eg Soebel Filter

### Excercise:

1. Open sample Mitosis.tif (*File>Open Samples>Mitosis*).
3. Scroll through the different Z-depths and Timepoints of the image.
4. Use magnifier & hand tools to zoom in and scroll around the image.
5. How many dimensions does the stack have? What is the size of each dimension?
6. Zoom in and choose a single voxel - can you give the coordinates of this voxel in all dimensions? What intensity does it have in each channel?
7. Go to frame *Z:3/5 T=3/51*
8. Use the *Image>Adjust>Brightness/Contrast* window to look at the histograms for both channels.
9. Adjust the *Maximum* and *Minimum* values to set the contrast how you like it.
10. Try clicking *Auto* to automatically set contrast levels and *Set* to manually input the Max and Min displayed levels
11. So far we have only adjusted the brightness with which each intensity value is visualised. The pixel intensity values remain the same. Clicking *Apply* would change the underlying value of each pixel and rescale them from the Minimum to the Maximum according to the image bit depth. **Generally it is not advisable to *Apply* changes, as pixel intensities are manupilated and information can be lost due to saturation.**
12. If in the last step you clicked *Apply*, close the image and reopen Mitosis.tif
13. 
