# 🏠 Real Estate Price Prediction

### Machine Learning Regression Project | Python • Pandas • Scikit-learn • Jupyter

<p align="center">
  <strong>Predicting residential property prices using Machine Learning</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.x-blue?style=for-the-badge&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/Scikit--learn-ML-orange?style=for-the-badge&logo=scikit-learn&logoColor=white" alt="Scikit-learn">
  <img src="https://img.shields.io/badge/Pandas-Data%20Analysis-purple?style=for-the-badge&logo=pandas&logoColor=white" alt="Pandas">
  <img src="https://img.shields.io/badge/Jupyter-Notebook-orange?style=for-the-badge&logo=jupyter&logoColor=white" alt="Jupyter">
  <img src="https://img.shields.io/badge/NumPy-Computing-blue?style=for-the-badge&logo=numpy&logoColor=white" alt="NumPy">
</p>

---

## 📌 About the Project

This project implements an end-to-end **Machine Learning regression workflow** for predicting residential property prices using the **Boston Housing dataset**.

The project covers the complete process from data exploration and preprocessing to model training, evaluation, cross-validation, model comparison, and model persistence.

Three regression algorithms were evaluated:

* 📈 Linear Regression
* 🌳 Decision Tree Regressor
* 🌲 Random Forest Regressor

After comparing the models using **10-fold cross-validation**, the **Random Forest Regressor** achieved the lowest average RMSE among the tested models.

---

## 🎯 Project Objective

The main objective is to build a regression model that can estimate the **median value of houses** based on characteristics of the property and its surrounding area.

The project focuses not only on obtaining predictions, but also on understanding the complete machine learning pipeline:

```text
📊 Data
   ↓
🔍 Data Exploration
   ↓
✂️ Train / Test Split
   ↓
🧹 Data Preprocessing
   ↓
⚙️ Feature Scaling
   ↓
🤖 Model Training
   ↓
📏 Model Evaluation
   ↓
🔁 10-Fold Cross-Validation
   ↓
🏆 Model Comparison
   ↓
💾 Model Persistence
```

---

## 📊 Dataset

The project uses the **Boston Housing dataset**.

The dataset contains housing and socioeconomic information used to predict the median value of homes.

### Dataset Features

|  Feature  | Description                             |
| :-------: | --------------------------------------- |
|   `crim`  | Per capita crime rate                   |
|    `zn`   | Proportion of residential land          |
|  `indus`  | Proportion of non-retail business acres |
|   `chas`  | Charles River dummy variable            |
|   `nox`   | Nitric oxide concentration              |
|    `rm`   | Average number of rooms per dwelling    |
|   `age`   | Proportion of older buildings           |
|   `dis`   | Distance to employment centres          |
|   `rad`   | Accessibility to radial highways        |
|   `tax`   | Property-tax rate                       |
| `ptratio` | Pupil-teacher ratio                     |
|    `b`    | Demographic-related feature             |
|  `lstat`  | Percentage of lower-status population   |
|   `medv`  | **Median value of homes — Target**      |

---

# 🧹 Data Preprocessing

Before training the models, the numerical features are processed using a **Scikit-learn Pipeline**.

### Missing Value Handling

Missing values are handled using the **median** of each feature:

```python
SimpleImputer(strategy="median")
```

### Feature Scaling

Features are standardized using:

```python
StandardScaler()
```

### Complete Preprocessing Pipeline

```python
my_pipeline = Pipeline([
    ('imputer', SimpleImputer(strategy="median")),
    ('std_scaler', StandardScaler()),
])
```

Using a pipeline ensures that preprocessing steps are applied consistently.

---

# 🤖 Machine Learning Models

## 1️⃣ Linear Regression

Linear Regression was used as the baseline regression model.

**10-Fold Cross-Validation Results:**

```text
Mean RMSE       : 5.03
Standard Deviation : 1.06
```

---

## 2️⃣ Decision Tree Regressor

A Decision Tree Regressor was evaluated to capture non-linear relationships within the dataset.

**10-Fold Cross-Validation Results:**

```text
Mean RMSE       : 4.27
Standard Deviation : 0.86
```

---

## 3️⃣ Random Forest Regressor 🌲

Random Forest produced the strongest results among the three tested models.

**10-Fold Cross-Validation Results:**

```text
Mean RMSE       : 3.34
Standard Deviation : 0.71
```

---

# 🏆 Model Comparison

The models were compared using **10-fold cross-validation** and **Root Mean Squared Error (RMSE)**.

| 🧠 Model             | 📉 Mean RMSE | 📊 Std. Deviation |
| -------------------- | -----------: | ----------------: |
| Linear Regression    |         5.03 |              1.06 |
| Decision Tree        |         4.27 |              0.86 |
| **🌲 Random Forest** |     **3.34** |          **0.71** |

### 🥇 Best Performing Model

> **Random Forest Regressor**

Among the three models tested, Random Forest achieved:

* 🥇 Lowest average RMSE
* 📉 Lowest standard deviation
* 🔄 More consistent cross-validation performance

Therefore, **Random Forest was selected as the best-performing model among the tested approaches**.

---

# 📏 Evaluation Metric

The primary evaluation metric used in this project is **Root Mean Squared Error (RMSE)**.

```text
              ┌───────────────────┐
              │       RMSE        │
              │                   │
              │    √(MSE)         │
              └───────────────────┘
```

