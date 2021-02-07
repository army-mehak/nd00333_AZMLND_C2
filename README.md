# Operationalizing Machine Learning
The aim of the project is to perform deployment of a model that can be consumed by other application. In this project, a bank marketing dataset was trained using AutoML and then deployed. The deployment was performed using HTTP Endpoint. The last part of the project consisted of creating pipelines and publishing it.

## Architectural Diagram
The main parts of the Operationalizing machine learning model includes training model, deploying the model, creating & publishing pipeline and consuming pipeline.

### Model training and deployment included of the following steps:
![alt text](https://github.com/army-mehak/nd00333_AZMLND_C2/blob/master/img/Model.png)
<p align="center">
 Figure 1: Model Training & Deployment Architectural Diagram
</p>

  1. Created a compute cluster (compute-cluster1) using Standard_DS12_v2 as a default cluster. Along with that, exit criterion was set 1 training hour and concurrency to 5.
  2. Uploaded the dataset for Bank-marketing using the link provided. It was named 'bank-marketing'.
  3. Created an AutoML run using the compute cluster and the dataset that performed Classification. The best model found was Voting Ensemble.
  4. The best model was then deployed using Azure Container Instance.
  5. Authentication key and HTTP endpoint was created.
  6. The Rest Endpoint URI and Primary key can be retrieved from ML studio.
  7. The endpoint.py is ran with the scoring uri and primary key to interact with the HTTP endpoint URI.
  8. The HTTP endpoint responds back with JSON data.


### Creating, Publishing & Consuming pipeline included of the following steps:
![alt text](https://github.com/army-mehak/nd00333_AZMLND_C2/blob/master/img/pipeline.png)
<p align="center">
 Figure 2: Creating, Publishing & Consuming pipeline Architectural Diagram
</p>

  1. A compute target called 'compute-target1' was created to run the jupyter notebook and as well as to training the AutoML step.
  2. Next, using the existing bank-marketing dataset if found or else creating a dataset from the URL.
  3. An automl step was creating and fed in the required configuration which had the label column as 'y'.
  4. The automl_step was then fed into a pipeline configuration.
  5. The pipeline was then submitted.
  6. A HTTP Endpoint URI was created. This can be used to trigger new pipeline runs.
  7. Pipeline consumption requires an authentication header to submit a POST request to HTTP endpoint. A new pipeline run gets created through the trigger of post request.

## Key Steps
The following are the key steps involved along with some screenshots:

### Model Training
The first thing in any machine learning project is to upload and register the dataset. The Bank Marketing dataset was uploaded and registered through Azure ML Studio. The Figure 3 shows how the dataset was uploaded successfully. 

![alt text](https://github.com/army-mehak/nd00333_AZMLND_C2/blob/master/img/s1.PNG)
<p align="center">
 Figure 3: 'bank-marketing' dataset uploaded successfully
</p>
After completing the dataset, an AutoML run was created to classify the bank marketing dataset. Figure 4 shows that AutoML ran successfully.

![alt text](https://github.com/army-mehak/nd00333_AZMLND_C2/blob/master/img/s2.PNG)
<p align="center">
 Figure 4: AutoML experiment ran successfully
</p>
The AutoML experiment ran many algorithms with different combination of hyperparamaters. The best model found was Voting Ensemble with ___ %. Figure 5 and 6 highlights the best model.

![alt text](https://github.com/army-mehak/nd00333_AZMLND_C2/blob/master/img/s3-1.PNG)
<p align="center">
 Figure 5: Best model - Voting Ensemble
</p>

![alt text](https://github.com/army-mehak/nd00333_AZMLND_C2/blob/master/img/s3-2.PNG)
<p align="center">
 Figure 6: Best model - Voting Ensemble
</p>

### Deploying Model
Voting Ensemble being the best model was deployed thrugh Azure ML Studio. Azure Container Instance was used and autentication ws enabled. Through terminal, Application Insight was enabled by running the logs.py. Figure 7 shows the output after running the logs.py file. The application was enabled and can be seen through Azure ML studio (Figure 8).

![alt text](https://github.com/army-mehak/nd00333_AZMLND_C2/blob/master/img/s4.PNG)
<p align="center">
 Figure 7:  Application Insight enabled
</p>

![alt text](https://github.com/army-mehak/nd00333_AZMLND_C2/blob/master/img/s5.PNG)
<p align="center">
 Figure 8: Log of logs.py file
</p>


## Screen Recording
The video can be found here -> https://www.youtube.com/watch?hd=1&v=NI3SbTBsVFU

## Future Work
This project can be further built into a web application where external application could interact using API provided along with key. This project can be further deep dived and implemented ro cater multiple applications.
