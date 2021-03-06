
# Operationalizing Machine Learning with Microsoft Azure

In this project I demonstrate how to operationalize a ML model in MS Azure. This process includes the steps of model creation, model deployment as well as providing an URL end-point so that the model can be accessible by end-users. I will also create a pipeline of the ML training, deploy & publish the training pipeline to an endpoint so that it can be consumed.

We can differentiate 2 endpoints in this project:
- model endpoint URL: this enables the end-users to use the trained model and make predictions with it
- pipeline endpoint URL: this enables to repeat the experiment from any platform environment

As a dataset we have a banking dataset available, which includes client data from a marketing campaign including age, job, education and other attributes as well as the information whether the client is subscribed to the certain bank product. The information on the subscription (yes or no) is our target variable: the task of our ML model will be make a prediction whether a new client will subscribe to the specific bank product or not.



## Architectural Diagram
Here is an architectual diagram of the project visualizing the flow of operations from start to finish. 
<img width="386" alt="architectural_diagram" src="https://user-images.githubusercontent.com/4347923/108600683-c27b0f00-7398-11eb-93f2-d48993fabb10.PNG">

## Key Steps


### 1. Create the Auto ML run: 
This step includes the dataset selection, the setting of the target variable and the configuration of the compute cluster, which was used to run the experiment. I used a CPU virtual machine with a size of 4 cores, 28 GB RAM and 56 GB storage (type: Standrad_DS12_v2). I was also able to set the minimum and maximum number of nodes used. In addition to the that, I set the training job time to 1 hour as exit criterion and the max concurrent iterations to 5.

Select dataset:
<img width="959" alt="udacity_1_bank_data_available" src="https://user-images.githubusercontent.com/4347923/108600587-38cb4180-7398-11eb-93d6-5b15c9215ae2.PNG">

Configuring the Auto ML run:
<img width="912" alt="udacity_2_configure_automl" src="https://user-images.githubusercontent.com/4347923/108600594-3d8ff580-7398-11eb-8273-0c5da9196cff.PNG">
<img width="914" alt="udacity_3_configure_cluster" src="https://user-images.githubusercontent.com/4347923/108600595-3ff24f80-7398-11eb-88bb-9122beb05bef.PNG">
<img width="941" alt="udacity_4_configure_cluster2" src="https://user-images.githubusercontent.com/4347923/108600597-42ed4000-7398-11eb-9e3c-3c82d04a83d2.PNG">
<img width="950" alt="udacity_5_ML_model_config" src="https://user-images.githubusercontent.com/4347923/108600602-4bde1180-7398-11eb-937a-0ab42e2ca810.PNG">

The experiment is shown in running state:

<img width="636" alt="udacity _new_1_running_experiment_overview1" src="https://user-images.githubusercontent.com/4347923/108754346-1bd47100-7546-11eb-97b1-911b8a6447f9.PNG">
<img width="633" alt="udacity _new_2_running_experiment_details2" src="https://user-images.githubusercontent.com/4347923/108754349-1d9e3480-7546-11eb-9ed0-eb08a91f8709.PNG">

The experiment is shown as being completed:
<img width="881" alt="udacity_7_experiment_completed" src="https://user-images.githubusercontent.com/4347923/108600614-54364c80-7398-11eb-9a99-688729791f9a.PNG">

<img width="629" alt="udacity _new_3_completed_experiment" src="https://user-images.githubusercontent.com/4347923/108754358-1ecf6180-7546-11eb-9e99-734fd4318b9d.PNG">

<img width="634" alt="udacity _new_5_completed_experiment_with_all_models" src="https://user-images.githubusercontent.com/4347923/108754374-22fb7f00-7546-11eb-9b17-ebfb82d78b1f.PNG">


### 2. Select the best model & deploy:
After the completion of the Auto ML run, I selected the model with the highest accuracy as best model. This model was based on the algorithm "VotingEnsemble" and reached an accuracy of 91.92%.

<img width="617" alt="udacity _new_4_completed_experiment_with_best_model" src="https://user-images.githubusercontent.com/4347923/108754365-2131bb80-7546-11eb-9e39-24768f9f57fc.PNG">

<img width="869" alt="udacity_10_model_deployed" src="https://user-images.githubusercontent.com/4347923/108600623-60220e80-7398-11eb-839a-ba0f848b691a.PNG">

