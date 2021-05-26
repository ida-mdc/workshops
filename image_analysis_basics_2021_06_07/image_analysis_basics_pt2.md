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
3. Let's get a feel for the image: Use the scrollbars to move through the different Z-depths and Timepoints. Use the magnifier & hand tools to zoom in and move around the image.
4. How many dimensions does the stack have? What is the size of each dimension?
5. Zoom in far and select a individual voxel - can you give the coordinates of this voxel in all dimensions? What intensity does it have in each channel?
6. Go to frame *Z:3/5 T=3/51*
7. Use the *Image>Adjust>Brightness/Contrast* window to look at the histograms for both channels.
8. Adjust the *Maximum* and *Minimum* values to set the contrast how you like it.
9. Try clicking *Auto* to automatically set contrast levels and *Set* to manually input the Max and Min displayed levels.
10. So far we have only adjusted the brightness with which each intensity value is visualised. The pixel intensity values remain the same. Clicking *Apply* would change the underlying value of each pixel and rescale them from the Minimum to the Maximum according to the image bit depth. **Generally it is not advisable to *Apply* changes, as pixel intensities are manupilated and information can be lost due to saturation.**
11. If in the last step you did click *Apply*, close the image and reopen Mitosis.tif
12. Duplicate the stack. It can be good practice to do this before each step as often there is no undo function. (use *Image>Duplicate* and tick the *Duplicate hyperstack* checkbox)
13. Let's get some info from the image metadata: With the image selected, click *Image>Show Info* or use *Ctrl+i*
14. What is the width and height of each pixel? what about the Z-depth between each slice?
15. The authors have added some info of their own about what has been imaged. It shows GFP-Aurora B and an mCherry-tubulin protein. The colours (LUTs) in the image are, however, the reverse of the colours of the fluorescent proteins. Lets change that to make Channel 1 (GFP-Aurora B) green and Channel 2 (mCherry-tubulin) is magenta. Use the channel scroll bar to switch between channels and use *Image>Lookup Tables* to choose the color you want to use to display each channel.
16. Reduce the image dimensionality by creating a maximum Z-projection (*Image>Stacks>Z-project*). Try this again with an averge projection and compare - what issues could each approach bring?
17. Let's split the channels so that we can work on one at a time. Use *Image>Color>Split Channels*
18. 
