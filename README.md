# Indian-Automotive-Data-Hub-API
The Indian Automotive Data Hub API offers real-time access to comprehensive and up-to-date data on the latest cars in India.

# Get it on

### This API listeed on RapidAPI - [Check Here](https://rapidapi.com/Deadpool2000/api/indian-automotive-data-hub-api)

![logo-ra](https://github.com/user-attachments/assets/4b4a1dac-90c1-4aee-b57f-1641edfc36f2)

## Endpoints

## 1. Get Car Details

- **URL**: /search
- **Method**: GET
- **Description**: Retrieves detailed information about cars based on the provided search parameters (model name required, other filters optional).

### Query Parameters:
| Parameter     | Type   | Required | Description                                                                 |
|---------------|--------|----------|-----------------------------------------------------------------------------|
| name          | String | Yes      | The car model name (or part of it) to search for.                           |
| fuel          | String | No       | Filter by fuel type: Petrol, Diesel, CNG, or Electric/EV.                   |
| seating       | Int    | No       | Filter by number of seats (e.g., 5, 7).                                     |
| vehicle_type  | String | No       | Filter by vehicle type: SUV, Sedans, Hatchback, MUV, Sports Utilities.      |

**Response Format:**
- Success (200): Returns a JSON object with car details and their variants.

  **Example**:
  
```
{
    "0": {
      "brand name": "Toyota",
      "model name": "Fortuner",
      "body type": "SUV",
      "engine": "2755 cc",
      "mileage": "12 kmpl",
      "seating": "7",
      "Petrol": "no",
      "CNG": "no",
      "Diesel": "yes",
      "Electric": "no",
      "variants": {
        "0": {
          "name": "Fortuner 4x2 AT",
          "engine": "2755 cc",
          "fuel type": "Diesel",
          "variant status": "Active",
          "on-road price": "₹ 32,00,000",
          "title": "Top Variant",
          "car variant": "FTR-001",
          "vehicle type": "SUV"
        },
        "1": {
          "name": "Fortuner 4x4 MT",
          "engine": "2755 cc",
          "fuel type": "Diesel",
          "variant status": "Active",
          "on-road price": "₹ 35,00,000",
          "title": "4WD Option",
          "car variant": "FTR-002",
          "vehicle type": "SUV"
        }
      }
    }
  }
```

- Error (400): Missing or incorrect parameters.

  **Example**:
  
```
{
    "error": "Car name is required"
}

{
    "error": "Incorrect fuel type! Use 'Diesel', 'Petrol', 'CNG' or 'Electric/EV'"
}
```

- Error (404): No car matches found.

  **Example**:
 
```
 {
    "error": "No cars matched your search"
  }
```

---
### **Example Usage**

**1. Request:**

`GET /search?name=Creta&fuel=Petrol&seating=5&vehicle_type=SUV`

**Response**:

```
{
  "0": {
    "brand name": "Hyundai",
    "model name": "Creta",
    "body type": "SUV",
    "engine": "1497 cc",
    "mileage": "17 kmpl",
    "seating": "5",
    "Petrol": "yes",
    "CNG": "no",
    "Diesel": "yes",
    "Electric": "no",
    "variants": {
      "0": {
        "name": "Creta EX",
        "engine": "1497 cc",
        "fuel type": "Petrol",
        "variant status": "Active",
        "on-road price": "₹ 11,00,000",
        "title": "Base Variant",
        "car variant": "CRT-001",
        "vehicle type": "SUV"
      }
    }
  }
}
```

**2. Request:**

`GET /car?name=Fortuner&fuel=Diesel`

**Response**:

```
{
  "0": {
    "brand name": "Toyota",
    "model name": "Fortuner",
    "body type": "SUV",
    "engine": "2755 cc",
    "mileage": "12 kmpl",
    "seating": "7",
    "Petrol": "no",
    "CNG": "no",
    "Diesel": "yes",
    "Electric": "no",
    "variants": {
      "0": {
        "name": "Fortuner 4x2 AT",
        "engine": "2755 cc",
        "fuel type": "Diesel",
        "variant status": "Active",
        "on-road price": "₹ 32,00,000",
        "title": "Top Variant",
        "car variant": "FTR-001",
        "vehicle type": "SUV"
      }
    }
  }
}
```

---

## Error Handling
- 400 Bad Request: Returned when required query parameters are missing or when incorrect filter values are provided.
- 404 Not Found: Returned when no car matches the search criteria.

---

### Rate Limiting (Optional Section):
- Rate Limit: 100 requests per minute.
- Response Code: 429 (Too Many Requests)

---

### Versioning
- Current Version: v1.0

---