RMSE measures the magnitude of prediction errors while giving larger errors greater weight.

### Lower RMSE = Better Performance

For this project:

```text
Random Forest       3.34  🟢
Decision Tree       4.27  🟡
Linear Regression   5.03  🔴
```

---

# 🔁 10-Fold Cross-Validation

Instead of relying on a single train/test split, the models were evaluated using **10-fold cross-validation**.

The dataset is divided into 10 folds.

```text
Fold 1 → Validation
Fold 2 → Validation
Fold 3 → Validation
...
Fold 10 → Validation
```

Each fold is used as the validation set once, while the remaining folds are used for training.

The resulting RMSE values are then summarized using:

* **Mean RMSE**
* **Standard Deviation**

This provides a more reliable view of model performance.

---

# 💾 Model Persistence

After training, the model is saved using **Joblib**.

### Save the model

```python
from joblib import dump

dump(model, 'Dragon.joblib')
```

### Load the model

```python
from joblib import load

model = load('Dragon.joblib')
```

This allows the trained model to be reused without training it again.

---

# 📁 Project Structure

```text
real-estate-price-prediction/
│
├── 📓 Dragon Real Estate.ipynb
├── 📓 Model Usage.ipynb
│
├── 📊 Data.csv
├── 📊 Housing1.xlsx
│
├── 🤖 Dragon.joblib
│
├── 📝 Outputs from different models.txt
├── 📄 housing.names.txt
│
├── 🚫 .gitignore
└── 📖 README.md
```

### 📓 `Dragon Real Estate.ipynb`

Main machine learning notebook containing:

* Data loading
* Data exploration
* Train/test split
* Data preprocessing
* Feature scaling
* Model training
* Model evaluation
* Cross-validation
* Model comparison

### 📓 `Model Usage.ipynb`

Demonstrates how the trained model can be loaded and used for predictions.

### 🤖 `Dragon.joblib`

Saved trained machine learning model.

### 📊 `Data.csv`

Dataset used for the machine learning workflow.

### 📊 `Housing1.xlsx`

Excel version of the housing dataset used during the project.

### 📝 `Outputs from different models.txt`

Contains model evaluation results and outputs.

---

# 🛠️ Tech Stack

| Technology              | Purpose                 |
| ----------------------- | ----------------------- |
| 🐍 **Python**           | Programming language    |
| 🐼 **Pandas**           | Data manipulation       |
| 🔢 **NumPy**            | Numerical computing     |
| 📊 **Matplotlib**       | Data visualization      |
| 🤖 **Scikit-learn**     | Machine Learning        |
| 💾 **Joblib**           | Model persistence       |
| 📓 **Jupyter Notebook** | Development environment |
| 🌐 **Git & GitHub**     | Version control         |

---

# 🚀 Getting Started

## 1️⃣ Clone the Repository

```bash
git clone https://github.com/Sylani-55/real-estate-price-prediction.git
```

## 2️⃣ Navigate to the Project

```bash
cd real-estate-price-prediction
```

## 3️⃣ Install Dependencies

```bash
pip install numpy pandas matplotlib scikit-learn joblib jupyter
```

## 4️⃣ Launch Jupyter Notebook

```bash
jupyter notebook
```

## 5️⃣ Run the Project

Open:

```text
Dragon Real Estate.ipynb
```

Run the notebook cells sequentially to reproduce the machine learning workflow.

---

# 🎯 Learning Outcomes

Through this project, I practiced:

* 📊 Working with a real-world dataset
* 🔍 Exploratory data analysis
* 🧹 Handling missing values
* ⚙️ Feature preprocessing
* 📏 Feature scaling
* 🔗 Building Scikit-learn Pipelines
* 🤖 Regression algorithms
* 📐 Model evaluation
* 📉 Mean Squared Error
* 📊 Root Mean Squared Error
* 🔁 Cross-validation
* 🏆 Model comparison
* 💾 Saving and loading trained models
* 🐙 Using Git and GitHub for project version control

---

# 🔮 Future Improvements

The project can be extended further by:

* 🎛️ Hyperparameter tuning using `GridSearchCV`
* 🎲 Experimenting with `RandomizedSearchCV`
* 🔍 Performing feature importance analysis
* 🤖 Testing additional regression algorithms
* 📊 Adding more detailed visualizations
* 💾 Saving the complete preprocessing + model pipeline
* 🌐 Building a web interface for predictions
* 🔌 Creating a REST API for the model
* 🚀 Deploying the model as a machine learning application

---

# 📌 Key Takeaway

This project demonstrates a complete **supervised machine learning regression workflow**, from raw data to model evaluation and persistence.

Among the three models tested:

> 🏆 **Random Forest Regressor achieved the best cross-validation performance with a mean RMSE of 3.34.**

The project also demonstrates how preprocessing pipelines and cross-validation can be used to build a more reliable machine learning workflow.

---

# 👨‍💻 Author

### **Syed Mohammed Sylani**

Aspiring Software & Machine Learning Developer focused on building practical projects and strengthening skills in **Python, Data Science, Machine Learning, and Software Development**.

---

<p align="center">
  ⭐ If you found this project useful, consider giving the repository a star!
</p>

<p align="center">
  <strong>Built with Python 🐍 & Machine Learning 🤖</strong>
</p>
