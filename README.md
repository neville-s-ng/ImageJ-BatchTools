# ImageJ Batch Tools

Copyright (c) 2014-2024, Neville S. Ng.

All rights reserved. The author assumes no responsibility for its use by other parties, and makes no guarantees, expressed or implied, about its quality, reliability, or any other characteristic. Please acknowledge ImageJ Batch Tools if this software is used in publications or theses. 

https://sites.imagej.net/BatchTools/

## Description 

Toolbar to support batch image processing and analysis, including batch extract, batch merge channels, composite conversion, Z-projection, channel B&C and colour adjustment, file export, and cell count, gray value & area.

Intended for handling small to medium sized datasets (10s-100s of images).

## Install

### Built-in

- Open ImageJ and click Help -> Update...
- Click Manage Update Sites, find and enable BatchTools
- On the ImageJ Toolbar, click the More Tools ">>" icon and select "Batch Tools"

### Manual
- Download "Batch Tools.ijm" into ImageJ\macros\toolsets\
- Click Plugins -> Macros -> Install... and select "Batch Tools.ijm"
- On the ImageJ Toolbar, click the More Tools ">>" icon and select "Batch Tools"

## Tools
- Batch Extract
	- For extracting images from Bio-Formats compatible files (e.g. .nd2, .lif, .lsm, etc.) to TIFF files
	- Useful for processing raw data in absence of proprietary software and when multiple samples are stored in a single file
	- Export each item/series with separate files for separate channels, or single files with merged channels
	- Processes 1 input file at a time
- Batch Merge
	- For merging multiple channels into intended channels, useful for merging individual channel files, changing channel assignments or changing channel order
	- Assumes files have been exported into individual files with channel suffix prior to file extension (e.g. suffix "_ch00.tif" of "Image1_ch00.tif")
        - Channel suffixes are entered by user to intended channels to merge as (e.g. all files with suffix "_ch00.tif" to C3 Blue)
	- Channel Order is defined based on to be assigned channel (not source channel)
		- e.g. "431" implies a final channel order of Channel 4 (Gray), Channel 3 (Blue), Channel 2 (Green) irrespective of the original image channel colour
        - Input path can be a single file or a directory 
        - In the case of a directory ALL files matching channel suffixes in selected directory will be opened for merging; remove any unintended files
- Batch Composite
	- Converts all open images to composite images
- Batch Max Intensity
	- Creates maximal intensity projections of all open images
- Batch Channel Settings
	- Adjust B&C applies the B&C of current image to all other open images, or applies Enhances Contrast to all images 
	- Adjust channel selection changes the currently selected channel to a different colour
- Batch Export
	- Exports all open images as PNG or TIFF
- Cell Analyser Parameters
	- Settings should be checked with each experimental analysis before using Cell Analyser
	- ROI Min and Max can be adjusted by changing "Accept" to "Change" and clicking OK, this requires an open image or a newly opened one to draw example circles to calculate intended areas
	- Set ROI channel 1 and 2 to the same channel if counting a single labelled target
	- Set ROI channel 1 to the counterstain (or the smaller area stain) and channel 2 to the mask if counting double labels
	- Set both ROI channels to 1 if input file is a single channel gray image
	- Smoothing, Binary and Watershed may help segregate edges of cells particularly with clusters
	- Entire Image ROI will return the intensity and area of the entire image
	- Measurement result as summary only will return the total number of objects counted, average mean and intensity rather than every object
- Cell Analyser
	- Counts ROIs, areas and intensities with Analyze Particles based on settings defined by the parameters tool, of the currently selected image or a newly opened one
	- Thresholds for target stain(s) are adjusted with the ImageJ Threshold tool
	- Data is displayed in Summary table and saved as a .csv file in image file location
- Batch Cell Analyser 
	- Runs cell analyser on all open/newly opened images
	- First image is used as configuration for thresholding
	- Note that during analysis, the results window will be opened and may interfere with multitasking
	- Data is displayed in Summary table and saved as .csv file in image file location

## Acknowledgements

All developers and maintainers of the ImageJ community

