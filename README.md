# SubglacialBedforms  


## Table of Contents  
1. [Description](#description)  
2. [Installation](#installation)  
3. [Required Data](#required-data)  
4. [Computation Time and Recommendations](#computation-time-and-recommendations)  
5. [Usage Examples and Scripts](#usage-examples-and-scripts)  
6. [Contributing](#contributing)  
7. [License](#license)  
8. [Contact](#contact)  





## Description  
This set of scripts is part of the work described in the publication available at the following link: [link]. Its purpose is to automate the mapping of subglacial bedforms, producing geomorphological maps (bedform outlines and centerlines) as well as morphometric maps (bedform outlines and hexagonal grids with values of various morphometric parameters [Morphometric_parameters](/Documentation/Morphometric_parameters.md).  

The goal of these cartographic products is to support the reconstruction of ice sheet dynamics by providing insights into subglacial environments, such as subglacial deformation or hydrology.

The scripts are written in Python, but result visualization can be simplified using GIS software such as QGIS (free) or ArcGIS (paid).  

---

## Installation  
The scripts are written in Python, so Python 3.X must be installed. The required libraries are detailed at the beginning of each script under the **Imports** section and can usually be installed via standard methods (e.g., install `numpy` by running `pip install numpy` in the command prompt if Python and pip are installed).  

For clarity, the scripts are provided as Jupyter notebooks with minimal reproductible examples.  

---

## Required Data  

1. **Digital Elevation Model (DEM)**  
   The primary input is a DEM of the study area, with a resolution appropriate to the level of detail expected by the user. During the tool’s development, DEMs from ArcticDEM (https://www.pgc.umn.edu/data/arcticdem/) were used at a 10-meter resolution. (ex: [input_DEM](/Outlines_and_centerlines_delineation/input_DEM.tif))

2. **Normalized Difference Water Index (NDWI) Image**  
   The second required input is an image representing the NDWI of the same area as the DEM. This image is used to filter out water bodies, such as lakes, which are prevalent in regions where this method has been developed (e.g., Canada, Laurentide Ice Sheet, Keewatin area). NDWI is calculated from satellite imagery bands, and the equations are described in various sources for each satellite data provider.  (ex: [input_NDWI](/Outlines_and_centerlines_delineation/input_NDWI.tif))

   A [script](/NDWI/NDWI_download_notebook.ipynb) for downloading satellite images and NDWI is provided, but it is not fully stable yet and is not officially part of the publication.  

   Alternatively, the scripts could run without NDWI input; however, this may result in noisy outputs if water bodies are present in the study area, requiring additional post-processing techniques.  

4. **Custom Grids for Sampling Morphometric Data**  
   Users can also supply their own grids for sampling morphometric data based on bedform outlines. (see [Custom_grid_Morphometric_parameters_calculation_and_statistical_sampling](Morphometric_parameters_calculation_and_statistical_sampling/Custom_grid_Morphometric_parameters_calculation_and_statistical_sampling.ipynb))

---

## Computation Time and Recommendations  
- **DEM Size**: Computation time increases roughly linearly with DEM size.  
- **Search Radius (VO)**: The execution time grows quadratically with the radius of the moving window used in the analysis.  

The smoothing algorithms for bedform outlines and centerlines are the most computationally expensive steps. If you modify the scripts, it is advisable to exclude these steps for initial tests and include them once the workflow is validated.  

A common source of error is misalignment between the DEM and NDWI image. GIS software usually handles on-the-fly reprojections for such datasets. However, in Python, these data are treated as matrices during computations, so it is crucial to verify their orientation. The scripts provide intermediate outputs to help troubleshoot such issues.  

Finally, ensure that the DEM and NDWI images have the same resolution for proper analysis.


## Usage Examples and Scripts

The scripts, along with usage examples, are available in the form of two notebooks. The [first](Outlines_and_centerlines_delineation/Outlines_and_centerlines_delineation.ipynb) produces outline and centerline maps, while the [second](Morphometric_parameters_calculation_and_statistical_sampling/Morphometric_parameters_calculation_and_statistical_sampling.ipynb) processes these maps to generate morphometric maps, such as [hexagonal grid maps](Morphometric_parameters_calculation_and_statistical_sampling/hexagonal_grid_with_morphometrics.gpkg).

The necessary inputs to obtain a minimal reproducible example, as well as the corresponding outputs, are provided and already illustrated in each of the two notebooks.

## Contact  
For any questions, issues, or collaboration requests, feel free to reach out:  
- **Email**: sofyane.hesni@gmail.com 
- **GitHub**: [HesniSofyane](https://github.com/HesniSofyane)  
