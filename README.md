# buildings-height-estimation
To estimate building's height on historical maps based on the building's characteristics in the present time using Random Forest Regression.

## About
This project aims to estimate building's height on historical maps based on the building's characteristics in the present time. Random forest regression are used to estimate the building's height, and the result will be visualized into 3D City Model Visualization that could be used for further spatial analysis.

## Historical Map 
Historical maps are one of the data available from the past. These maps are commonly found in physical form, have small scales, and missing the height of objects depicted in the map.

## Data Understanding
Data used in this project are derived and calculated from various sources (Sekolah Tinggi Teknik Cirebon archives, Heritage Smart City Planning research results, and Direktorat Penataan Bangunan dan Lingkungan Kementerian Pekerja Umum) and some of them are confidential. 

• List of data used: 
  • Building's characteristics of Cirebon City 1940
  • Building's characteristics of Cirebon City 2020

• Data Dictionary (predictors): 
  • Perimeter : the perimeter of each building
  • VxCount   : the number of vertices (edge) of each building 
  • CentroidX : the value of centroid of X coordinate for each building
  • CentroidY : the value of centroid of Y coordinate for each building
  • Shape_Area: the area of each building
  • neighborco: the value of neighbors around the building
  • Kategori_Bangunan: the category of each building
  • Z_Mean    : building's height
    • KawasanPerdagangan    : market area
    • KawasanPermukiman     : residential area
    • KawasanPrasarana      : public facilities and infrastructure area
    • KawasanWisata         : tourist area
    • BangunanKeraton       : palace buildings
    • WilayahJasa           : public services area
    
## Data Preparation
• Predictors calculation  : historical map and orthophoto processing GIS software (ArcGIS and QGIS)
• Target calculation      : DTM and DSM processing using ArcGIS
• Code                    : Python in Jupyter Notebook
• Packages                : Scikit-learn, pandas, matplotlib
    
## Summary
The model had successfully estimate the building's height on the 1940 Cirebon Map in respect to Cirebon 2020 data resulting R-Squared value 61.2 % and various metrics for estimated building height are calculated using MAE, MSE, and RMSE as 1.12, 1.75, and 1.32 meters respectively. Building's height are applied to build the 3D Model Visualization.
