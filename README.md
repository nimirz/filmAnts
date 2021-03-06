# filmAnts
We are recording using [OAK-D cameras](https://shop.luxonis.com/products/1098obcenclosure) which are powerful cameras that allow us to run neural networks on board. There are 3 cameras on the device: a central 4K color camera, plus left and right 720p mono cameras that enable depth perception. This script allows you to do a basic 1080p recording using the central camera and control the camera settings using keystrokes. For more information check out the DepthAi [documentation](https://docs.luxonis.com/en/latest/).

## Recording Videos

The following steps will get you started with recording:

1. **Environment Setup**: use **`filmAnts.yml`** to setup a conda environment to ensure all of the required packages are installed. Conda is a package management system for python, if it is not installed I recommend installing [miniconda](https://docs.conda.io/en/latest/miniconda.html). Open a terminal and run the following commands:\
a. Create the environment: `conda create --name filmAnts --file filmAnts.yml` \
b. Activate the environment `conda activate filmAnts`

2. **Camera Setup**: connect the camera to your computer using a USB cable. 

3. **Recording**: the script **`encode.py`** will encode h265 or h264 videos at 1080p and 30 frames per second. To begin recording type: \
`python encode.py --output /path/to/output_file.h265` 

This will launch a preview window where you can see what is being recorded and save the output in the provided location.

4. **Camera setings**: the following keystrokes allow you to change settings on the camera \
\
*Lens Position*: **,** increases and **.** decreases \
*Exposure*: **o** increases and **i** decreases \
*ISO*: **l** increases and **k** decreases \
 *press **q** to end the recording* 
 
 The values for each camera setting will be printed out in the console. After noting the values that work well for the camera setup, you can begin the recording with these settings by adding the optional arguments: \
 `python encode.py --output /path/to/output_file.h265 --exposure exp_value --iso iso_value --lens lens_position`
 
 5. **Convert to mp4**: use ffmpeg to convert h265 to mp4 (download ffmpeg from [here](https://www.ffmpeg.org/) if you do not have it). \
 `ffmpeg -framerate 30 -i /path/to/output_file.h265 -c copy /path/to/video.mp4`

## Saving Videos

Save the h265 videos under ouput/h265 and the converted mp4 in the output/mp4 folder. All videos used for analysis should be transfered to the external hard drive and/or uploaded to the sharepoint folder.


## Metadata for videos
For each video recorded, keep track of the filming conditions in a spreadsheet. Important things to note are date, time of recording, camera distance, walking substrate, and trail width, as well as any experimental alterations.

