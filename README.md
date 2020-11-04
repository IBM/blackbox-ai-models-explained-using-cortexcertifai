# Black box AI models explained using Cortex Certifai

Trust is the foundation of digital systems. Without trust, AI cannot deliver on its potential value. However, machine learning models often function inside black-boxes. This has resulted in significant business risks that hampers Enterprise AI adoption. Cortex Certifai detects and scores 6 dimensions of AI business risk: performance, bias/fairness, explainability, robustness, compliance, and data drift. Cortex Certifai evaluates AI models for robustness, fairness, and explainability, and allows users to compare different models or model versions for these qualities.

Cortex Certifai generates the first-ever composite trust score, the AI Trust Index, that measures data and model risks related to Performance, Data Quality, Robustness, Explainability, Fairness, and Compliance. Certifai can be applied to any black-box model including machine learning models, statistical models, business rules, and other predictive models and works with a variety of input data.

Certifai is available in three Editions:

Certifai Toolkit		
Everything you need to create, run, and view scans locally. 

Certifai Pro
Single-user deployment running in a cloud-hosted VM	

Certifai Enterprise
Multi-user server deployment running in Kubernetes, plus the Certifai AI Risk Assessment Questionnaire and Policy Select compliance toolset. 

This code pattern demonstrates how to use Certifai Toolkit for creating scans to evaluate the performance of multiple predictive models using IBM Watson Studio platform.

# How does Certifai work?

Data Scientists create scan definitions, which are comprised of:

One or more trained models that they want to evaluate
A single curated dataset (NOTE: For explanations a subset of the dataset may be used.)
Models are evaluated/scored for one or more of the following:

**Performance Metric:** This is a measurement that the data scientist has provided test data to calculate or pre-calculated scores for in the model definition. (e.g. Accuracy)

**Robustness:** measures how well models retain an outcome given changes to the data feature values. The more robust a model is, the greater the changes required to alter the outcome.

**Fairness by group:** measures the difference required to change the outcome for different groups implicit in a feature given the same model and dataset. For example, implicit groups male, female, and nonbinary belong to the feature, "gender". A fair model shows that all 3 groups require a similar amount of change to alter the results.

**Explainability:** measures the average simplicity of counterfactual explanations provided for each model. An explanation that requires a single changed feature will score 100%. Explanations that require more changed features will score lower.

**Explanations:** display the prediction provided through the generation of counterfactuals for the change that must occur in a dataset with given restrictions to obtain a different outcome. To alter an outcome some dataset feature values must change while others remain constant. Each observation row of the dataset is displayed in a table that shows the changed features, as well as the original values and counterfactual values for that feature. Users can explore the entire dataset one observation at a time to understand what features changed and by how much to obtain a different result.

Business decision makers and Compliance Officers are able to view the evaluation comparison visualizations and scores to select the best models for business goals and to identify whether or not models meet thresholds for robustness, fairness, and/or explainability.

Data Scientists can use the evaluation results to improve models and model training to provide more trustworthy AI models.

# Architecture Diagram

