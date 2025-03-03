# Weather API

## Overview
The **Weather API** allows users to retrieve current weather conditions, forecasts, and historical weather data for a given location. Developers can integrate this API to fetch weather details based on city name, latitude/longitude, or ZIP code.

- **Base URL:** `https://api.weatherdata.com/v1`
- **Authentication:** API Key required in the request headers. 

---

## Authentication  
To authenticate, include your API key in the request header:

```http
X-API-KEY: your_api_key
```

## Endpoints
The Weather API provides the following endpoints:

| Method | Endpoint         | Description |
|--------|----------------|-------------|
| `GET`  | `/weather`      | Get current weather conditions. |
| `GET`  | `/forecast`     | Get a multi-day weather forecast. |
| `GET`  | `/history`      | Retrieve past weather data. |

---

### Get Current Weather

Retrieve the latest weather conditions for a given location.

- **URL:** `GET /weather`
- **Authentication Required:** ✅ Yes  
- **Query Parameters:**

  | Parameter   | Type    | Required? | Description |
  |------------|--------|------------|-------------|
  | `city`     | `string` | Yes | City name (e.g., "New York"). |
  | `lat`      | `float`  | No | Latitude of the location. |
  | `lon`      | `float`  | No | Longitude of the location. |
  | `units`    | `string` | No | Measurement units (`metric`, `imperial`). |


### **Example Request**
```http
GET /weather?city=London&units=metric
Host: api.weatherdata.com
X-API-KEY: your_api_key
```

### **Example Response**
```json
{
  "city": "London",
  "temperature": 15,
  "humidity": 72,
  "conditions": "Cloudy",
  "wind_speed": 12.5
}
```
---


### Get a Multi-day Weather Forecast

Use this endpoint to retrieve data for multi-day weather forecasts for a given location, planning ahead (e.g., showing the 7-day forecast), requesting forecasts for a specific number of days (default: 7 days, max: 10 days).


-**URL:** `GET /forecast`
-**Authentication Required:** ✅ Yes  
-**Query Parameters:**

  | Parameter   | Type    | Required? | Description |
  |------------|--------|------------|-------------|
  | `city`     | `string` | Yes | City name (e.g., "New York"). |
  | `lat`      | `float`  | No | Latitude of the location. |
  | `lon`      | `float`  | No | Longitude of the location. |
  | `days`     | `integer`| No | Number of forecast days (default: 7, max: 10).  |
  | `units`    | `string` | No | Measurement units (`metric`, `imperial`). |


  ### **Example Request**
```http
GET /forecast?city=Tokyo&days=5&units=metric
Host: api.weatherdata.com
X-API-KEY: your_api_key
```

### **Example Response**
```json
{
  "city": "Tokyo",
  "forecast": [
    { "date": "2025-03-04", "temperature": 18, "conditions": "Sunny" },
    { "date": "2025-03-05", "temperature": 20, "conditions": "Partly Cloudy" },
```
---

### Get Weather History

Use this endpoint to retrieve past weather conditions for a given date and location. This is useful for climate research, weather analysis, or travel planning.

- **URL:** `GET /history`
- **Authentication Required:** ✅ Yes  
- **Query Parameters:**

  | Parameter   | Type    | Required? | Description |
  |------------|--------|------------|-------------|
  | `city`     | `string` | Yes | City name (e.g., "New York"). |
  | `lat`      | `float`  | No | Latitude of the location. |
  | `lon`      | `float`  | No | Longitude of the location. |
  | `date`     | `string`| No | Date in `YYYY-MM-DD` format.   |
  | `units`    | `string` | No | Measurement units (`metric`, `imperial`). |

  ### **Example Request**
```http
GET /history?city=Paris&date=2025-02-28&units=metric
Host: api.weatherdata.com
X-API-KEY: your_api_key
```

### **Example Response**
```json
{
  "city": "Paris",
  "date": "2025-02-28",
  "temperature": 10,
  "humidity": 65,
  "conditions": "Clear Sky",
  "wind_speed": 8.4
}
```
---




