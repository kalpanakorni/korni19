# agent_system.py

import random

class FarmerAgent:
    def __init__(self, name):
        self.name = name
    
    def report_soil_data(self):
        return {
            "soil_moisture": random.uniform(10, 30),
            "pH": random.uniform(5.5, 7.5)
        }

class WeatherStationAgent:
    def __init__(self, location):
        self.location = location
    
    def get_forecast(self):
        return {
            "rainfall_mm": random.uniform(0, 20),
            "temperature_c": random.uniform(15, 35)
        }

class ExpertAgent:
    def advise(self, soil_data, forecast):
        advice = []
        if soil_data["soil_moisture"] < 15:
            advice.append("Increase irrigation")
        if forecast["rainfall_mm"] > 10:
            advice.append("Delay watering")
        if soil_data["pH"] < 6:
            advice.append("Add lime to soil")
        return advice

# Main coordination
def main():
    farmer = FarmerAgent("Farmer A")
    weather_station = WeatherStationAgent("Field 1")
    expert = ExpertAgent()

    soil_data = farmer.report_soil_data()
    forecast = weather_station.get_forecast()
    advice = expert.advise(soil_data, forecast)

    print(f"Soil Data: {soil_data}")
    print(f"Weather Forecast: {forecast}")
    print(f"Expert Advice: {advice}")

if __name__ == "__main__":
    main()
