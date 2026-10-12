Absolutely. Here is a clean, portfolio-ready README.md for your GitHub repository. It reflects the actual workflow and results of your project rather than making it sound like a generic forecasting project.
# 🌡️ Daily Minimum Temperature Forecasting

## Time-Series Forecasting using SARIMAX with Fourier Annual Seasonality

This project develops an end-to-end **time-series forecasting model for daily minimum temperature** using historical temperature observations from Melbourne, Australia.

The final model combines **SARIMAX(3,0,1)** with **5 Fourier harmonics** to capture annual seasonality and short-term temporal dependence.

The project covers the complete workflow from data cleaning and exploratory analysis to model development, evaluation, forecasting, and deployment through an interactive **Streamlit dashboard**.

---

## 🚀 Live Demo

**Streamlit Dashboard:**  
[Add your Streamlit Cloud URL here]

---

## 📌 Project Overview

### Problem

Daily temperature data contain both:

- Strong annual seasonal patterns
- Short-term temporal dependence
- Unusual warm and cold events

A forecasting model therefore needs to capture both the recurring annual cycle and short-term autocorrelation.

### Objective

The objective of this project is to:

- Explore historical daily minimum temperature patterns
- Identify trend, seasonality and autocorrelation
- Develop and compare time-series forecasting models
- Model annual seasonality using Fourier terms
- Select and evaluate a final SARIMAX model
- Generate a 365-day temperature forecast
- Deploy the forecasting model through an interactive Streamlit application

---

# 📊 Dataset

The project uses the **Daily Minimum Temperatures in Melbourne, Australia** dataset.

| Feature | Description |
|---|---|
| Location | Melbourne, Australia |
| Period | 1981–1990 |
| Frequency | Daily |
| Target | Daily minimum temperature |
| Unit | °C |
| Observations | Approximately 3,650 |

The cleaned dataset used by the project is:

