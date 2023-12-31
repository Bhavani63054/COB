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

# Read the CSV file
df = pd.read_csv('weather_dataset.csv')

# Replace missing values (assuming NaN represents missing values)
df.fillna(value, inplace=True)

# Remove outliers (you can customize this based on your dataset and criteria)
# For example, removing rows where temperature is below 0 or above 40 (just as an example)
df = df[(df['main.temp'] > 0) & (df['main.temp'] < 40)]

# Save the cleaned DataFrame to a new CSV file
df.to_csv('cleaned_weather_dataset.csv', index=False)
