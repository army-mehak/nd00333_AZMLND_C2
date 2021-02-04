# Operationalizing Machine Learning
The aim of the project is to perform deployment of a model that can be consumed by other application. In this project, a bank marketing dataset was trained using AutoML and then deployed. The deployment was performed using HTTP Endpoint. The last part of the project consisted of creating pipelines and publishing it.

## Architectural Diagram
The main parts of the Operationalizing machine learning model includes training model, deploying the model, creating & publishing pipeline and consuming pipeline.
### Model training and deployment included of the following steps:
  1. Created a compute cluster (compute-cluster1) using Standard_DS12_v2 as a default cluster. Along with that, exit criterion was set 1 training hour and concurrency to 5.
  2. Uploaded the dataset for Bank-marketing using the link provided. It was named 'bank-marketing'.
  3. Created an AutoML run using the compute cluster and the dataset that performed Classification. The best model found was Voting Ensemble.
  4. The best model was then deployed using Azure Container Instance.
  5. Authentication key and HTTP endpoint was created. 
  6. The Rest Endpoint URI and Primary key can be retrieved from ML studio.
  7. The endpoint.py is ran with the scoring uri and primary key to interact with the HTTP endpoint URI.
  8. The HTTP endpoint responds back with JSON data.

### Creating, Publishing & Consuming pipeline included of the following steps:
  1. A compute target called 'compute-target1' was created to run the jupyter notebook and as well as to training the AutoML step.
  2. Next, using the existing bank-marketing dataset if found or else creating a dataset from the URL.
  3. An automl step was creating and fed in the required configuration which had the label column as 'y'.
  4. The automl_step was then fed into a pipeline configuration. 
  5. The pipeline was then submitted.
  6. A HTTP Endpoint URI was created. This can be used to trigger new pipeline runs.
  7. Pipeline consumption requires an authentication header to submit a POST request to HTTP endpoint. A new pipeline run gets created through the trigger of post request.

## Key Steps
*TODO*: Write a short discription of the key steps. Remeber to include all the screenshots required to demonstrate key steps.

## Screen Recording
*TODO* Provide a link to a screen recording of the project in action. Remember that the screencast should demonstrate:

## Standout Suggestions
*TODO (Optional):* This is where you can provide information about any standout suggestions that you have attempted.
