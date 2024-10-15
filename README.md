# Analyze-traffic-accident-data
# Traffic Accident Analysis

def analyze_accident_data(data):
    accident_hotspots = {}
    contributing_factors = {}

    for record in data:
        road_condition = record['road_condition']
        weather = record['weather']
        time_of_day = record['time_of_day']
        location = (record['latitude'], record['longitude'])

        # Count accidents by location
        if location not in accident_hotspots:
            accident_hotspots[location] = 0
        accident_hotspots[location] += 1

        # Count contributing factors
        if road_condition not in contributing_factors:
            contributing_factors[road_condition] = 0
        contributing_factors[road_condition] += 1

        if weather not in contributing_factors:
            contributing_factors[weather] = 0
        contributing_factors[weather] += 1

        if time_of_day not in contributing_factors:
            contributing_factors[time_of_day] = 0
        contributing_factors[time_of_day] += 1

    return accident_hotspots, contributing_factors

def visualize_hotspots(hotspots):
    for location, count in hotspots.items():
        print(f"Location: {location}, Accidents: {count}")

def visualize_contributing_factors(factors):
    for factor, count in factors.items():
        print(f"Factor: {factor}, Count: {count}")

# Example data
accident_data = [
    {'road_condition': 'wet', 'weather': 'rain', 'time_of_day': 'night', 'latitude': 34.0522, 'longitude': -118.2437},
    {'road_condition': 'dry', 'weather': 'clear', 'time_of_day': 'day', 'latitude': 34.0522, 'longitude': -118.2437},
    {'road_condition': 'wet', 'weather': 'rain', 'time_of_day': 'night', 'latitude': 34.0522, 'longitude': -118.2437},
]

hotspots, factors = analyze_accident_data(accident_data)
visualize_hotspots(hotspots)
visualize_contributing_factors(factors)
