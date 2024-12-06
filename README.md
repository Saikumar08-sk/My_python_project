# Time Series Forecasting model using the FBProphet module

The forecasting model is able to predict the Sunspots (see above) by using Facebook’s Prophet Time
Series Forecasting model. Prophet is a procedure for forecasting time series data based on an additive model
where non-linear trends are fit with yearly, weekly, daily seasonality. Sunspots are temporary phenomena on the
Sun's photosphere that appear as spots darker than the surrounding areas. They are regions of reduced surface
temperature caused by concentrations of magnetic field flux that inhibit convection. Sunspots usually appear in
pairs of opposite magnetic polarity. Their number varies according to the approximately 11-year solar cycle.

Source: https://en.wikipedia.org/wiki/Sunspot

# contents:

* Column 1-3: Gregorian calendar date
1) Year
2) Month
3) Day
* Column 4: Date in fraction of year.
* Column 5: Daily total sunspot number. A value of -1 indicates that no number is available for that day (missing value).
* Column 6: Daily standard deviation of the input sunspot numbers from individual stations.
* Column 7: Number of observations used to compute the daily value.
* Column 8: Definitive/provisional indicator. '1' indicates that the value is definitive. '0' indicates that the value is still provisional.

# Data Granularity
1) Daily:
Uses daily sunspot data, capturing high-frequency details and noise.
Suitable for short-term predictions (e.g., up to a year).

2) Monthly:
Uses monthly sunspot data, balancing granularity and smoothness.
Suitable for medium-term trends (e.g., predictions for several years).

3) Yearly:
Uses yearly sunspot data, providing a smoothed and aggregated view.
Best suited for long-term trend forecasting (e.g., decades into the future).

# Data Preprocessing
1) Daily:
Handles missing values (-1).
Log-transform applied to stabilize variance and adjust for skewness.
Zeroes are replaced with a small positive constant (1e-6).

2) Monthly:
Likely similar preprocessing as the daily notebook but tailored for monthly timestamps.
May involve aggregating or interpolating daily data into monthly averages.

3) Yearly:
Preprocessing is simpler due to yearly data's aggregated nature.
Filters invalid values and uses log-transformations for stability.

# Prophet Model Setup
1) Daily:
Forecasts short-term future values (e.g., 100, 200, 365 days).
Captures fine-grained seasonality.

2) Monthly:
Forecasts medium-term values (e.g., several years).
Likely models monthly seasonality patterns effectively.

3) Yearly:
Forecasts long-term values (e.g., 20 years).
Focuses on overall trends and broader patterns.

# Forecasting Horizon
1) Daily: Short-term (days to a year).
2) Monthly: Medium-term (years).
3) Yearly: Long-term (decades).

# Model Evaluation
Although all notebooks import evaluation metrics like MAE, MAPE, and R², they likely differ in performance:

* Daily: Higher error due to noise and granularity.
* Monthly: Balanced performance, likely smoother than daily.
* Yearly: Lower errors due to aggregated, less noisy data.
