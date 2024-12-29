# AI-Driven Supply Chain Disruption Predictor and Inventory Optimization System

## Project Overview
The AI-Driven Supply Chain Disruption Predictor and Inventory Optimization System is an advanced AI-powered solution designed to revolutionize supply chain management. The system monitors global supply chain data, predicts potential disruptions, and optimizes inventory levels accordingly. By leveraging Large Language Models (LLMs) like OpenAI GPT and Meta LLaMA for natural language processing (NLP) and data analysis, the system can predict risks in supply chains and automate inventory adjustments. Real-time alerts are provided via Slack or Email, ensuring businesses can respond proactively to supply chain disruptions.

## Project Statement
This project aims to enable businesses to manage supply chain disruptions by:
- Predicting disruptions through analysis of news, supplier data, and transportation trends.
- Optimizing inventory levels based on predicted disruption risks.
- Automating notifications and inventory adjustments.

The system integrates with Google Sheets for data storage and utilizes ERP systems like SAP for seamless inventory management.

## Key Features and Outcomes
- **Prediction of Supply Chain Disruptions**: Uses NLP to analyze global data sources for potential risks.
- **Dynamic Inventory Optimization**: Adjusts inventory based on disruption forecasts.
- **Real-Time Notifications**: Alerts through Slack or Email for critical disruptions and inventory recommendations.
- **ERP Integration**: Automates stock adjustments and reorder point suggestions.

## Task 1: API Integration with Python

### Objective
For Task 1, the goal was to integrate data APIs to gather relevant supply chain data from the web. The task was focused on using the provided websites and their APIs to fetch small data sets and analyze them using Python.

### Steps Taken

1. **API Selection**:
   The first step involved selecting appropriate APIs to gather data related to global supply chains. For this, I used the GNews API to fetch news articles about "supply chain disruption" in real-time.

2. **Python Integration**:
   I used Python's `requests` library to interact with the API and retrieve data. The retrieved data was parsed and processed for use in further analysis.
   
   Here's the code used to fetch and process the data:
   ```python
   import requests
   import pandas as pd

   # API Key and base URL for the GNews API
   api_key = 'f25f7be0c8f4b7903ee9ee56dc97c72a'
   base_url = "https://gnews.io/api/v4/search"
   params = {
       'q': 'supply chain disruption',
       'lang': 'en',
       'country': 'us',
       'max': 10,  # Number of articles
       'token': api_key  # API key
   }

   response = requests.get(base_url, params=params)
   if response.status_code == 200:
       print("API request successful!")
       data = response.json()
   else:
       print(f"Error: {response.status_code} - {response.text}")

   if 'articles' in data:
       articles = data['articles']
       news_df = pd.DataFrame([{
           'Title': article['title'],
           'Description': article['description'],
           'Source': article['source']['name'],
           'Published Date': article['publishedAt'],
           'URL': article['url']
       } for article in articles])

       print("Collected News Articles:")
       print(news_df)

       # Save the data as both CSV and Excel files
       news_df.to_csv("supply_chain_news.csv", index=False)
       news_df.to_excel("supply_chain_news.xlsx", index=False, engine='openpyxl')
   else:
       print("No articles found.")

## Task 2: Advanced News Analysis and Risk Assessment

### Objective
Task 2 expanded the project's capabilities by implementing advanced news article analysis specifically focused on Lithium-Ion battery supply chains. The system now incorporates sentiment analysis and sophisticated risk assessment using LLM technology.

### Key Implementations

#### Event Registry API Integration
- Implemented OR operations in keyword search to capture a broader range of relevant articles.
- Keywords include: "Lithium Ion Batteries", "Li-ion Batteries", "Lithium Battery", "EV Batteries".
- Fetches articles from both news and blog sources within a 7-day window.

#### Sentiment Analysis
- Integrated **TextBlob** for robust sentiment analysis of news articles.
- Provides sentiment classification (**POSITIVE**, **NEGATIVE**, **NEUTRAL**).
- Includes confidence scoring for reliability assessment.

#### Risk Analysis with Groq LLaMA
- Implemented structured risk analysis using the LLaMA model.
- Analyzes five key risk categories:
  1. Raw Material Risks
  2. Manufacturing Risks
  3. Geographic Risks
  4. Industry Impact
  5. Mitigation Strategies
- Provides detailed analysis of potential supply chain impacts.

#### Data Processing Pipeline
- Automated article fetching and processing.
- Structured data storage in both DataFrame and JSON formats.
- Real-time analysis logging and result storage.