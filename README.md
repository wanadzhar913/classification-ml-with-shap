#### **TLDR**

Exploratory data analysis & modeling exercise with Logistic Regression, Imbalanced-learn, RobustScaler and SHAP (SHapley Additive exPlanations). The dataset details a set of categorical/continuous features with a binary target variable `classLabel`.

#### **Folder Structure**
```
├── README.md
├── data
│   ├── processed_training.csv
│   ├── processed_validation.csv
│   ├── training2.csv
│   └── validation2.csv
├── notebooks
│   ├── 1_EDA.ipynb
│   ├── 2_Feature_Engineering_&_Treatment.ipynb
│   ├── 3_Model_Building.ipynb
│   └── helper_functions.py
```

#### **Outcomes of EDA (Exploratory Data Analysis)**
- We note that, since we do not have any information as to what these variables represent, we unfortunately aren't able to do more business-specific analyses. Hence, we'll focus on understanding the underlying distributions of each feature in the dataset.
- Neither datasets had any duplicates in them.
- In terms of missing values, more than half of the rows in feature `v16` are missing for both validation & training sets, the most for any feature in the dataset.
- For categorical features, there are several instances of highly imbalanced classes e.g., `classLabel` (training), `v12`, `v8` (training), `v4` & `V1`, as well as values with extremely rare occurences (<1% presence in the feature). These are namely the value *l*, for `v4`, and the value *o*, for `v12`.
- For continous features, most are positively skewed with the exception of `v5` & `v6`. Most of these positively skewed features have outliers.
- In terms of correlation between numerical columns, we've identified features `v15` & `v13` to be suffering from perfect multicollinearity. Hence, we'll randomly drop one when we build our classification model.
- On the other hand, for the categorical columns, Cramer's V reveals that column `v17` has an extremely high correlation with the target (~98%), `classLabel`. This is also grounds for dropping due to redundancy.