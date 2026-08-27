# Cardiovascular Disease Prediction 🫀

A machine learning project that predicts whether a person has cardiovascular disease based on medical and lifestyle features such as age, blood pressure, cholesterol, weight, and physical activity.

## 📊 Dataset

- **Source:** [Kaggle - Cardiovascular Disease Dataset](https://www.kaggle.com/datasets/akshatshaw7/cardiovascular-disease-dataset)
- **Size:** 30,000+ records
- **Target variable:** `cardio` (0 = healthy, 1 = diseased)
- **Features:** age, gender, height, weight, blood pressure (ap_hi, ap_lo), cholesterol, glucose, smoking, alcohol intake, physical activity

## 🔧 Data Preprocessing

- Checked class balance (dataset is nearly balanced: 50.5% healthy / 49.5% diseased)
- Handled missing values (none found)
- Removed unnecessary columns (`id`, `Unnamed: 0`)
- Filtered unrealistic values using medical logic
- Converted age from days to years
- Handled outliers using the IQR method with clipping
- Checked and removed duplicate rows
- Engineered a new feature: **BMI**

## 📈 Exploratory Data Analysis (EDA)

- Visualized target distribution with a pie chart
- Verified outlier handling with boxplots
- Generated a correlation heatmap across all features
- Analyzed each feature's correlation with the target (`cardio`)
  - Strongest predictors: `ap_hi`, `ap_lo`, `age`, `cholesterol`, `BMI`

## ✂️ Data Splitting & Scaling

- Split into training (80%) and testing (20%) sets using stratified sampling
- Scaled features using `StandardScaler`

## 📉 Dimensionality Reduction

Two techniques were compared against the original feature set:

- **Feature Selection:** `SelectKBest` (ANOVA F-test) to select the top 7 most statistically significant features
- **PCA:** Reduced dimensionality while preserving 95% of the explained variance

## 🤖 Modeling

Three classification models were trained and evaluated on all three versions of the data (Original, Feature Selection, PCA):

- Decision Tree
- Random Forest
- K-Nearest Neighbors (KNN)

## 🏆 Results

| Model | Original | Feature Selection | PCA |
|---|---|---|---|
| Decision Tree | 63.7% | 63.7% | 62.8% |
| Random Forest | 71.1% | 70.8% | 70.8% |
| KNN | 69.6% | 69.8% | 69.1% |

**Random Forest** achieved the best overall performance. Feature Selection slightly improved results, while PCA significantly reduced dimensionality with minimal loss in accuracy.

## 🗂️ Project Structure

```
cardiovascular-disease-prediction/
├── source_code.ipynb     # Full analysis & modeling notebook
├── health_data.csv       # Dataset
├── requirements.txt      # Project dependencies
└── README.md             # Project documentation
```

## ▶️ How to Run

```bash
git clone https://github.com/tjin9/cardiovascular-disease-prediction.git
cd cardiovascular-disease-prediction
pip install -r requirements.txt
jupyter notebook source_code.ipynb
```

## 🛠️ Tools & Libraries

- Python, Pandas, NumPy
- Matplotlib, Seaborn
- Scikit-learn (`StandardScaler`, `SelectKBest`, `PCA`, `DecisionTreeClassifier`, `RandomForestClassifier`, `KNeighborsClassifier`)



