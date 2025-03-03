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

