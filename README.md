# COB
import pandas as pd
import requests

# OpenWeatherMap API key (replace 'YOUR_API_KEY' with your actual API key)
api_key = 'YOUR_API_KEY'
city = 'London'  # Replace with your desired city

# API endpoint for current weather data
api_url = f'http://api.openweathermap.org/data/2.5/weather?q={city}&appid={api_key}'

# Fetch data from the API
response = requests.get(api_url)
data = response.json()

# Create a DataFrame from the API data
df = pd.json_normalize(data)

# Save the DataFrame to a CSV file
df.to_csv('weather_dataset.csv', index=False)
fhgg