```text
daily_minimum_temperature_cleaned.csv
Dataset source: The original dataset URL should be added here if required by the project submission.

🔬 Project Workflow
The complete workflow is:
Problem Definition
        ↓
Data Acquisition
        ↓
Data Cleaning
        ↓
Exploratory Data Analysis
        ↓
Time-Series Diagnostics
        ↓
Train / Validation / Test Split
        ↓
Baseline Models
        ↓
ARIMA Modelling
        ↓
Holt-Winters Modelling
        ↓
Fourier Feature Engineering
        ↓
SARIMAX + Fourier
        ↓
Residual Diagnostics
        ↓
Model Selection
        ↓
Final Test Evaluation
        ↓
365-Day Forecast
        ↓
Streamlit Dashboard
        ↓
GitHub / Streamlit Cloud Deployment
🧹 Data Preparation
The raw dataset was processed through the following steps:
1. Load the raw CSV dataset.
2. Convert the date variable to datetime format.
3. Sort observations chronologically.
4. Clean malformed temperature values.
5. Convert temperature values to numeric format.
6. Check for missing values.
7. Check for duplicate dates.
8. Establish daily time-series frequency.
9. Handle missing observations where required.
10. Save the cleaned dataset.
The resulting cleaned file is:
daily_minimum_temperature_cleaned.csv
📈 Exploratory Data Analysis
The following analyses were performed:
- Descriptive statistics
- Temperature distribution
- Histogram
- Boxplot
- Historical time-series plot
- Monthly temperature analysis
- Yearly temperature analysis
- Year-month heatmap
- Seasonal analysis
- Rolling mean
- Rolling standard deviation
- Time-series decomposition
- Day-of-year seasonal analysis
- Autocorrelation Function (ACF)
- Partial Autocorrelation Function (PACF)
- Lag correlation analysis
- Augmented Dickey-Fuller (ADF) test
Key EDA finding
The temperature series showed a strong annual seasonal pattern along with shorter-term temporal dependence.
This motivated the use of Fourier terms together with an ARIMA/SARIMAX structure.
🧪 Train / Validation / Test Strategy
A chronological split was used to avoid data leakage.
Dataset	Period	Purpose
Training	1981–1988	Model fitting
Validation	1989	Model selection
Final Test	1990	Final performance evaluation


The 1990 observations were kept as an untouched final test set during model selection.
🤖 Models Evaluated
Several forecasting approaches were evaluated.
1. Naïve Forecast
Uses the most recent observed temperature as the forecast.
2. Seasonal Naïve Forecast
Uses the temperature from the corresponding seasonal position approximately one year earlier.
3. ARIMA
Multiple combinations of:
p = 0–3
d = 0–1
q = 0–3
were evaluated.
4. Holt-Winters
An exponential smoothing approach was evaluated to model level, trend and seasonality.
5. SARIMAX + Fourier
SARIMAX was combined with Fourier terms to represent the annual seasonal cycle.
🌊 Fourier Feature Engineering
Instead of using a conventional SARIMA model with a seasonal period of 365 days, annual seasonality was represented using Fourier terms.
The annual period was defined as:
365.25 days
Five harmonics were used.
For each harmonic k:
sin(2πkt / 365.25)
cos(2πkt / 365.25)
were generated.
Therefore:
K = 5
Fourier terms allow the annual temperature cycle to be represented smoothly while allowing the SARIMAX component to focus on short-term temporal dependence.
🏆 Final Model
The final selected model was:
SARIMAX(3,0,1) + 5 Fourier Harmonics
Model specification
Parameter	Value
ARIMA order	(3,0,1)
Seasonal order	(0,0,0,0)
Fourier harmonics	5
Annual period	365.25 days
Target	Daily minimum temperature


The model was selected using a combination of:
- Validation MAE
- Validation RMSE
- AIC
- BIC
- Residual diagnostics
- Ljung-Box tests
- Model parsimony
📊 Model Performance
Performance on the held-out 1990 test set:
Model	MAE (°C)	RMSE (°C)
Naïve	3.32	3.99
Seasonal Naïve	2.87	3.65
ARIMA(1,0,2)	3.20	3.86
Holt-Winters	3.54	4.20
SARIMAX(3,0,1) + Fourier	1.97	2.56


Final performance
MAE: 1.97°C
RMSE: 2.56°C
Compared with the Seasonal Naïve baseline:
- MAE improved by approximately 31%
- RMSE improved by approximately 30%
This indicates that explicitly modelling the annual seasonal pattern using Fourier terms substantially improved forecasting performance.
🔍 Residual Diagnostics
Residual diagnostics were performed to determine whether important temporal structure remained unexplained.
The analysis included:
- Residual statistics
- Residual plots
- Residual ACF
- Ljung-Box tests at multiple lags
The initial SARIMAX(1,0,2) + Fourier model showed significant residual autocorrelation.
Alternative SARIMAX specifications were therefore evaluated.
The final SARIMAX(3,0,1) + Fourier model showed substantially improved residual behaviour, with no significant residual autocorrelation at the key diagnostic lags used for model assessment.
🔮 365-Day Forecast
After model selection, the final model was refitted using the complete historical dataset.
A 365-day future forecast was then generated.
Forecast summary
Statistic	Value
Mean	11.46°C
Minimum	6.84°C
Median	11.40°C
Maximum	15.86°C


The forecast captures the expected annual seasonal temperature cycle.
The application also provides 95% prediction intervals to represent forecast uncertainty.
⚠️ Error Analysis
The largest forecast errors were associated with unusually warm or cold days.
Examples included several observations during:
- January
- March
- August
- September
- October
- November
- December
These events were not fully captured by the univariate seasonal model.
This highlights an important limitation:
Historical temperature and annual seasonality alone cannot explain all short-term weather variability and extreme events.

🖥️ Streamlit Dashboard
The project includes an interactive Streamlit dashboard.
Dashboard features
Historical Data
- Historical temperature visualization
- Summary statistics
- Temperature trends
Model Evaluation
- MAE
- RMSE
- Model comparison
- Performance visualization
Forecasting
- User-selectable forecast horizon
- Future temperature predictions
- 95% prediction intervals
- Forecast summary statistics
Download
The forecast can be downloaded as a CSV file.
📁 Project Structure
daily-temperature-forecasting/
│
├── app.py
├── daily_minimum_temperature_cleaned.csv
├── requirements.txt
├── README.md
│
├── models/
│   └── sarimax_fourier_model.pkl
│
└── outputs/
    ├── SARIMAX_Fourier_365_day_forecast.csv
    ├── forecast_model_comparison.csv
    └── monthly_temperature_forecast.csv
🛠️ Technologies Used
Programming Language
- Python 3.11
Data Analysis
- Pandas
- NumPy
Statistical Modelling
- Statsmodels
- ARIMA
- SARIMAX
- Fourier seasonality
- Holt-Winters exponential smoothing
Visualization
- Matplotlib
Deployment
- Streamlit
- Streamlit Community Cloud
Version Control
- Git
- GitHub
Development Environment
- Jupyter Notebook
- Anaconda
⚙️ Installation
Clone the repository:
git clone https://github.com/YOUR_USERNAME/daily-temperature-forecasting.git
Navigate to the project:
cd daily-temperature-forecasting
Create the Conda environment:
conda create -n temperature_forecast python=3.11
Activate it:
conda activate temperature_forecast
Install the required packages:
pip install -r requirements.txt
▶️ Run the Application Locally
Start the Streamlit application:
streamlit run app.py
The dashboard should open automatically in your browser.
📦 Requirements
The main dependencies are:
streamlit
pandas
numpy
matplotlib
statsmodels
💾 Model Deployment
The trained SARIMAX model is stored as:
models/sarimax_fourier_model.pkl
The Streamlit application loads the saved model rather than retraining it every time the application runs.
This makes the dashboard faster and more suitable for deployment.
📌 Key Findings
1. Daily minimum temperature exhibits strong annual seasonality.
2. Short-term temporal autocorrelation is also present.
3. Seasonal Naïve forecasting provides a strong baseline.
4. Standard ARIMA models alone do not adequately represent the annual seasonal cycle.
5. Fourier terms provide an efficient way to represent annual seasonality.
6. The SARIMAX(3,0,1) + Fourier model achieved the best overall balance of accuracy and residual behaviour.
7. The final model achieved an RMSE of approximately 2.56°C on the held-out 1990 test set.
8. The model improved RMSE by approximately 30% compared with the Seasonal Naïve baseline.
9. The model performs well in capturing the overall seasonal trajectory but has difficulty with unusual weather events.
⚠️ Limitations
The current project has several limitations:
- It is primarily a univariate forecasting model.
- Only historical temperature is used as the main predictive information.
- Extreme weather events are difficult to predict.
- Fourier terms represent a smooth seasonal pattern and may not capture abrupt changes.
- Forecast uncertainty increases over longer horizons.
- The historical dataset covers approximately ten years.
🔭 Future Improvements
Future work could include:
- Adding humidity
- Adding rainfall
- Adding wind speed
- Adding atmospheric pressure
- Adding cloud cover
- Incorporating climate indicators such as ENSO
- Developing multivariate SARIMAX models
- Testing XGBoost and LightGBM
- Testing LSTM and GRU networks
- Developing ensemble forecasting models
- Implementing rolling-origin cross-validation
- Developing probabilistic forecasting approaches
📚 References
1. Box, G. E. P., Jenkins, G. M., Reinsel, G. C., & Ljung, G. M. Time Series Analysis: Forecasting and Control.
2. Hyndman, R. J., & Athanasopoulos, G. Forecasting: Principles and Practice.
3. Ljung, G. M., & Box, G. E. P. (1978). On a measure of lack of fit in time series models. Biometrika, 65(2), 297–303.
👩‍💻 Author
Leena Gaikwad
Public Health Researcher | Health Economics & Outcomes Research | Data Science & Machine Learning
Areas of interest include:
- Public Health Analytics
- Health Economics & Outcomes Research
- Evidence Synthesis
- Statistical Modelling
- Machine Learning
- Time-Series Forecasting
⭐ Project Highlights
Final Model: SARIMAX(3,0,1) + 5 Fourier Harmonics
Forecast Horizon: 365 days
Test MAE: 1.97°C
Test RMSE: 2.56°C
RMSE Improvement vs Seasonal Naïve: ~30%
Deployment: Streamlit
