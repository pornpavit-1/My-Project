#  Portfolio allocation for investment using sentiment analysis from financial news
By Mr.Pornpavit Kaoropthai, Mr.Thanapat Wiriyakiatphaisan

## 1.0 Abstract
This code implements a portfolio construction and management tool that combines sentiment analysis on financial news with machine learning models and portfolio optimization techniques. The tool identifies stocks that are likely to outperform the market, simulates an investment strategy, and evaluates the performance. In the example, an initial capital of 10,000 USD is used and the investment outcome is visualized using various charts and summary statistics.

## 2.0 Executive Summary
This project aims to allow users to ingest financial news data, perform sentiment processing, and construct an investment portfolio accordingly. The main steps include:

1.Loading and cleaning news data from a CSV file stored on Google Drive.

2.Text preprocessing using cleaning techniques, stop words removal, and lemmatization.

3.Sentiment analysis using the VADER model and assigning labels (e.g., Strong Buy, Buy, Hold, Sell, Strong Sell).

4.Retrieving stock price data via Yahoo Finance with the yfinance library.

5.Portfolio optimization using various methods such as MVO, HRP, and MCVaR (implemented via PyPortfolioOpt).

6.Simulating an investment to determine share purchases and final portfolio value, along with detailed visualization using charts.

## 3.0 Data	
News Data: The code first mounts Google Drive and reads a CSV file containing financial news data—specifically including “Title”, “Summary”, and “Ticker” columns.

Stock Data: Stock pricing data is fetched from Yahoo Finance via the yfinance library for a specified date range.

## 4.0 Methodology
### 4.1 Data Preparation and Cleaning
Mounting Google Drive: The script mounts Google Drive using drive.mount('/content/drive') to access files stored there.

Loading CSV Data: It reads the CSV file using pd.read_csv() while specifying appropriate data types and selecting necessary columns.

Data Cleaning: It removes duplicate rows and rows with missing values using dropna() and drop_duplicates().

### 4.2 Text Preprocessing
Combining Text: The code concatenates “Title” and “Summary” into a “Cleaned Text” column.

Removing Unwanted Patterns: It removes URLs, usernames, and non-alphabetic characters using regular expressions (re.sub()).

Standardizing Text: The text is converted to lowercase, and stop words are removed via the NLTK stopwords corpus.

Lemmatization: The NLTK WordNetLemmatizer is employed to reduce words to their base forms.

### 4.3 Sentiment Analysis and Labeling
Sentiment Calculation: The VADER sentiment analyzer computes a compound score for each text snippet.

Assigning Labels: The set_label() function maps the compound score to investment signal labels (e.g., “Strong Buy”, “Buy”, “Hold”, “Sell”, “Strong Sell”).

Saving Results: The annotated data is then saved to a CSV file for further reference.

### 4.4 Stock Data Retrieval and Portfolio Optimization
Fetching Stock Prices: The code retrieves closing price data from Yahoo Finance using yfinance over the specified period.

Portfolio Construction: The PyPortfolioOpt library is used to perform portfolio optimization with several methods such as MVO, HRP, and MCVaR, calculating expected returns, risk (volatility), and Sharpe ratios.

Comparing Portfolios: The outcomes of the various optimization methods are compared in a summary table and saved for further analysis.

### 4.5 Investment Simulation and Visualization
Investment Simulation: The portfolio, derived from the MVO model, is used to simulate an investment by allocating an initial capital (e.g., 10,000 USD) and computing the number of shares bought and final portfolio value.

ROI Calculation: The script calculates profit/loss and ROI by comparing initial and final portfolio values.

Visualization: The results are visualized using bar charts (showing individual stock investments and profit/loss), pie charts (displaying investment allocation) and line charts (tracking portfolio value over time).

## 5.0 Results	
Sentiment Summary: A table is generated that shows the average sentiment score for each stock, filtering out those with strong positive signals (“Strong Buy”).

Portfolio Optimization Results: A summary table compares the performance (expected return, risk, and Sharpe ratio) of the portfolios optimized with different methods (MVO, HRP, MCVaR).

Investment Simulation Outcome: The simulation section displays the number of shares purchased per stock, profit/loss, and ROI, along with visualization through various charts.

## 6.0 Conclusion and Next Steps
This code exemplifies an integration of NLP, machine learning, and portfolio optimization techniques to build an effective portfolio management tool.

Recommendations: Future improvements could include further hyperparameter tuning of various models, expanding the dataset across multiple years for more robust predictions, and creating new features to enhance portfolio performance.

Future Work: Productionizing this tool may involve developing a user-friendly interface and integrating real-time market data.

## 7.0 Appendix

Setup details and installation instructions for necessary libraries (e.g., yfinance, PyPortfolioOpt).

Charts and graphs that visualize the simulation results.

Further recommendations for expanding and refining the tool in the future.

### 7.1 References	
1.Engelberg, J., & Parsons, C. A. (2011).
The Causal Impact of Media in Financial Markets.
The Journal of Finance, 66(1), 67–97.

2.Gokmenoglu, K. K., & Fazlollahi, N. (2015).
The Interactions among Gold, Oil, and Stock Market: Evidence from S&P500.
Procedia Economics and Finance, 25, 478–488.

3.Tetlock, P. C. (2007).
Giving Content to Investor Sentiment: The Role of Media in the Stock Market.
The Journal of Finance, 62(3), 1139–1168.

4.Hoti & Ajdari (2023).
Sentiment analysis using the VADER model for assessing company services based on posts on social media.
SEEU Review, 18(2), 19–33.

5.Katterbauer et al. (2023).
Return versus hype: Are Islamic metaverse companies more profitable than general ones? A Chinese stock analysis.
Turkish Journal of Islamic Economics, 11(2), 2–16.

6.Natras, Soja, & Schmidt (2022).
Ensemble machine learning of Random Forest, AdaBoost and XGBoost for vertical total electron content forecasting.
Remote Sens, 14, 1–34.

