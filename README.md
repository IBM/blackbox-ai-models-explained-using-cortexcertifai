# WARNING: This repository is no longer maintained

> This repository will not be updated. The repository will be kept available in read-only mode.

# Black box AI models explained using Cortex Certifai

Explainability of AI models is a difficult task which is made simpler by Cortex Certifai. It evaluates AI models for robustness, fairness, and explainability, and allows users to compare different models or model versions for these qualities. Certifai can be applied to any black-box model including machine learning models, predictive models and works with a variety of input datasets.

# How does Certifai work?

Data Scientists can create model scan definitions, which are comprised of trained models that they want to evaluate for the parameters listed below. 

**Performance Metric:** (e.g. Accuracy)

**Robustness:** How the model generalizes on new data.

**Fairness by group:** measures the bias in the data. 

**Explainability:** measures the explanations provided for each model. 

**Explanations:** display the change that must occur in a dataset with given restrictions to obtain a different outcome. 

Business decision makers are able to view the evaluation comparison through visualizations and scores to select the best models for business goals and to identify whether or not models meet thresholds for robustness, fairness, and/or explainability. Data Scientists can use the evaluation results for analysis to provide more trustworthy AI models. 

This code pattern demonstrates how to use Certifai Toolkit for creating scans to evaluate the performance of multiple predictive models using IBM Watson Studio platform.

# Architecture Diagram

![](https://github.com/IBM/blackbox-ai-models-explained-using-cortexcertifai/blob/main/images/architecture.png)

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

**Download Certifai Toolkit**

Toolkit Edition: You can signup for free use of the Certifai Toolkit on the [CognitiveScale website](https://www.cognitivescale.com/download-certifai/). A download link will be provided in the confirmation email.

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

![](https://github.com/IBM/blackbox-ai-models-explained-using-cortexcertifai/blob/main/images/create_prj.png)

Define the project by giving a Name and hit 'Create'.

![](https://github.com/IBM/blackbox-ai-models-explained-using-cortexcertifai/blob/main/images/def_prj.png)

## 3. Add Data

[Clone this repo](https://github.com/IBM/blackbox-ai-models-explained-using-cortexcertifai)
Navigate to [data/assets](https://github.com/IBM/blackbox-ai-models-explained-using-cortexcertifai/tree/main/data/assets) and save the file by name `german_credit_eval.csv` on the disk. The dataset will be available under the Certifai toolkit which was downloaded in the previous step.

Click on Assets and select Browse and add the csv file from your file system.

![](https://github.com/IBM/blackbox-ai-models-explained-using-cortexcertifai/blob/main/images/add_asset.png)

## 4. Create the notebook

* Open [IBM Watson Studio](https://dataplatform.ibm.com).
* Go to the project and click on Add 
* Click on `Create notebook` to create a notebook.
* Select the `From URL` tab.
* Enter a name for the notebook.
* Optionally, enter a description for the notebook.
* Enter this Notebook URL : https://github.com/IBM/blackbox-ai-models-explained-using-cortexcertifai/blob/main/notebooks/WS_classifier.ipynb
* Select the runtime (8 vCPU and 32GB RAM)
* Click the `Create` button.

After the notebook is imported, click on `Not Trusted` and select the option as Yes to trust the source of the notebook.

![](https://github.com/IBM/blackbox-ai-models-explained-using-cortexcertifai/blob/main/images/not_trusted.png)

`This notebook has been created to demonstrate the steps for building the model using Watson Studio platform. For other usecases, the notebook has to be created from scratch.`

## 5. Insert the data as dataframe

Click on 0010 icon at the top right side which will bring up the data assets tab.

![](https://github.com/IBM/blackbox-ai-models-explained-using-cortexcertifai/blob/main/images/add.png)

Click on Insert to code dropdown and select the option Insert Pandas Dataframe.

![](https://github.com/IBM/blackbox-ai-models-explained-using-cortexcertifai/blob/main/images/insert_dataframe.png)

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

After we run all cells in the notebook, the scan results are uploaded onto object storage which can be downloaded by following these steps. Login to [IBM Cloud](https://cloud.ibm.com/), navigate to `Dashboard` on the left hand side and click on `Storage`. Click on the bucket name which is an extension of the project name in Watson Studio and select the `scan_results.csv` file for downloading it.

Cloud Object Storage
![](https://github.com/IBM/blackbox-ai-models-explained-using-cortexcertifai/blob/main/images/cos.png)

Download results file
![](https://github.com/IBM/blackbox-ai-models-explained-using-cortexcertifai/blob/main/images/dwn_scan_results.png)

View results file
![](https://github.com/IBM/blackbox-ai-models-explained-using-cortexcertifai/blob/main/images/scan_results.png)


## How to run the scan locally using CLI

* Create a folder in your local file system, [Download this repo](https://github.com/IBM/blackbox-ai-models-explained-using-cortexcertifai) into the folder and unzip it. 
* `Please make sure that you have installed Python version 3.6 or higher.`
* Open a command prompt, CD into the subfolder of notebooks and type `Jupyter Notebook`. When the notebook is launched, select the notebook by name `regressor.ipynb` and run all the cells using top down approach. 
* After we run the cells, the scan is complete and results are stored in the current directory of the notebook under `reports` folder. 
* Open a new command prompt, CD into the `reports` folder and type the command `certifai console reports`. This will start the flask server and the UI is ready for review.
* Launch the UI at http://localhost:8000/ and the scan reports along with comparitive analysis are ready for review and analysis.

### Scan results for Classification usecase - Predict Fraud

![](https://github.com/IBM/blackbox-ai-models-explained-using-cortexcertifai/blob/main/images/scan_results_c.png)

**Comparative analysis**
![](https://github.com/IBM/blackbox-ai-models-explained-using-cortexcertifai/blob/main/images/scan_details_c.png)


### Scan results for Regression usecase - Predict Customer spend

![](https://github.com/IBM/blackbox-ai-models-explained-using-cortexcertifai/blob/main/images/scan_res_r.png)

**Comparative analysis**
![](https://github.com/IBM/blackbox-ai-models-explained-using-cortexcertifai/blob/main/images/scan_details_r.png)

**Note :** The scan results are dependent on the input dataset. If we change the input data, the scan results change accordingly. 

As per business requirement, we can choose the best model for production deployment. The scan result files in csv format are also available for review under [certifai-scan-results folder](https://github.com/IBM/blackbox-ai-models-explained-using-cortexcertifai/tree/main/certifai-scan-results).

This code pattern will be very helpful for developers, machine learning engineers, data scientists, architects to compare multiple models and evaluate under different criteria to select the best model as per their requirement. We can also run remote scans from Red Hat Open Shift cluster provided there is a storage allocated from Amazon S3, GCP or Azure.

## Related Links :

[Click here to know about Cortex Certifai](https://www.cognitivescale.com/certifai/)

[Click here for additional information](https://cognitivescale.github.io/cortex-certifai/docs/quickstart#best-practices-for-new-toolkit-users)

# Troubleshooting

[See DEBUGGING.md.](DEBUGGING.md)

# License

This code pattern is licensed under the Apache Software License, Version 2.  Separate third party code objects invoked within this code pattern are licensed by their respective providers pursuant to their own separate licenses. Contributions are subject to the Developer [Certificate of Origin, Version 1.1 (DCO)](https://developercertificate.org/) and the [Apache Software License, Version 2](http://www.apache.org/licenses/LICENSE-2.0.txt).

Check the [ASL FAQ link](http://www.apache.org/foundation/license-faq.html#WhatDoesItMEAN) for more details
