Deep Learning Model for GeoSpatail Data:

The Copernicus Data Store (CDS) is a one stop shop for a wide range of historical and real time geospatial data from various remote sensing and on-the-ground weather observations. The CDS API allows for programmatic access to this data store. This API is used to obtain the following data from the ERA5-Land Hourly Reanalysis Dataset. The section in square brackets refers to the specifics of the download - 

1. Temperature of air at 2m above the surface - [2m Temperature - 2019 - December - First 15 days - 12:00 - Whole Available Region - NetCDF]

2. Total precipitation - [Total Precipitation - 2019 - December - First 15 days -12:00 - Whole Available Region - NetCDF]

3. Volumetric soil water layer 1 - [Volumetric soil water layer 1 - 2019 - December - First 15 days - 12:00 - Whole Available Region - NetCDF]

The first part of the notebook includes code that invokes the CDS API to download the three datasets outlined above.

Required Libraries:
1. cdsapi
2. numpy
3. pandas
4. xarray
5. scipy
6. sklearn.metrics
7. torch

Steps to install CDS API:
1. Install the CDS API key
    In the file $HOME/.cdsapirc (in your Unix/Linux environment). 
    url: https://cds.climate.copernicus.eu/api/v2
    key: 71165:c04a079f-80be-4b6a-a739-a2b94a291866
2. Install the CDS API client
    $ pip install cdsapi
3. Use the CDS API client for data access
    import cdsapi
    c = cdsapi.Client()

    c.retrieve("dataset-short-name", 
        {... sub-selection request ...}, 
        "target-file"
        )

Answers to Deep Learning for Geospatial Data questions:
1. How you will split the data for training, validation & testing?
Ans. I split the data into 0.8:0.1:0.1 for training, validation and testing respectively. This was done considering the dataset was for 7 days and divided nearly 5 days for training and a day each for validation and test set.
2. Implementations for data loading, data transformations & inverse transformation?
Ans. NA
3. Choice of Model architecture?
Ans. The model chosen is a multi layer perceptron designed for regression, it consists of a single input layer with sigmoidal activation and a similar hidden layer and an output layer. The initial goal was implement a time series based LSTM network but choose to implement this due to time constraints, as well as the processing power required for training the model was too much.
4. Obtaining and Fine-tuning a pre-trained model if used?
Ans. NA
5. Function descriptions and definitions for model training, testing and inference?
Ans.
6. Your choice of activation function, loss function and error metrics?
Ans. Activation Function: Sigmoid Function
     Loss Function: Mean Squared Error minimisation
     Error Metric: Mean Squared Error
7. Implementation techniques that help improve the efficiency of model training and data loading?
Ans. NA
8. How you will avoid overfitting (and implementation of solution)?
ANs. I tried a combination of tuning parameters to look for cases of overfitting within the training dataset.
9. What do you use for visualising model training and performance?
Ans. I plotted a graph between the predicted and actual result from the test dataset and gave MSE and RMSE values as performance metrics.
10. What factors do you think might restrict the model from achieving a high accuracy?
Ans. Being a simple multi layer perceptron is the greatest restriction as it does not have any memory that mey help the model in better prediction.
