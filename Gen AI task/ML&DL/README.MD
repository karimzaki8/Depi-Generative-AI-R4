ML_TASK


Project Overview
In this project, I developed a machine learning pipeline to classify members of the US House of Representatives as either Democrat or Republican based on their voting records from the 1984 98th Congress. The dataset presented several real-world challenges, including non-standard labeling, significant missing data (abstentions), and numeric noise.

Key Features & Workflow
I implemented a full end-to-end data science workflow, focusing on data integrity and model robustness:

1. Data Cleaning & Preprocessing
Label Standardization: I unified inconsistent party labels such as REP, repub, and demo into a standard format.

Noise Reduction: I identified and removed numeric outliers like -999.0 and -998.5, replacing them with NaN to prepare for imputation.

Strategic Imputation: Instead of simply dropping rows, I used a party-based mode imputation. I filled in missing votes using the most common vote (mode) cast by members of the same party for that specific issue.

2. Addressing Data Leakage
One of the critical parts of this project was ensuring the validity of the model evaluation:

The Problem: In my initial approach, I performed imputation on the entire dataset, which unintentionally leaked information from the test set into the training process.

The Solution: I corrected this by splitting the data into training and testing sets first. I then calculated the modes using only the training data and applied those values to the test set, ensuring a fair and realistic evaluation.

3. Model Architecture
I built an Ensemble Voting Classifier to maximize predictive stability. The ensemble combines three different algorithmic approaches:

Logistic Regression: Proved that the data is linearly separable.

Random Forest: Captured non-linear decision boundaries and feature importance.

Support Vector Machine (SVM): Optimized the margin between classes.

Performance
The final model achieved 100% accuracy on the test set. While this is a perfect score, it is justified by the extreme political polarization of the 1984 Congress, particularly on key issues like the Physician Fee Freeze.


Technologies Used
Python (Pandas, NumPy)

Scikit-Learn (Classification, Imputation, Model Selection)

Matplotlib/Seaborn (Data Visualization)

____________________________________________________________________________________________________________________________________________________________________________________________________________________________