![](https://github.com/IBM/predict-fraud-using-auto-ai/blob/master/images/architecture.png)

1. Log in to Watson Studio powered by spark, initiate Cloud Object Storage, and  create a project.
2. Upload the .csv data file to Object Storage.
3. Load the Data File in Watson Studio Notebook.
4. Install Cortex Certifai Toolkit in the Watson Studio Notebook.
5. Visualization for explainability and interpretability of AI Model for the three different types of Users.

## Included components

* [IBM Watson Studio](https://www.ibm.com/cloud/watson-studio): Analyze data using RStudio, Jupyter, and Python in a configured, collaborative environment that includes IBM value-adds, such as managed Spark.

* [IBM Cloud Object Storage](https://console.bluemix.net/catalog/services/cloud-object-storage): An IBM Cloud service that provides an unstructured cloud data store to build and deliver cost effective apps and services with high reliability and fast speed to market. This code pattern uses Cloud Object Storage.


## Featured technologies

* [Artificial Intelligence](https://developer.ibm.com/technologies/artificial-intelligence/): Any system which can mimic cognitive functions that humans associate with the human mind, such as learning and problem solving.
* [Data Science](https://developer.ibm.com/code/technologies/data-science/): Systems and scientific methods to analyze structured and unstructured data in order to extract knowledge and insights.
* [Analytics](https://developer.ibm.com/code/technologies/analytics/): Analytics delivers the value of data for the enterprise.
* [Python](https://www.python.org/): Python is a programming language that lets you work more quickly and integrate your systems more effectively.

We can run the scan using Cortex Certifai using Watson Studio and command line interface. This code pattern demonstrates how to run the scan using Watson studio on two different machine learning techniques, Regression & Classification. 


# Steps using Cortex Certifai on Watson Studio


1. [Create an account with IBM Cloud](#1-create-an-account-with-ibm-cloud)
1. [Create a new Watson Studio project](#2-create-a-new-watson-studio-project)
1. [Add Data](#3-add-data)
1. [Create the notebook](#4-create-the-notebook)
1. [Insert the data as dataframe](#5-insert-the-data-as-dataframe)
1. [Run the notebook](#6-run-the-notebook)
1. [Analyze the results](#7-analyze-the-results)

## 1. Create an account with IBM Cloud

Sign up for IBM [**Cloud**](https://console.bluemix.net/). By clicking on create a free account you will get 30 days trial account.

## 2. Create a new Watson Studio project

Sign up for IBM's [Watson Studio](http://dataplatform.ibm.com/). 

Click on New Project and select per below.

![](https://github.com/IBM/predict-fraud-using-auto-ai/blob/master/images/create_prj.png)

Define the project by giving a Name and hit 'Create'.

![](https://github.com/IBM/predict-fraud-using-auto-ai/blob/master/images/def_prj.png)

## 3. Add Data

[Clone this repo](https://github.com/IBM/blackbox-ai-models-explained-using-cortexcertifai)
Navigate to [data](https://github.com/IBM/predict-fraud-using-auto-ai/tree/master/data) and save the file on the disk. Review the data glossary from the data folder for more details. `Note: Citation is needed to use this dataset for any other projects.` 

Click on Assets and select Browse and add the csv file from your file system.

![](https://github.com/IBM/predict-fraud-using-auto-ai/blob/master/images/add_asset.png)

## 4. Create the notebook

* Open [IBM Watson Studio](https://dataplatform.ibm.com).
* Go to the project and click on Add 
* Click on `Create notebook` to create a notebook.
* Select the `From URL` tab.
* Enter a name for the notebook.
* Optionally, enter a description for the notebook.
* Enter this Notebook URL for Classification : 
* Enter this Notebook URL for Regression : 
* Select the runtime (8 vCPU and 32GB RAM)
* Click the `Create` button.

After the notebook is imported, click on `Not Trusted` and select the option as Yes to trust the source of the notebook.

![](https://github.com/IBM/predict-fraud-using-auto-ai/blob/master/images/not_trusted.png)

`This notebook has been created to demonstrate the steps for building the model using Watson Studio platform. For other usecases, the notebook has to be created from scratch.`

## 5. Insert the data as dataframe

Click on 0010 icon at the top right side which will bring up the data assets tab.

![](https://github.com/IBM/predict-fraud-using-auto-ai/blob/master/images/add.png)

Click on Insert to code dropdown and select the option Insert Pandas Dataframe.

![](https://github.com/IBM/predict-fraud-using-auto-ai/blob/master/images/insert_dataframe.png)

## 6. Run the notebook

When a notebook is executed, what is actually happening is that each code cell in
the notebook is executed, in order, from top to bottom.

Each code cell is selectable and is preceded by a tag in the left margin. The tag
format is `In [x]:`. Depending on the state of the notebook, the `x` can be:

* A blank, this indicates that the cell has never been executed.
* A number, this number represents the relative order this code step was executed.
* A `*`, this indicates that the cell is currently executing.

There are several ways to execute the code cells in your notebook:

* One cell at a time.
  * Select the cell, and then press the `Play` button in the toolbar.
* Batch mode, in sequential order.
  * From the `Cell` menu bar, there are several options available. For example, you
    can `Run All` cells in your notebook, or you can `Run All Below`, that will
    start executing from the first cell under the currently selected cell, and then
    continue executing all cells that follow.

## 7. Analyze the results


