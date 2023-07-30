### 1. Multi-Label classification with Natural Language Processing and Azure Machine Learning 

#### The Business Requirements: 
The request to develop Machine Learning model came from the company that built a data pipeline in the Microsoft Azure and had to take a list of diagnosis from MS SQL Server as an input and generate a set of labels as output. The output had to be deployed as a REST API Endpoint that would be used by MS Azure Factory which sent a diagnosis and received the list of labels back. The labels could be  further used to trigger certain actions, e.g.  schedule an appointment, generate a receipt, define a treatment, etc. 

#### The Solution Design: 
Since the inbound diagnosis came in the text format and were very short, I used CountVectorizer from sklearn library to tokenize input string and PorterStemmer from NLTK library to preprocess and normalize the input text.
I experimented with a few models and decided to proceed with Multi-layer Perceptron (MLP) neural network  that was able to produce multiple labels as a prediction. The Keras was selected to build and train the neural network. 
After model was developed, trained and assessed locally, it was moved and deployed in the  MS Azure Machine Learning environment. The re-training pipeline and REST API Endpoint was set up and became a part of the overall process pipeline through the generation of labels for provided input strings. The result included probabilities for all labels  and threshold was applied on reception side to filter out labels with insufficient probability. The model accuracy was accessed as 94%.

#### Appendices: 
The solution architecture diagram: https://github.com/boris-korotkov/DS-Portfolio/blob/main/Azure%20ML/MS%20Azure%20solution%20architecture.drawio.png

 The model training script: https://github.com/boris-korotkov/DS-Portfolio/blob/main/Azure%20ML/keras_model_training.py
   
 The deployment module: https://github.com/boris-korotkov/DS-Portfolio/blob/main/Azure%20ML/Model%20Training%20and%20Deployment.ipynb
      
 `The toolset: Azure Machine Learning, Azure Python SDK, SKLearn, NLTK, Keras`
