# buildings-height-estimation
To estimate building's height on historical maps based on the building's characteristics in the present time using Random Forest Regression.

## About
This project aims to estimate building's height on historical maps based on the building's characteristics in the present time. Random forest regression are used to estimate the building's height, and the result will be visualized into 3D City Model Visualization that could be used for further spatial analysis.

## Historical Map 
Historical maps are one of the data available from the past. These maps are commonly found in physical form, have small scales, and missing the height of objects depicted in the map.

## Data Understanding
Data used in this project are derived and calculated from various sources (Sekolah Tinggi Teknik Cirebon archives, Heritage Smart City Planning research results, and Direktorat Penataan Bangunan dan Lingkungan Kementerian Pekerja Umum) and some of them are confidential. 

List of data used: 
- Building's characteristics of Cirebon City 1940
- Building's characteristics of Cirebon City 2020

Data Dictionary (predictors): 
  - Perimeter : the perimeter of each building
  - VxCount   : the number of vertices (edge) of each building 
  - CentroidX : the value of centroid of X coordinate for each building
  - CentroidY : the value of centroid of Y coordinate for each building
  - Shape_Area: the area of each building
  - neighborco: the value of neighbors around the building
  - Kategori_Bangunan: the category of each building
  - Z_Mean    : building's height
    - KawasanPerdagangan    : market area
    - KawasanPermukiman     : residential area
    - KawasanPrasarana      : public facilities and infrastructure area
    - KawasanWisata         : tourist area
    - BangunanKeraton       : palace buildings
    - WilayahJasa           : public services area

## Modeling Flow    
### 1. Data Preparation 
- Predictors calculation  : historical map and orthophoto processing GIS software (ArcGIS and QGIS)
- Target calculation      : DTM and DSM processing using ArcGIS
- Code                    : Python in Jupyter Notebook
- Packages                : Scikit-learn, pandas, matplotlib

### 2. Data Splitting
the Cirebon 2020 data are split into training and testing data.

### 3. Data Analysis
**Correlation between predictors:** are calculated using pearson's for both numerical perdictors, phi K for both categorical predictors, and point biserial for correlation between numerical and categorical predictors. 

![image](https://user-images.githubusercontent.com/92083593/136366424-d147d949-8e26-4923-b757-bf4dbfbafe42.png) ![image](https://user-images.githubusercontent.com/92083593/136366978-7b5e99b3-ca9b-473b-826c-1f9cf81ae7d7.png) ![image](https://user-images.githubusercontent.com/92083593/136366843-1898e2f4-8507-4626-b98e-a751d9f56ca0.png)

**Feature Importance:**

![image](https://user-images.githubusercontent.com/92083593/136367029-55cf421e-a731-46bc-b170-240c3892c772.png)

predictors correlation and importace analysis resulting in the elimination of shape area predictor. 

### 3. Model Building
Random forest regression model are built using the training data of Cirebon 2020 data only.

### 4. Evaluate 
The model are evaluated by calculating the MAE, MSE, and RMSE between building's actual height and estimated height of Cirebon 2020 data. The values are 1.12, 1.75, and 1.32 meters respectively. 

The height value are also extruded to 3D Visualization for visual evaluation purpose. 

![image](https://user-images.githubusercontent.com/92083593/136368371-2349de99-e815-4b37-aee2-43162431f215.png)

### 5. Predict Data
The model are then used to predict/estimate building's height in the Cirebon 1940 historical map. 

## Summary
The model had successfully estimate the building's height on the 1940 Cirebon Map in respect to Cirebon 2020 data resulting R-Squared value 61.2 % and various metrics for estimated building height are calculated using MAE, MSE, and RMSE as 1.12, 1.75, and 1.32 meters respectively. Building's height are applied to build the 3D Model Visualization. Thank you!

![image](https://user-images.githubusercontent.com/92083593/136369570-0c0391d9-8513-47d2-9f65-cdc5318fd3a1.png)

