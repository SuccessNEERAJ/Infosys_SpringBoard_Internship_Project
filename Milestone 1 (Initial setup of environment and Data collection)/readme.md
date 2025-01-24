## Milestone 1: API Integration with Python

### Objective
For Milestone 1, the goal was to integrate data APIs to gather relevant supply chain data from the web. The task was focused on using the provided websites and their APIs to fetch small data sets and analyze them using Python.

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