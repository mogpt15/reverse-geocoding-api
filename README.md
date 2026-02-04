# Reverse Geocoding API

REST API to convert latitude/longitude coordinates into city, state, and country data. Turn GPS coordinates into human-readable locations.

## Features

- Convert lat/long coordinates to location names
- Returns city, state, and country code
- Works with any location on Earth
- 5,000 requests/month on free tier
- Example Response:
```json
{
  "name": "San Francisco",
  "state": "California",
  "country_code": "US"
}
```

## Authentication

1. Create account at [omkar.cloud](https://www.omkar.cloud/auth/sign-up)

![Sign Up](https://raw.githubusercontent.com/omkarcloud/assets/master/images/signup.png)

2. Get API key from [omkar.cloud/api-key](https://www.omkar.cloud/api-key)

![Copy API Key](https://raw.githubusercontent.com/omkarcloud/assets/master/images/enrichment-key-omkar.png)

3. Include `API-Key` header in requests

## Quick Start

```bash
curl -X GET "https://reverse-geocoding-api.omkar.cloud/reverse-geocode?lat=37.7749&lon=-122.4194" \
  -H "API-Key: YOUR_API_KEY"
```

```json
[
  {
    "name": "San Francisco",
    "state": "California",
    "country_code": "US"
  }
]
```

## Installation

### Python

```bash
pip install requests
```

```python
import requests

response = requests.get(
    "https://reverse-geocoding-api.omkar.cloud/reverse-geocode",
    params={"lat": 37.7749, "lon": -122.4194},
    headers={"API-Key": "YOUR_API_KEY"}
)

data = response.json()[0]
print(f"Location: {data['name']}, {data['state']}, {data['country_code']}")
```

### Node.js

```bash
npm install axios
```

```javascript
import axios from "axios";

const response = await axios.get("https://reverse-geocoding-api.omkar.cloud/reverse-geocode", {
    params: { lat: 37.7749, lon: -122.4194 },
    headers: { "API-Key": "YOUR_API_KEY" }
});

console.log(`Location: ${response.data[0].name}, ${response.data[0].state}`);
```

## API Reference

### Endpoint

```
GET https://reverse-geocoding-api.omkar.cloud/reverse-geocode
```

### Headers

| Header | Required | Description |
|--------|----------|-------------|
| `API-Key` | Yes | API key from [omkar.cloud/api-key](https://www.omkar.cloud/api-key) |

### Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `lat` | Yes | Latitude (-90 to 90) |
| `lon` | Yes | Longitude (-180 to 180) |

### Response Fields

| Field | Type | Description |
|-------|------|-------------|
| `name` | string | City/place name |
| `state` | string | State or province |
| `country_code` | string | Two-letter ISO country code |

## Examples

### Get location from coordinates

```python
response = requests.get(
    "https://reverse-geocoding-api.omkar.cloud/reverse-geocode",
    params={"lat": 40.7128, "lon": -74.0060},
    headers={"API-Key": "YOUR_API_KEY"}
)

location = response.json()[0]
print(f"{location['name']}, {location['state']}")  # New York, New York
```

### Tokyo coordinates

```python
response = requests.get(
    "https://reverse-geocoding-api.omkar.cloud/reverse-geocode",
    params={"lat": 35.6762, "lon": 139.6503},
    headers={"API-Key": "YOUR_API_KEY"}
)

location = response.json()[0]
print(f"{location['name']}, {location['country_code']}")  # Tokyo, JP
```

## Error Handling

```python
response = requests.get(
    "https://reverse-geocoding-api.omkar.cloud/reverse-geocode",
    params={"lat": 37.7749, "lon": -122.4194},
    headers={"API-Key": "YOUR_API_KEY"}
)

if response.status_code == 200:
    data = response.json()
elif response.status_code == 401:
    # Invalid API key
    pass
elif response.status_code == 429:
    # Rate limit exceeded
    pass
```

## Rate Limits

| Plan | Price | Requests/Month |
|------|-------|----------------|
| Free | $0 | 5,000 |
| Starter | $25 | 100,000 |
| Grow | $75 | 1,000,000 |
| Scale | $150 | 10,000,000 |

## Questions? We have answers.

Reach out anytime. We will solve your query within 1 working day.

[![Contact Us on WhatsApp about Reverse Geocoding API](https://raw.githubusercontent.com/omkarcloud/assets/master/images/whatsapp-us.png)](https://api.whatsapp.com/send?phone=918178804274&text=I%20have%20a%20question%20about%20the%20Reverse%20Geocoding%20API.)

[![Contact Us on Email about Reverse Geocoding API](https://raw.githubusercontent.com/omkarcloud/assets/master/images/ask-on-email.png)](mailto:happy.to.help@omkar.cloud?subject=Reverse%20Geocoding%20API%20Question)
