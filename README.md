CBOE + ADX Absolute Crossover Futures Trading System
This system scans all current month NSE stock futures and generates bullish and bearish trading signals based on CBOE oscillator and ADX (Directional Index) indicators.

How It Works
Fetches all current month stock futures (excluding NIFTY/BANKNIFTY) using Kite API.

Updates OHLC (Open, High, Low, Close, Volume) data for the last 50 trading days for each future.

Calculates indicators:

CBOE-based oscillator (odds of bull, bear, stagnant)

ADX, DI+ and DI- (Wilder’s smoothing)

Checks for absolute crossovers:

Bullish Trigger:

odd_bull crosses above 15, AND

di_plus crosses above 9 (on yesterday or today).

Bearish Trigger:

odd_bear crosses above 15, AND

di_minus crosses above 9 (on yesterday or today).

Crossovers for CBOE and ADX can happen on different days within the last 2 days.

Outputs results:

Bullish signals → green_absolute.csv

Bearish signals → red_absolute.csv

How to Run
Configure your Kite API credentials in the script.

Ensure PostgreSQL is running with required tables (script will auto-create if missing).

Run the main script to fetch data, calculate indicators, and generate signals:

bash
Copy
Edit
python main.py
Check the output CSV files for bullish and bearish trade candidates.

Requirements
Python 3.x

kiteconnect, pandas, numpy, psycopg2

PostgreSQL database

