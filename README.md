Stock Trade Outlier Analysis using Graph Database

This project aims to develop a system for analyzing foreign exchange (FX) trades, identifying outliers, and comparing actual trading patterns against expected guidelines using a graph database, specifically Neo4j. The following sections outline the key components of the project, including data collection, graph construction, outlier detection, comparison with expected guidelines, and visualization.

OBJECTIVES :
Data Collection:
Collect historical FX trade data for various currency pairs (e.g., EUR/USD, GBP/USD) from public APIs or CSV files.
Store the collected data in a Neo4j graph database to facilitate efficient querying and analysis.
Graph Construction:
Develop a graph structure where each trade is represented as a node, with edges indicating relationships between trades (e.g., consecutive trades or trades with similar characteristics).
Enrich the nodes with relevant attributes such as trade volume, price, and timestamp to provide context for each trade.
Outlier Detection:
Implement statistical methods (e.g., Z-score, Interquartile Range) to identify outliers—trades that significantly deviate from typical trading patterns.
Highlight these outliers within the graph for easy identification and further analysis.
Comparison with Expected Guidelines:
Define expected trading patterns or guidelines based on historical data and market norms, such as normal trading volume ranges and typical price movements.
Analyze actual trading behavior against these guidelines to identify deviations and assess compliance.
Visualization:
Utilize visualization libraries (e.g., Matplotlib, Plotly) to create graphical representations of the trade data, emphasizing identified outliers.
Generate a comprehensive report summarizing findings, insights, and visualizations derived from the analysis.
This project involves analyzing the historical forex data for the EUR/USD exchange rate and detecting outliers based on price and volume fluctuations. The data is fetched using the yfinance library, and the historical values are stored in a Neo4j graph database for further analysis. Z-scores are calculated for both price and volume data, and outliers are identified based on predefined thresholds. These outliers are then stored in the Neo4j database with appropriate relationships to help in analyzing trading anomalies.
Key Features:
Forex Data Fetching:
The project retrieves historical forex data for EUR/USD using the yfinance API.
Data is fetched at an hourly interval for a specified period (7 days in this case).
Data Storage in Neo4j:
The fetched forex data is stored in Neo4j, a graph database.
The system creates Currency nodes for EUR and USD and links them with EXCHANGE_RATE relationships to store exchange rate data.
Each trade is stored as a Trade node with attributes like price, volume, and timestamp.
Outlier Detection:
Z-scores for price and volume are calculated to identify outliers.
If a trade’s price or volume exceeds a certain Z-score threshold (e.g., greater than 3 or less than -3), it is flagged as an outlier.
These outliers are stored in Neo4j, and an Outlier node is created and linked to the corresponding trade with an IS_OUTLIER relationship.
Trade Relationships:
The system identifies consecutive trades and stores relationships between trades (e.g., CONSECUTIVE relationships).
Additionally, trades that are similar in price and volume are linked with SIMILAR relationships.
Analysis and Querying:
Queries can be run to retrieve trade relationships, outliers, and other trading anomalies from the Neo4j graph database.
Example queries include fetching consecutive trades, similar trades, and outlier trades based on price or volume deviations.
Technologies Used:
Python: For data fetching, processing, and storing it in the Neo4j database.
yfinance: To fetch historical forex data from Yahoo Finance.
Neo4j: A graph database to store forex trades and relationships.
Z-Score Calculation: Used to identify outliers based on price and volume deviations.
Workflow:
Data Collection: Forex data is collected using the yfinance API for the EUR/USD pair.
Data Processing: Z-scores are calculated for price and volume.
Outlier Detection: Trades with Z-scores exceeding the threshold are flagged as outliers.
Graph Storage: Data, including trades and outliers, is stored in a Neo4j database with relationships linking trades to other trades and currencies.
Analysis: Queries are executed to retrieve relationships, identify consecutive trades, and flag anomalies.
Use Cases:
Trading Anomaly Detection: The system can be used to detect unusual trading patterns based on historical price and volume data, which can help in identifying potential market manipulation or abnormal events.
Market Analysis: Traders and analysts can use the stored data to examine trends and correlations between currency values and market behaviors.
Outlier Identification: The project can help detect rare events (outliers) that could represent important market signals, such as sudden spikes or drops in trading volume or price.
Potential Enhancements:
Real-time Data Integration: Integrating live forex data feeds for real-time analysis and outlier detection.
Automated Alerts: Implementing a system that sends alerts when outliers or significant price/volume anomalies are detected.
Advanced Analytics: Incorporating machine learning models to predict forex price movements or detect more complex trading anomalies.

