import pyowm 
import matplotlib.pyplot as plt 
import csv 
 
 
 
def get_weather_forecast(location): 
    owm = pyowm.OWM('0143de37d56629e629873e0bd44edddf') 
     
    try: 
        observation = owm.weather_manager().weather_at_place(location) 
        weather = observation.weather 
 
        status = weather.status.lower() 
        temperature = weather.temperature('celsius')['temp'] 
        humidity = weather.humidity 
        wind_speed = weather.wind()['speed'] 
        wind_direction = weather.wind()['deg'] 
         
        forecast = f"The weather in {location} is {status} with a temperature of {temperature}°C and {humidity}% humidity, wind speed of {wind_speed} m/s, and wind direction of {wind_direction}°." 
        return forecast 
    except Exception as e: 
        return f"Error: {e}" 
    import pyowm 
from datetime import datetime 
 
def get_weather_forecast(location): 
    owm = pyowm.OWM('0143de37d56629e629873e0bd44edddf') 
     
    try: 
        observation = owm.weather_manager().weather_at_place(location) 
        weather = observation.weather 
 
        status = weather.status.lower() 
        temperature = weather.temperature('celsius')['temp'] 
        humidity = weather.humidity 
        wind_speed = weather.wind()['speed'] 
        wind_direction = weather.wind()['deg'] 
         
        current_time = datetime.now().strftime('%Y-%m-%d %H:%M:%S') 
         
        forecast = f"Time: {current_time},\nthe weather in {location} is {status} with a temperature of {temperature}°C ,\nhumidity:{humidity}% humidity \nwind speed of {wind_speed} m/s , wind direction of {wind_direction}°." 
        return forecast 
    except Exception as e: 
        return f"Error: {e}" 
 
 
 
def read_temperature_data(file_path): 
    dates = [] 
    temperatures = [] 
     
    with open(file_path, 'r') as file: 
        csv_reader = csv.reader(file) 
        next(csv_reader)   
        for row in csv_reader: 
            dates.append(row[0]) 
            temperatures.append(float(row[1])) 
     
    return dates, temperatures 
 
def plot_temperature_data(dates, temperatures): 
    plt.figure(figsize=(10, 6)) 
    plt.plot(dates, temperatures, marker='o', linestyle='-') 
    plt.title('Temperature Over Time') 
    plt.xlabel('Year') 
    plt.ylabel('Temperature (°C)') 
    plt.xticks(rotation=45) 
    plt.grid(True) 
    plt.tight_layout() 
    plt.show() 
 
if __name__ == "__main__": 
    location = input("Enter the location for weather prediction: ") 
    print(get_weather_forecast(location)) 
    import os 
import pyowm 
import matplotlib.pyplot as plt 
import csv 
 
# Specify absolute file path 
file_path = os.path.abspath('temperature_data.csv') 
 
def read_temperature_data(file_path): 
    dates = [] 
    temperatures = [] 
     
    try: 
        with open(file_path, 'r') as file: 
            csv_reader = csv.reader(file) 
            next(csv_reader)   
            for row in csv_reader: 
              dates.append(row[0]) 
              temperatures.append(float(row[1]))
              
        return dates.temperatures 
    except FileNotFoundError: 
            print(f"Error: File'{file_path}'not found.") 
            return [],[] 
