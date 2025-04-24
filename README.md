# 🔥 Burner Power Optimizer with XGBoost and Optuna

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Python](https://img.shields.io/badge/Python-3.12%2B-blue.svg)](https://www.python.org/)
[![XGBoost](https://img.shields.io/badge/XGBoost-Model-green)](https://xgboost.readthedocs.io/)
[![Optuna](https://img.shields.io/badge/Optuna-HPO-orange)](https://optuna.org/)

A robust and modular Python tool for training an optimized XGBoost regression model to predict burner power.  
It connects directly to a MySQL database, performs feature engineering, optimizes hyperparameters with Optuna, logs the entire process, and stores performance metrics in a custom SQL table.

---

## 🧠 Overview

This project helps optimize burner power prediction in industrial processes by:

- 🗃️ Extracting data from a MySQL production database  
- 🧹 Preprocessing and engineering domain-specific features  
- ⚙️ Automatically optimizing model hyperparameters using [Optuna](https://optuna.org)  
- ♻️ Training a powerful [XGBoost](https://xgboost.readthedocs.io/) regression model  
- 📊 Logging and saving model performance metrics (MAE, RMSE, R², etc.)  
- 📀 Exporting the model and transformer to a `.pkl` file  
- 🧱 Saving results into a SQL table for traceability  

---

## 📂 Project Structure

```
burner-power-optimizer/
├── burner_model_trainer.py          # Main training script and class definition
├── burner_model.pkl                 # Output: Trained model and transformer (generated after running)
├── requirements.txt                 # List of Python dependencies
├── README.md                        # Project documentation (this file)
├── LICENSE                          # Open-source license (MIT)
└── logs/
    └── burner_model_trainer.log     # Log file with detailed training/evaluation information
```

---

## 📦 Installation

> **Python 3.8+ is required.**  
Install dependencies from the `requirements.txt` file:

```bash
pip install -r requirements.txt
```

**Required packages**:

- `pandas`
- `numpy`
- `joblib`
- `optuna`
- `mysql-connector-python`
- `scikit-learn`
- `xgboost`

---

## ⚙️ Configuration

Edit the database connection and training configuration in the `__main__` block:

```python
trainer = BurnerModelTrainer(
    host="your_mysql_host",
    user="your_username",
    password="your_password",
    database="your_database",
    table_name="your_table"
)
trainer.run()
```

---

## 💧 Main Functionalities

| Functionality            | Description                                                        |
|-------------------------|--------------------------------------------------------------------|
| **MySQL Integration**   | Connects and fetches data from a live SQL table                    |
| **Feature Engineering** | Generates domain-specific features like `FUEL_PER_PROD`            |
| **Outlier Filtering**   | Automatically removes extreme `BURNER_POWER` values               |
| **HPO with Optuna**     | Finds best model parameters using Bayesian optimization           |
| **Model Training**      | Fits an `XGBRegressor` to transformed targets                      |
| **Evaluation**          | Calculates metrics: MAE, RMSE, R², MAPE, etc.                    |
| **Model Export**        | Saves the trained model and transformer as `.pkl`                 |
| **Metrics Logging**     | Saves results in a log file and a custom SQL table                |

---

## 📊 Sample Output Metrics

```
MAE:                12.8765
RMSE:               15.2893
R² Score:           0.9142
MAPE:               4.57%
Explained Var.:     0.9151
Max Error:          33.41
Median Abs Error:   9.23
```

✅ All logs are saved to `logs/burner_model_trainer.log`  
✅ Metrics are also inserted into a MySQL table for future monitoring

---

## 🧦 Evaluation Metrics Explained

| Metric                | Description                                  |
|----------------------|----------------------------------------------|
| **MAE**              | Mean Absolute Error                          |
| **RMSE**             | Root Mean Squared Error                      |
| **R² Score**         | Coefficient of Determination                 |
| **MAPE**             | Mean Absolute Percentage Error               |
| **Explained Var.**   | Proportion of variance explained by model   |
| **Max Error**        | Largest absolute difference                  |
| **Median AE**        | Median absolute error                        |

---

## 🤖 Usage Example

```bash
# Run the training script
python burner_model_trainer.py
```

> Make sure your MySQL credentials and table names are correct before execution.

---

## 📃 License

This project is licensed under the **MIT License**.  
Feel free to use, modify, and distribute it for personal or commercial use.

🔗 See the full [LICENSE](LICENSE) file.

---

## 🤝 Contact

For questions, suggestions, or collaboration:

**Deuser Tech Group**  
📧 Email: iafontal@deuser.es  
🌐 Website: [Deuser](https://deuser.es/)

---

<p align="center">
  <img src="https://github.com/user-attachments/assets/d7d86d47-edc0-468a-89da-84e13ad3ffea" width="200" alt="EU logo">
  &nbsp;&nbsp;
  <img src="https://github.com/user-attachments/assets/b8738b8e-c69f-43f7-a434-0a847ad429bc" width="150" alt="SX AIPI logo">
</p>

## ✨ Acknowledgements

- [Optuna](https://optuna.org/) – For powerful hyperparameter optimization
- [XGBoost](https://xgboost.readthedocs.io/) – High-performance machine learning library
- [Scikit-learn](https://scikit-learn.org/) – Model evaluation tools

---

> Made with ❤️ for industrial AI projects and continuous improvement.
