import pandas as pd
import requests
from bs4 import BeautifulSoup
from io import StringIO

# Step 1: Define the URL where GameStop revenue data is located
url = 'https://www.macrotrends.net/stocks/charts/GME/gamestop/revenue'

# Step 2: Set up headers to mimic a browser request
headers = {
    'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/85.0.4183.121 Safari/537.36'
}

# Step 3: Make a request to the website with headers
response = requests.get(url, headers=headers)

# Step 4: Check the response status
if response.status_code == 200:
    # Step 5: Parse the HTML content of the page
    soup = BeautifulSoup(response.content, 'html.parser')
    
    # Step 6: Try to find the table
    tables = soup.find_all('table')  # Get all tables
    
    if tables:
        # Use StringIO to convert the HTML table to a DataFrame
        gme_revenue = pd.read_html(StringIO(str(tables[0])))[0]
        
        # Step 7: Display the last five rows of the DataFrame
        print(gme_revenue.tail())
    else:
        print("No table found on the webpage.")
else:
    print(f"Failed to retrieve the webpage. Status code: {response.status_code}")