### 3. Enabling application insights: 
I downloaded the config.json file, which can be found under the subscription details.  After this step I changed the name of the model name in the logs.py file as well as set the value of enable_application_insights to True. After it is done, I ran the the logs.py file. 

<img width="356" alt="udacity_11_creating_logspy_for_enabling_insights" src="https://user-images.githubusercontent.com/4347923/108600624-63b59580-7398-11eb-8157-7eeafdbac19a.PNG">

Running the python file logs.py, logs are initialized:

<img width="641" alt="udacity_logs_run" src="https://user-images.githubusercontent.com/4347923/110251588-72e43800-7f81-11eb-8c57-fbb2bf9f1d52.PNG">

Application insights enabled is shown in the MS ML Studio:
<img width="617" alt="udacity _new_6_model_deployed_insights_enabled" src="https://user-images.githubusercontent.com/4347923/108754391-2989f680-7546-11eb-898c-5ae8dd7867cf.PNG">

<img width="584" alt="udacity_13_app_insights" src="https://user-images.githubusercontent.com/4347923/108600633-69ab7680-7398-11eb-924b-7b77a858ab64.PNG">


### 4. Setup swagger documentation
I used Swagger to document and consume the deploy model with APIs in get & post HTTP requests. To setup swagger I ran the serve.py script and swagger.sh in port 8000. 
After this step I was able to interact with the swagger instance and see its response from localhost.

<img width="630" alt="udacity_14_swagger_localhost" src="https://user-images.githubusercontent.com/4347923/108600636-6ca66700-7398-11eb-901e-66977155d458.PNG">
<img width="626" alt="udacity_15_swagger_interaction" src="https://user-images.githubusercontent.com/4347923/108600641-7203b180-7398-11eb-94fd-82c06e7a8094.PNG">
<img width="608" alt="udacity_15_swagger_interaction2" src="https://user-images.githubusercontent.com/4347923/108600643-7af48300-7398-11eb-878f-1ca04c3f1aeb.PNG">

### 5. Consume the end-point

<img width="306" alt="udacity_16_endpointpy_after_editing_URLandkey" src="https://user-images.githubusercontent.com/4347923/108600645-7def7380-7398-11eb-9ad5-6bcd98040cfd.PNG">
<img width="268" alt="udacity_16_endpointpy_runs_against _the_API" src="https://user-images.githubusercontent.com/4347923/108600646-847deb00-7398-11eb-8ec1-1ec052c6c3df.PNG">

### 6. Create a pipeline

Running the sample notebook the pipeline has been created.

<img width="642" alt="udacity _new_8_pipeline_created" src="https://user-images.githubusercontent.com/4347923/108754408-2e4eaa80-7546-11eb-9ae7-e510aa093554.PNG">

The pipeline in running status in the notebook:
<img width="570" alt="udacity _new_9_pipeline_running" src="https://user-images.githubusercontent.com/4347923/108754424-31e23180-7546-11eb-8245-8ec1ed021f53.PNG">

The pipeline is completed - we can also see the child runs listed:
<img width="624" alt="udacity _new_9_pipeline_completed" src="https://user-images.githubusercontent.com/4347923/108754413-2f7fd780-7546-11eb-8147-f54c3c5d0636.PNG">
<img width="638" alt="udacity _new_10_pipeline_completed_child_runs" src="https://user-images.githubusercontent.com/4347923/108754438-36a6e580-7546-11eb-8327-9f514d7a54c6.PNG">

### 7. Consume the pipeline

After the training run is completed, we deployed the pipeline.
The deployed pipeline generated a pipeline endepoint.

<img width="624" alt="udacity _new_12_published_pipelines_endpoint_active" src="https://user-images.githubusercontent.com/4347923/108754458-3d355d00-7546-11eb-8b10-78dce0b59497.PNG">

8. Publish the pipeline

The published pipeline has now a REST URL for accessing the model by other end-users.

<img width="636" alt="udacity _new_11_published_pipelines" src="https://user-images.githubusercontent.com/4347923/108754446-39a1d600-7546-11eb-9cc2-695c5f6d18f7.PNG">


## Screen Recording

Under the following link you can find the screen recording about the project:
https://youtu.be/lrYkXD4cF4s

## Further improvement possibilities for the project

- Handling the imbalance dataset: The dataset was an imbalanced dataset as it was recognised during the AutoML run. By using some further data preparation techniques we could further improve our model by reducing the bias for a certain class.

- Experiment with deep learning algorithms to improve the model performance

- Use of GPU resources for accelerating the training time


