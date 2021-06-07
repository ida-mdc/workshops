# Image analysis basics (pt4): Automating processes

## Overview
- Collecting output data: CSV files
- Batch processing
- ImageJ macro recording
- Give a dataset, can you count the number of cells in each image

## Content

In this part, we want to show you some of approaches to turn a series of image j commands into a basic macro that will run it as an analysis pipeline, and some of the benefits that can come from that.

1. First I#m going to open the sample image *Embryos.jpg*
2. Now I want to start the macro recorder to record each command that I run. This is useful to do while I play around with the image, and it will give me a record to look back over of all the things I have done - like a lab notebook of the tests I've fun on the image. However, I've already played a bit with this image and decided on a pipeline, so now I will just click through the commands involved in my pipeline:

   a. Duplicate the image and now work on the duplicate.
   
   b. Convert it to 8-bit.
   
   c. Run a median filter (radius 8).
   
   d. Auto threshold with Otsu. (don't close the threshold window).
   
   e. If you used dark background in thresholding, now invert the outcome.
   
   f. Fill the holes (*Process>Binary>Fill Holes*).
   
   g. Use *Analyse>Set Measurements* and decide to look at Area, Mean gray value, centroid, perimetera and shape descriptors. Redirect this analysis (for the gray values) to the original image.
   
   h. Use analyse particles, tick *Exclude on edges*, *Include holes*, and *Add to manager*.
   
   i. *Save as>Results*.

3. Now I can *Create* the macro from what I have recorded. This will open all the commands into the Fiji Macro editor.
4. Close the open windows (except the editor) and open embryos again.
5. Click *Run* in the editor... does it work on the newly opened embryos image?
6. What about if I open another image (try *Blobs*)... does it work on that?
7. You should find it doesn't. Look at the commands and you will see there are a couple of places where the command refers to the name of the image ("Embryos.jpg"). But now the name of the image is "Blobs.gif". To fix this we need to define a variable which we will call `imageName` and use the `getTitle()`command to get the title of the current image.
8. Now we can replace all the incidences of the string "Embryos.jpg" with the variable `imageName`
9. Let's try again on the Blobs image. This time it should work!
10. So now we have automated the pipeline, and we can drag an image into fiji, and run it in one click... But we still have to drag in and click! What about if we have 50... or 50 000 images to analyse? Can we make this macro run on all of them? This requires a little bit more exposure to code, but fortunately some nice people have made templates to help us out.
11. Open the *Process Folder (IJ1 Macro)* in *Templates>ImageJ 1.x>Batch>Process Folder (IJ1 Macro)*
12. This contains a bit more content to understand:

  -The first lines in green are *Comments*. They are not part of the code, instead they are bit's of additional info put in to help you out. Comments in the imageJ macro start with either a `/*` (multi-line) or a `//` (single line).
  
  -The lines beginning `#@` bring up a GUI window where you can manually select the `input`, `output` and `suffix` variables.
  
  -Line 12 (`processFolder(input);`) calls the function `processFolder()` and runs it on the variable `input`. This function is then defined below (lines 15-24)
  
  -The function `processFolder` looks through all the folders and files in the input folder. If it finds a folder, it will apply itself to that folder too (it will therefore work on all subfolders as well). If it finds a file that ends with the chosen suffix (chosen in the GUI), it will run the function `processFile` on it. This function is defined below (currently lines 26-31). It is this function that you need to edit and add the code from the pipeline that you have already made.
13. Make yourself a folder containing images to analyse, put in your code and click run... Does it work? Does it do what you wanted?
14. Probably not... This script is not yet opening anything. The commands we used before worked on an image that had been already opened. Now we need to add the command `Open(input+"/"+file)` to the first line of the function.
15. Notice how we are now referring to the file by its path, using the variables `input` and `file` (and later we also need `output`). Make sure that in the rest of the code (eg in the saveAs line), you are now referring to images and locations using these variables.
16. Try running it again. Does it work?... If so Awesome! :)... If not, don't worry, that's kind of expected. Try to look through for possible errors/typos in the code. Do you understand what each line does? Searching commands on imagej.net can help you with this. Are you getting an error message? Does it make any sense to you? Or at least hint at where you should look?... You could search the error message online to get a better idea what it means and how to solve it. A quick search on google will usually bring up a thread on StackExchange or image.sc etc where someone has had the same problem as you and looking at the best voted answer will often help.

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
