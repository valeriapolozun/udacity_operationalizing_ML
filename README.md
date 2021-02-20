
# Operationalizing Machine Learning with Microsoft Azure

In this project I demonstrate how to operationalize a ML model in MS Azure. This process includes the steps of model creation, model deployment as well as providing an URL end-point so that the model can be accessible by end-users.

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
<img width="946" alt="udacity_6_ML_running" src="https://user-images.githubusercontent.com/4347923/108600606-4f719880-7398-11eb-95df-f5a561da4460.PNG">


### 2. Select the best model & deploy:
After the completion of the Auto ML run, I selected the model with the highest accuracy as best model. This model was based on the algorithm "VotingEnsemble" and reached an accuracy of 92.018%.

<img width="881" alt="udacity_7_experiment_completed" src="https://user-images.githubusercontent.com/4347923/108600614-54364c80-7398-11eb-9a99-688729791f9a.PNG">
<img width="902" alt="udacity_8_choosing_best_model" src="https://user-images.githubusercontent.com/4347923/108600617-58626a00-7398-11eb-9286-1098a4cb57d7.PNG">
<img width="533" alt="udacity_9_best_model_votingensemble" src="https://user-images.githubusercontent.com/4347923/108600619-5d271e00-7398-11eb-9842-86ff8cb3bd65.PNG">
<img width="869" alt="udacity_10_model_deployed" src="https://user-images.githubusercontent.com/4347923/108600623-60220e80-7398-11eb-839a-ba0f848b691a.PNG">

### 3. Enabling application insights: 
I downloaded the config.json file, which can be found under the subscription details.  After this step I changed the name of the model name in the logs.py file as well as set the value of enable_application_insights to True. After it is done, I ran the the logs.py file. 

<img width="356" alt="udacity_11_creating_logspy_for_enabling_insights" src="https://user-images.githubusercontent.com/4347923/108600624-63b59580-7398-11eb-8157-7eeafdbac19a.PNG">
<img width="609" alt="udacity_12_running_logspy" src="https://user-images.githubusercontent.com/4347923/108600628-66b08600-7398-11eb-8f91-2a709d8ec844.PNG">
<img width="584" alt="udacity_13_app_insights" src="https://user-images.githubusercontent.com/4347923/108600633-69ab7680-7398-11eb-924b-7b77a858ab64.PNG">

### 4. Setup swagger documentation
I used Swagger to document and consume the deploy model with APIs in get & post HTTP requests. To setup swagger I ran the serve.py script and swagger.sh in port 8000. 
After this step I was able to interact with the swagger instance and see its response from localhost.

<img width="630" alt="udacity_14_swagger_localhost" src="https://user-images.githubusercontent.com/4347923/108600636-6ca66700-7398-11eb-901e-66977155d458.PNG">
<img width="626" alt="udacity_15_swagger_interaction" src="https://user-images.githubusercontent.com/4347923/108600641-7203b180-7398-11eb-94fd-82c06e7a8094.PNG">
<img width="608" alt="udacity_15_swagger_interaction2" src="https://user-images.githubusercontent.com/4347923/108600643-7af48300-7398-11eb-878f-1ca04c3f1aeb.PNG">

5. Consume the end-point

<img width="306" alt="udacity_16_endpointpy_after_editing_URLandkey" src="https://user-images.githubusercontent.com/4347923/108600645-7def7380-7398-11eb-9ad5-6bcd98040cfd.PNG">
<img width="268" alt="udacity_16_endpointpy_runs_against _the_API" src="https://user-images.githubusercontent.com/4347923/108600646-847deb00-7398-11eb-8ec1-1ec052c6c3df.PNG">

6. Create a pipeline

Running the sample notebook the pipeline has been created.

<img width="638" alt="udacity_17_pipeline_created" src="https://user-images.githubusercontent.com/4347923/108600647-8647ae80-7398-11eb-84a7-7e5c04526deb.PNG">

<img width="552" alt="udacity_18_pipeline_running_details" src="https://user-images.githubusercontent.com/4347923/108600649-86e04500-7398-11eb-80db-27cd33d2c0f2.PNG">


7. Consume the pipeline

The deployed pipeline generated an end-point for consuming.

8. Publish the pipeline

The published pipeline has a REST URL for accessing the model by other end-users.

## Screen Recording



## Standout Suggestions

The dataset was an imbalanced dataset as it was recognised during the AutoML run. By using some further data preparation techniques we could improve our model by reducing the bias for a certain class.




