# Black box AI models explained using Cortex Certifai

Trust is the foundation of digital systems. Without trust, AI cannot deliver on its potential value. However, machine learning models often function inside black-boxes. This has resulted in significant business risks that hampers Enterprise AI adoption. Cortex Certifai detects and scores 6 dimensions of AI business risk: performance, bias/fairness, explainability, robustness, compliance, and data drift. Cortex Certifai evaluates AI models for robustness, fairness, and explainability, and allows users to compare different models or model versions for these qualities.

Certifai is available in three Editions:

Certifai Toolkit		
Everything you need to create, run, and view scans locally. 

Certifai Pro
Single-user deployment running in a cloud-hosted VM	

Certifai Enterprise
Multi-user server deployment running in Kubernetes, plus the Certifai AI Risk Assessment Questionnaire and Policy Select compliance toolset. 

This code pattern demonstrates how to use Certifai Toolkit for creating scans to evaluate the performance of multiple predictive models.

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

Flow:

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



