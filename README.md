# Stock-Price-Forecasting-Using-LSTM
A deep learning project for forecasting stock closing prices using **Long Short-Term Memory (LSTM)** networks. The project compares a baseline LSTM model with a tuned architecture to evaluate whether model adjustments can improve time series forecasting performance.

## Project Workflow
Data Collection → Preprocessing → Sequence Preparation → Model Development → Hyperparameter Tuning → Evaluation

## Dataset
Historical stock transaction data was obtained from **Yahoo Finance**. The dataset contains:
* `Date`
* `Close`

The project focuses on predicting future closing prices based on historical closing price sequences.

Two stocks were analyzed:
* FB
* IBM

The dataset contains historical data up to **April 1, 2020**.

## Data Preparation
The data was prepared as a time series before being used as input to the LSTM model. The last **one year of data** was reserved as the test set, while the remaining data was divided into training and validation sets using a **90:10 split**.  
A sliding-window approach was used to transform the time series into supervised learning sequences.
* Input window: **5 previous days**
* Forecast horizon: **1 day ahead**

Each sequence uses the previous five closing prices to predict the next closing price.

## Baseline Model
A baseline LSTM model was developed as the initial reference model.  
The baseline architecture used:
* LSTM layer with **50 units**
* Output layer with **1 unit**
* ReLU activation
* One-day-ahead forecasting

The baseline model was then used as a reference for evaluating the tuned model.

## Model Tuning
The LSTM architecture and hyperparameters were adjusted to investigate whether the forecasting performance could be improved. The tuned model was evaluated against the baseline using the same test data and evaluation metrics.

## Evaluation
Model performance was evaluated using:
* **RMSE** — Root Mean Squared Error
* **MAE** — Mean Absolute Error
* **MAPE** — Mean Absolute Percentage Error

### Results
| Stock         | Model         | RMSE        | MAE         | MAPE        |
| ------------- | ------------: | ----------: | ----------: | ----------: |
| FB            |      Baseline |     4.5236% |     3.0906% |     1.6737% |
| FB            |      Improved | **4.3515%** | **3.0742%** | **1.6601%** | 
| IBM           |      Baseline |     2.6653% |     1.7201% |     1.3274% |
| IBM           |      Improved | **2.6494%** | **1.7059%** | **1.3158%** |

The tuned model achieved lower results for both stocks compared with the baseline model.

## Visualization
The project includes visualizations comparing the actual and predicted stock prices to evaluate how closely the model follows the observed price movements.
