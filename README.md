##Welcome to FraudShield: Intelligent Credit Card Fraud Detection Project

The goal is to detect fraudulent transactions using intelligent machine-learning techniques.

Followed All steps related to machine learning model development.
Import Ilbraries 
import pandas as pd 
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
%matplotlib inline
from sklearn.preprocessing import LabelEncoder
from sklearn import metrics
from sklearn.metrics import precision_recall_curve, roc_auc_score
from sklearn.metrics import precision_score, recall_score, confusion_matrix, classification_report
from sklearn.metrics import accuracy_score, f1_score
If you get error that module is not found, try to first install module using pip isntall module name

Download ne_110m_admin_0_countries.sh from geopandas data set to show map.


All Steps:
Data Pre Processing
Exploratory Data Analysis
Feature Engineering 
Model Training 
Hyper Parameter Tuning Using RandomizedSearchCV
Model Validation
Save model
Predict on unseen Datase

Note:
If you use GridSearchCV, your computer might slow down or get memory leak. To avoid this, use RandomizedSearchCV.
Hyper Parameter might not affect performance or you can get worse result instead of better. So don't rely on hyper parameter tuning

