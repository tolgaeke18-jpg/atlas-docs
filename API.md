# Atlas API Specification

**Version:** 0.1.0

**Status:** Draft

**Owner:** Atlas Labs

---

# Overview

Atlas exposes RESTful APIs for the mobile application and future web applications.

All endpoints use HTTPS and JSON.

Base URL

https://api.atlaslabs.app/api/v1

---

# Authentication

Authentication Method

Bearer Token (JWT)

Header

Authorization: Bearer <token>

---

# Response Format

Success

```json
{
  "success": true,
  "data": {},
  "message": null
}
```

Error

```json
{
  "success": false,
  "error": {
    "code": "USER_NOT_FOUND",
    "message": "User not found."
  }
}
```

---

# Authentication APIs

## Login

POST

/auth/login

Body

```json
{
  "email":"user@email.com",
  "password":"password"
}
```

---

## Register

POST

/auth/register

---

## Logout

POST

/auth/logout

---

## Refresh Token

POST

/auth/refresh

---

# User APIs

## Get Profile

GET

/users/me

---

## Update Profile

PUT

/users/me

---

## Delete Account

DELETE

/users/me

---

# Vehicle APIs

## Get My Vehicles

GET

/vehicles

---

## Add Vehicle

POST

/vehicles

Example

```json
{
  "manufacturer":"Togg",
  "model":"T10X",
  "year":2026
}
```

---

## Update Vehicle

PUT

/vehicles/{vehicleId}

---

## Delete Vehicle

DELETE

/vehicles/{vehicleId}

---

## Set Default Vehicle

POST

/vehicles/{vehicleId}/default

---

# Vehicle Library APIs

## Manufacturers

GET

/library/manufacturers

---

## Models

GET

/library/models

Query Parameters

manufacturerId

year

---

## Vehicle Details

GET

/library/models/{id}

---

# Trip APIs

## Plan Trip

POST

/trips/plan

Example

```json
{
  "origin":"Istanbul",
  "destination":"Ankara",
  "battery":82,
  "averageSpeed":110
}
```

Returns

- Estimated Consumption
- Arrival Battery
- Charging Stops
- Total Duration

---

## Trip History

GET

/trips

---

## Trip Details

GET

/trips/{tripId}

---

# Charging APIs

## Charging Stations

GET

/charging/stations

Query Parameters

latitude

longitude

radius

connector

---

## Station Details

GET

/charging/stations/{id}

---

## Nearby Stations

GET

/charging/nearby

---

## Charging Networks

GET

/charging/networks

---

# AI APIs

## Ask Atlas

POST

/ai/chat

Example

```json
{
   "message":"Can I reach Ankara without charging?"
}
```

---

## AI History

GET

/ai/history

---

# Weather APIs

GET

/weather

Parameters

latitude

longitude

---

# Notification APIs

GET

/notifications

PUT

/notifications/read

DELETE

/notifications/{id}

---

# Favorites APIs

GET

/favorites

POST

/favorites

DELETE

/favorites/{id}

---

# Settings APIs

GET

/settings

PUT

/settings

---

# Error Codes

| Code | Description |
|--------|-------------|
| AUTH_001 | Invalid Token |
| AUTH_002 | Token Expired |
| USER_001 | User Not Found |
| VEHICLE_001 | Vehicle Not Found |
| TRIP_001 | Trip Calculation Failed |
| AI_001 | AI Service Unavailable |
| SERVER_500 | Internal Server Error |

---

# HTTP Status Codes

200 OK

201 Created

204 No Content

400 Bad Request

401 Unauthorized

403 Forbidden

404 Not Found

422 Validation Error

500 Internal Server Error

---

# Versioning

Atlas uses URL versioning.

Example

/api/v1/

Future

/api/v2/

---

# Rate Limiting

Anonymous

60 requests/minute

Authenticated

300 requests/minute

Premium

1000 requests/minute

---

# Security

HTTPS Only

JWT Authentication

Row Level Security

Request Validation

Input Sanitization

Rate Limiting

Audit Logging

---

# Future APIs

Vehicle Telemetry

Battery Health

OBD Device

Fleet Management

Insurance

Energy Prices

Apple CarPlay

Android Auto

---

# API Goals

Simple

Predictable

Secure

Fast

Versioned

Developer Friendly

---

© Atlas Labs
