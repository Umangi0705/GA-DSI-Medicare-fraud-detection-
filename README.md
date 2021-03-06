# Medicare Fraud Detection

Medicare is a Federal Government healthcare program that provides affordable health insurance to the elderly population and individuals with select disabilities. Unfortunately, there is a significant amount of fraud, waste, and abuse within the Medicare system that costs taxpayers billions of dollars and puts beneficiaries’ health and welfare at risk.

This Capstone project will build a Medicare Fraud Detection model to analyze data and detect the fraudulent based on the previously excluded providers and predict the fraud provider for the future. I have obtained all datasets from publicly available Medicare data from the Centers for Medicare and Medicaid Services (CMS).

## Table of Contents
- [1. Introduction](#introduction)
- [2. Problem Statement](#problem-statement)
- [3. Datasets](#Datasets)
- [4. Work flow](#Workflow)
- [5. Evaluation and Performance Metrics](#Evaluation-and-Performance-Metrics)
- [6. Executive Summary](#executive-summary)
- [7. References](#References)

### 1. Introduction <a id = 'introduction'></a>

Although no precise measure of health care fraud exists, those who exploit Federal health care programs can cost taxpayers billions of dollars while putting beneficiaries’ health and welfare at risk. The impact of these losses and risks magnifies as Medicare continues to serve a growing number of beneficiaries. According to the 2018 Medicare Trustees Report, in 2017 Medicare provided coverage to 58.4 million beneficiaries and exceeded $710 billion in total expenditures. Medicare enrollment has grown to 60.6 million as of February 2019.

There are many factors that drive the costs of healthcare and health insurance, including fraud, waste, and abuse within the healthcare system. Total healthcare spending in the United States, in 2017, was approximately $3.5 trillion, with Medicare contributing a significant portion with a total spending of $702 billion (∼20%). Using the high-end estimate of fraud percentage presented by the FBI, the amount lost from fraudulent actions would be $350 billion, with up to $70 billion from Medicare alone.

#### 1.1 Project overview

In this project, I am building a simple data Model to show the relationships among the different datasets and identify the key feature-sets for fraud detections. I have gathered multiple datasets and merged them with specific feature. Then I made different machine learning models to detect fraud pattern based on the different features such as: Service Providers, Insurance subscribers, Provider's claim counts, their drug counts etc. Finally, I evaluated my models using diffrent classification matrices.

### 2. Problem Statement <a id = 'problem-statement'></a>

Build a model using the machine learning method to detect the fraudulence Medicare claims using different modeling techniques from the CMS open datasets and other public use data.

#### 2.1 Define problem 

The objective of the healthcare system should be to provide essential care to as many patients as possible, but with frauds in healthcare system, this objective can not be adequately fulfilles. Thus, finding ways to identify the  fraudulent activity is necessary. 

CMS’s Medicare public insurance largely serving Americans 65 years and older—is estimated to dole out 6 billion dollars due to fraud every year, representing about 10% of its 60 billion dollar annual expenditures. CMS relies on it to detect and prevent fraud, waste and abuse in Part D program. But using the traditional methods, the fraud detection is conducted on random samples by human experts. The consequences are the samples might be misleading or manual detection is costly. Fraud and medical billing errors represent a huge cost in the U.S healthcare system.  Machine learning plays an innovative role in fraud detection because it can very quickly predict potential fraud cases based on past available data.

### 3. Datasets <a id = 'Datasets'></a>

In this project, I have used following Medicare data of 2017
1. Prescriber data(Part D)
2. Opioid prescriber data
3. Referring provider and their aggregated supplier data 
4. Excluded provider data
5. Physician payment data

----

1. Prescriber data(Medicare Provider Utilization and Payment Data: 2017 Part D Prescriber):

The Centers for Medicare & Medicaid Services (CMS) has prepared a public data set, the Medicare Provider Utilization and Payment Data: Part D Prescriber Public Use File (PUF), with information on prescription drugs prescribed by individual physicians and other health care providers and paid for under the Medicare Part D Prescription Drug Program.The dataset identifies providers by their National Provider Identifier (NPI) and the specific prescriptions that were dispensed at their direction, listed by brand name (if applicable) and generic name. For each prescriber and drug, the dataset includes the total number of prescriptions that were dispensed, which include original prescriptions and any refills, and the total drug cost. The total drug cost includes the ingredient cost of the medication, dispensing fees, sales tax, and any applicable administration fees and is based on the amount paid by the Part D plan, Medicare beneficiary, government subsidies, and any other third-party payers. 
 
2. Opioid prescriber data:

The Centers for Medicare & Medicaid Services (CMS) has prepared a public data set, the Medicare Part D Opioid Prescriber Summary File, which presents information on the individual opioid prescribing rates of health providers that participate in Medicare Part D program. This file is a prescriber-level data set that provides data on the number and percentage of prescription claims (includes new prescriptions and refills) for opioid drugs, and contains information on each provider’s name, specialty, state, and ZIP code.

3. Referring provider and their aggregated supplier data:

In this dataset there is an information on DMEPOS products and services provided to Medicare beneficiaries ordered by physicians and other healthcare professionals. The Referring Provider DMEPOS PUF contains data on utilization, payment (allowed amount and Medicare payment), and submitted charges organized by National Provider Identifier (NPI), Healthcare Common Procedure Coding System (HCPCS) code and supplier rental indicator.

4. Excluded providers data:

The LEIE (List of Excluded Individuals and Entities) is updated monthly with all individuals and entities who have been excluded from participation in Federal health care programs. Providers who bill Medicare, Medicaid, or other Federal health care programs must ensure that they know what individuals or entities are excluded and not bill for their services (e.g., a pharmacy should not bill Medicaid for a drug prescribed by an excluded physician nor for drugs dispensed by an excluded pharmacist)

5. Physician payment data:

Physicians in the US are required to declare all payments received from pharmaceutical companies. In addition to “payments received” basic information (ex: amount, date, type) this datasets contains many other useful data elements such as physician ownership in company, consulting fees, charity indicator, dispute status etc. The whole datasets are includes three parts: General Payment, Research Payment and Physician Ownership Details.

I cleaned all dataset and merged them with the common column NPI(National Provider Identifier) number and their Name. I collected some important data only which I was going to use in my modeling.

### 4. Work flow <a id = 'Workflow'></a>

#### 4.1 Data Preprocessing:

Fraud detection using CMS Medicare data presents several challenges. The problem is characterized by the four Vs of big data: volume, variety, velocity, and veracity. Around 10 million records released by CMS each year satisfies both high volume and velocity. Another challenge is that the positive class of interest makes up just 0.03% of all records, creating a severe class-imbalanced distribution. Learning from such distributions can be very difficult, and standard machine learning algorithms will typically over-predict the majority class.

One approach to addressing imbalanced datasets is to oversample the minority class. The simplest approach involves duplicating examples in the minority class, although these examples don’t add any new information to the model. Instead, new examples can be synthesized from the existing examples. This is a type of data augmentation for the minority class and is referred to as the Synthetic Minority Oversampling Technique, or SMOTE. I have used this oversampling method.

After oversampling my minority class I split my data into train and test.

#### 4.2 Modeling

This is a classification problem so here I used different classification models as following:
1. Logistic Regression
2. Decision Tree Classifier
3. Bagging Classifier
4. Random forest Classifier
5. KNeighbors Classifier
6. Bernoulli Naive Bayes 

As I said earlier, the dataset is highly imbalanced as there is only few amount of frauds in a big data so the standard machine learning algorithms will typically over-predict the majority class. Which would unable to make a good model for detecting a fraud so I believed that deep learning is an important area of research that will play a critical role in the future of modeling class-imbalanced big data.
Finally, I came up with Neural network from which I got improved model with good score.

### 5. Evaluation and Performance Metrics <a id = 'Evaluation and Performance Metrics'></a>

In this fraud detection problem, accuracy doesn’t work because of the imbalanced datasets.As we had 99% more non-fraudulent data and less than 1% fraud data. So if we predict all data points as a normal class, we would at least get 99% correct. This is called accuracy paradox. So to evaluate my model I will use recall and precision matrices.

Logistic model predicted around 60% correctly the fraud providers while there are around 27000 predicted non fraud providers who were actual fraud provider. Neural Network gave me only 25 false negative and for fraud detection the consequences of predicting non fraud but actually they fraud is high so I will choose Neural Network model.

### 6. Excecutive summary <a id = 'Excecutive summary'></a>

I performed various supervised learning classification models and got different scores for each of them gave me high score for my false negatives which is saying that my models are incorrectly predicting frauds which causes more problems as you predict provider is not fraud but in actual he is fraud.Neural Network search for every detail so it gave me only 25 False negative so I would choose NN model as good model for my project. As I mentioned above my dataset has highly imbalance class which was the obstacle in predicting the fraud effectively. I will continue work on this project and I will find some missing data for the excluded providers and try some other mehods. 

### References <a id = 'References'></a>

Datasets:
 
https://data.cms.gov/Medicare-Durable-Medical-Equipment-DME-/Medicare-Referring-Provider-DMEPOS-PUF-CY2017/k2nz-4k5i
https://data.cms.gov/Medicare-Part-D/Medicare-Provider-Utilization-and-Payment-Data-201/77gb-8z53 
https://oig.hhs.gov/exclusions/exclusions_list.asp 
https://www.cms.gov/Research-Statistics-Data-and-Systems/Statistics-Trends-and-Reports/Medicare-Provider-Charge-Data/OpioidMap_Medicaid_State
https://www.cms.gov/Research-Statistics-Data-and-Systems/Statistics-Trends-and-Reports/Medicare-Provider-Charge-Data/PartD2017

Other:
https://blogs.sas.com/content/hiddeninsights/2019/08/12/combating-insurance-fraud-with-machine-learning/
https://journalofbigdata.springeropen.com/articles/10.1186/s40537-019-0225-0
https://digital.hbs.edu/platform-rctom/submission/chasing-medicare-fraud-with-machine-learning/
https://pyligent.github.io/2018-08-26-CMS-Medicare-Data-Fraud-Detection/















