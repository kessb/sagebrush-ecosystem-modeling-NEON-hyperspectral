# Sagebrush Ecosystem Modeling with Hyperspectral Data

This repository tests the ability of hyperspectral data to detect species-level diversity using open source data and packages in Python.  While this workflow focuses on identifiying greater sagebrush *Artemsia tridentata*, and cheatgrass, *Bromus tectorum* and cheatgrass in a known sagebrush environment at a National Ecological Obervatory Network (NEON) site in Utah (ONAQ), it is adaptable to any other NEON site and focal species/landcover types with known spectral signatures. 
  
This repository is part of a three-part project developed in collaboration with NatureServe, a wildlife conservation non-profit, to examine the efficacy of publicly availble remote sensing data to reconstruct sagebrush ecosystems. The three components of this project test the following for their sensitivity to sagebrush ecosystems:<br>

* LIDAR Canopy Height Models at 1x1 meter resolution, workflow developed by users @kessb and @sarahmjaffe and hosted <a href= "https://github.com/kessb/sagebrush-ecosystem-modelinghere" target="_blank"> here</a> <br>
* LANDSAT 8 Multispectral at 30x30 meter/7 bands, developed by @sarahmjaffe and hosted at her <a href ="https://github.com/sarahmjaffe/sagebrush-ecosystem-modeling-with-landsat8"> Sagebrush Ecosystem Modeling with LANDSAT8 </a> repository.<br> 
* NEON's Hyperspectral at 1x1 meter/426 bands, developed by @kessb and hosted here. <br>

The results of this workflow can be interpreted alone,  or they can also be compared with @sarahmjaffe's LANDSAT workflow. The use of remote sensing data to model sagebrush ecosystems has not been extensively explored; and, along with visualizing the abundance/distribution of our focal species, we hoped to test the efficacy of different spatial/spectral resolutions. Consequently, @kessb and @sarahmjaffe's workflows provide the building blocks for more in-depth analysis of spectral and spatial resolutions in these ecosystems.

# Relevance
Sagebrush ecosystems cover much of the western United States and parts of southwestern Canada. Sagebrush ecosystems provide essential forage and habitat for approximately 350 other species of plants and animals, some of which, like the Greater Sage Grouse, are found only in sagebrush habitat. Sagebrush ecosystems are increasingly fragmented through anthropogenic land use and invasive species, with ranges expected to shift and shrink as warming temperatures force sagebrush populations north. While sagebrush still covers much of the western United States, only 10% of current habitats are considered unaffected by fragmentation. Consequently, many plants and animals associated with sagebrush are losing essential habitat and some qualify as endangered or threatened species under the Endangered Species Act. Conservation efforts targeted to sagebrush ecosystems are costly as they require the surveillance and upkeep of millions of acres of public and private land.

This repository offers an alternative to traditional land monitoring strategies through its unique focus on and analyses of sagebrush ecosystems. 

# Workflow Requirements
## Required Packages
All required packages are included in the repo's environment.yml. To activate the environment and install required packages, fork and clone the repository into the desired local directory and use conda activate nature-serve-env in the command line. 

## Data Sources and Formats
This workflow uses data from NEON and USGS Spectral Library. The required data for this workflow are hosted on @kessb and @sarahmjaffe's figshares, and the workflows will download the required data programatically. However, users are welcome to peruse NEON's page for Spectrometer Orthorectified Surface Directional Reflection - Mosaic (Hyperspectral) data or search the Spectral Library's Convolved to 2014 specifications of AVIRIS< records (linked below) to substitute in their own desired areas and landcover types. The table below represents all data we retrieved to create our blog (found in the 'presentations' folder).

| Data Products                                                               | File Format  |  Puprpose                                              |
|-----------------------------------------------------------------------------|--------------|--------------------------------------------------------|
| <a href= "https://data.neonscience.org/data-products/DP3.30006.001" target="_blank">NEON Spectrometer Orthorectified Surface Directional Reflection - Mosaic </a> | .h5 files  | Aerial Hyperspectral Tile for Endmember Extraction          |
| <a href="https://crustal.usgs.gov/speclab/AV14.php" target="_blank" > USGS Spectral Library Convolved to 2014 specifications of AVIRIS </a> | .txt files | Wavelength and Reflectance Values to Create Spectral Signatures for Endmember Validation |

## Functions
The functions for these workflow have been adapted from NEON's tutorial for <a href= "https://www.neonscience.org/classification-endmember-python" target="_blank"> Unsupervised Endmember Extraction</a> and are saved in the neon_helper_functions.py. They are imported with the library imports in the workflow and help open and clean the .hdf5 hyperspectral files.

## Layout and Run Instructions
This repo is divided into two directories: scripts and presentations. The presentation folder includes a copy of my abridged results (sage_advice_hyperspectral) in both .html and .ipynb. The .ipynb can be run through programmatic data downloads and the associated blog_helper_functions.py in the same directory. The scripts directory contains the unabridged workflows for the endmember sensistivity analysis (see endmember_sensitivity_analysis_ONAQ_tiles.ipynb) and the NEON hyperspectral tile endmember extraction (see sagebrush_hyperspectral_modeling_NEON_ONAQ.ipynb). Also in the scripts directory is file containing the required helper functions (see neon_helper_functions.py). An additional directory, test_scripts, is also located in the scripts folder and contains code currently under development. To run these workflows, the environment.yml must be forked, cloned, and activated. Once the requisite libraries are available, the scripts and presentations directories can be run to download, process, and analyze data. 

Additional code is in progress to 1) subset larger NEON hyperspectral datasets to insitu plot centroids with xarray - in a workflow inspired by Joe McGlinchy's <a href="https://github.com/earthlab/neon-headwall-data" > NEON-headwall-data </a> repository and 2) extract spectral signatures from single pixels. Both approaches offer potential ways to validate data though they are limited by the lack of *insitu* data documentating vegetation coordinates.
