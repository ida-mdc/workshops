# Image analysis basics (pt4): Automating processes

## Overview
- Collecting output data: CSV files
- Batch processing
- ImageJ macro recording
- Give a dataset, can you count the number of cells in each image

## Content



## Exercise

### Objective:
Now it's time for you to have a little more freedom to design an analysis pipeline and get it to run automatically on a large dataset. We're going to look at a time series of sporozoites of the malaria parasite *Plasmodium falciparum*. Their high motility is a key factor in their ability to invade liver cells after infection and attempts to understand and affect this is the target of drug and vaccine research. We're going to try to design an automated analysis pipeline to characterise their motile behavoir in a dish.

1. Open the file Malaria Sporozoites in *File>Open Samples*. Check out the crazy little guys going round in circles.
2. In this case we could analyse this as a whole movie, but instead we want to learn to automate an analysis and run it on many individual files. So let's save it on your computer as such. Use *File>Save As>Image Sequence...* and select *TIFF* format. Then create a folder for this image sequence in a directory of your choice on your computer.
3. Now close the movie, go to the folder containing the image sequence and drag in to fiji 2 trial frames from it. It can be good to use one near the beginning and one near the end. Using these frames you will design your pipeline.
4. First we need to think of what outputs we'd could generate that would quantify characteristics of the sporozoite behaviour. Some ideas:
  -To describe the motility, we could look at things like velocity, angular velocity, circling radius etc. To do this we need to measure it's location over time and a good quantification of its location could be the X- and Y- coordinates of its centroid.
  -In the movie, we also see that the sporozoite's movement correlates with its shape, so it could be good to measure some *Shape descriptors* like circularity, aspect ratio and Area.
5. To get the measurements above, our pipeline is going to need to *Segment* out which pixels belong to each sporozoite and then take the measurements on those. Some things to consider putting in the pipeline:
  -Preprocessing: Do we need some denoising steps (filtering?) or is the signal to noise ratio good enough to auto-threshold every frame?
  -Segmentation: How are we going to decide on a threshold to segment the images. Is there a good auto-thresholding approach?
  -Post-processing: Is the segmentation going to work well for all the images? Will there be some speckles (false positives/negatives) that we need to clean up (eg *Erode, Dilate*)
  -Quantification: Which Fiji commands can we run on the segmented image to extract the outputs measurements we want? (*Set Measurements, Analyze Particles, Skeletonize*)
  -Saving outputs: Can we collect together the appropriate output data and save it eg in a .csv file?
6. If we manage to do all the steps above, we should have a set of commands that work. Now let's try to record them into a Macro script. Open a new raw image from your saved folder and start the recorder with *Plugins>Macros>Record*. Now click through the sequence of operations you defined in your pipeline above and watch as the Recorder writes out for you the sequence of commands to do what you want are doing. If you make a mistake, you can delete the command from the recorder. Once you're done, click *Create* and it will open as a *.ijm* file in the Fiji editor. Here you can save it, do further manual editing, or copy in more commands from the recorder if you want.
7. Now Open a new raw image again and click *Run* on the macro. Can you get it to complete all the operations on your image?
8. Now lets add our pipeline to a tamplate macro that will loop through all the files in your folder. Within the editor window, use *Templates>ImageJ 1.x>Batch>Process Folder (IJ1 Macro)*
