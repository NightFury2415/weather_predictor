Weather Predictor – Ridge Regression Forecasting

A next-day temperature forecasting model built using walk-forward validation to ensure realistic, future-proof evaluation.

🧠 How It Works

Loads historical daily data from weather.csv (indexed by DATE).

Drops columns with ≥ 5% missing values, normalizes names to lowercase, and fills gaps using forward-fill (ffill).

Defines the prediction target: tomorrow’s tmax, aligned to today’s row using .shift(-1).

Trains a Ridge Regression model using scikit‑learn with alpha=0.1, ignoring non-numeric identifiers (name, station).

Implements walk-forward backtesting:

Train on all past data

Predict the next 90 days

Slide forward and repeat (prevents data leakage)

Adds time-series intelligence via:

3 & 14-day rolling means (tmax, tmin, prcp)

Trend % difference vs rolling window

Seasonal expanding averages (month_avg_*, day_avg_*)

Measures accuracy using MAE → mean_absolute_error(actual, prediction) using Mean Absolute Error.

Visualizes forecast error distribution using matplotlib.

🛠️ Setup & Run
1. Install dependencies
pip install pandas scikit-learn matplotlib

2. Add dataset

Place your weather.csv file in the project root.

3. Run the model
python weather_predictor.py

✅ What I Achieved

Built an interpretable, fast, low-latency forecasting model

Used real-world simulation testing (walk-forward, not random splits)

Prevented future data leakage

Captured trend + seasonality without complex deep learning

Evaluated performance realistically using MAE
