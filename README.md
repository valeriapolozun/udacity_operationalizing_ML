
# Operationalizing Machine Learning with Microsoft Azure

In this project I demonstrate how to operationalize a ML model in MS Azure. This process includes the steps of model creation, model deployment as well as providing an URL end-point so that the model can be accessible by end-users.

## Architectural Diagram
Here is an architectual diagram of the project visualizing the flow of operations from start to finish. 



1. Create the Auto ML run: this step includes the dataset selection, the setting of the target variable and the configuration of the compute cluster, which was used to run the experiment. I used a CPU virtual machine with a size of 4 cores, 28 GB RAM and 56 GB storage (type: Standrad_DS12_v2). I was also able to set the minimum and maximum number of nodes used. In addition to the that, I set the training job time to 1 hour as exit criterion and the max concurrent iterations to 5.

2. Select the best model: After the completion of the Auto ML run, I selected the model with the highest accuracy as best model. This model was based on the algorithm "VotingEnsemble" and reached an accuracy of 92.018%.




## Key Steps
*TODO*: Write a short discription of the key steps. Remeber to include all the screenshots required to demonstrate key steps. 

## Screen Recording
*TODO* Provide a link to a screen recording of the project in action. Remember that the screencast should demonstrate:

## Standout Suggestions
*TODO (Optional):* This is where you can provide information about any standout suggestions that you have attempted.
