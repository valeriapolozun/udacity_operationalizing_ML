
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


2. Select the best model & deploy: After the completion of the Auto ML run, I selected the model with the highest accuracy as best model. This model was based on the algorithm "VotingEnsemble" and reached an accuracy of 92.018%.

3. Enabling application insights: I downloaded the config.json file, which can be found under the subscription details.  After this step I changed the name of the model name in the logs.py file as well as set the value of enable_application_insights to True. After it is done, I ran the the logs.py file. 

4. Setup swagger documentation

5. Consume the end-point

6. Create a pipeline

7. Consume the pipeline

8. Publish the pipeline



## Screen Recording
*TODO* Provide a link to a screen recording of the project in action. Remember that the screencast should demonstrate:

## Standout Suggestions
*TODO (Optional):* This is where you can provide information about any standout suggestions that you have attempted.
