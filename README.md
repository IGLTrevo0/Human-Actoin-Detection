Readme · MDCopyHuman Action Detection
A machine learning pipeline that classifies 12 human physical activities from MHEALTH wearable sensor data. Handles class imbalance, removes outliers via quantile filtering, applies RobustScaler preprocessing, and benchmarks four classifiers: Logistic Regression, KNN, Random Forest, and SVM.

Dataset

Source: MHEALTH (Mobile Health) dataset
File: mhealth_raw_data.csv
Sensors: Accelerometer and gyroscope readings from body-worn sensors (left/right ankle)
Subjects: Multiple subjects labeled as subject1, subject2, etc.

Activity Classes
CodeActivity0None1Standing still (1 min)2Sitting and relaxing (1 min)3Lying down (1 min)4Walking (1 min)5Climbing stairs (1 min)6Waist bends forward (20x)7Frontal elevation of arms (20x)8Knees bending / crouching (20x)9Cycling (1 min)10Jogging (1 min)11Running (1 min)12Jump front & back (20x)

Pipeline Overview
1. Data Preprocessing

Class imbalance handling: Activity 0 (None) was heavily over-represented. It was downsampled to 40,000 rows to balance the dataset.
Outlier removal: Values outside the 1st–99th quantile range were dropped for each feature.
Label encoding: Activity labels and subject names were encoded to integers using LabelEncoder.

2. Feature Scaling

RobustScaler was used (instead of StandardScaler) because it is resistant to outliers — it scales using the median and interquartile range rather than the mean and standard deviation.

3. Train/Test Split

75% training / 25% test split with random_state=42

4. Models Trained
ModelNotesLogistic RegressionBaseline linear classifierK-Nearest Neighbors (K=5)Distance-based classifierRandom Forest (100 trees)Ensemble tree classifierSVM (RBF kernel, C=0.1)Margin-based classifier
5. Evaluation

Accuracy score reported for each model
Confusion matrix computed (heatmap visualization available but commented out)


Dependencies
numpy
pandas
matplotlib
seaborn
scikit-learn
Install with:
bashpip install numpy pandas matplotlib seaborn scikit-learn

How to Run

Place mhealth_raw_data.csv in the project directory (update the path in the notebook if needed).
Open Human_Action_Detection.ipynb in Jupyter Notebook or JupyterLab.
Run all cells sequentially.


Note: The dataset path is currently hardcoded as C:\Users\sahil\Human Action Detetection\mhealth_raw_data.csv. Update this to your local path before running.


Project Structure
Human-Action-Detection/
│
├── Human_Action_Detection.ipynb   # Main notebook
├── mhealth_raw_data.csv           # Dataset (not included)
└── README.md