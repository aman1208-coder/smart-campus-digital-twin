# API Specification

## 1. Overview
This specification defines the primary application programming interfaces required for device management, alert retrieval, campus monitoring, and digital twin access. All APIs are presented as design-level contracts for Phase 1 planning.

## 2. Authentication
- Authentication method: design-level secure login flow, expected to use a token or session mechanism.
- Use case: login before restricted access to device configuration and operational functions.

## 3. Device APIs

### POST /devices
Create a new device record.

#### Request
```json
{
  "deviceId": "TEMP-AB-A-101",
  "deviceType": "TEMPERATURE",
  "buildingId": "BUILD-A",
  "roomId": "ROOM-101",
  "status": "ACTIVE",
  "enabled": true,
  "mqttTopic": "campus/academic_block_a/room_101/temp/data"
}
```

#### Response
- Status: 201 Created
```json
{
  "deviceId": "TEMP-AB-A-101",
  "deviceType": "TEMPERATURE",
  "status": "ACTIVE",
  "enabled": true,
  "createdAt": "2026-09-24T09:00:00Z"
}
```

#### Error Responses
- 400 Bad Request for invalid payload
- 409 Conflict for duplicate device ID
- 401 Unauthorized for unauthenticated requests

### GET /devices
Retrieve all devices with optional filters.

#### Request
- Query parameters: `type`, `building`, `status`, `enabled`

#### Response
- Status: 200 OK
```json
{
  "devices": [
    {
      "deviceId": "TEMP-AB-A-101",
      "deviceType": "TEMPERATURE",
      "status": "ACTIVE",
      "buildingId": "BUILD-A",
      "roomId": "ROOM-101"
    }
  ]
}
```

### GET /devices/{id}
Retrieve a single device by unique identifier.

#### Response
- Status: 200 OK
```json
{
  "deviceId": "TEMP-AB-A-101",
  "deviceType": "TEMPERATURE",
  "buildingId": "BUILD-A",
  "roomId": "ROOM-101",
  "status": "ACTIVE",
  "lastSeen": "2026-09-24T09:20:00Z"
}
```

#### Error Responses
- 404 Not Found if the device does not exist
- 401 Unauthorized

### PUT /devices/{id}
Update device metadata or operational properties.

#### Request
```json
{
  "status": "WARNING",
  "enabled": true,
  "mqttTopic": "campus/academic_block_a/room_101/temp/data"
}
```

#### Response
- Status: 200 OK
```json
{
  "deviceId": "TEMP-AB-A-101",
  "status": "WARNING",
  "updatedAt": "2026-09-24T09:21:00Z"
}
```

#### Error Responses
- 400 Bad Request for invalid field updates
- 404 Not Found
- 401 Unauthorized

## 4. Alert APIs

### GET /alerts
Retrieve active and historical alerts.

#### Query Parameters
- `status` = active | acknowledged | resolved
- `severity` = low | medium | high | critical
- `buildingId`
- `roomId`

#### Response
- Status: 200 OK
```json
{
  "alerts": [
    {
      "alertId": "ALT-001",
      "deviceId": "TEMP-AB-A-101",
      "buildingId": "BUILD-A",
      "roomId": "ROOM-101",
      "severity": "HIGH",
      "status": "ACTIVE",
      "createdAt": "2026-09-24T09:25:00Z"
    }
  ]
}
```

## 5. Dashboard APIs

### GET /dashboard
Provides key metrics for the landing dashboard.

#### Response
- Status: 200 OK
```json
{
  "campusHealth": "WARNING",
  "activeDevices": 126,
  "alertsOpen": 7,
  "energyUsageKwh": 840.5,
  "occupancyRate": 72.4,
  "waterLevelPercent": 68.1
}
```

## 6. Digital Twin APIs

### GET /digital-twin
Returns the campus digital twin state at a requested granularity.

#### Query Parameters
- `level` = campus | building | room | device
- `buildingId`
- `roomId`

#### Response
- Status: 200 OK
```json
{
  "level": "building",
  "buildingId": "BUILD-A",
  "status": "WARNING",
  "devicesOnline": 24,
  "alertCount": 3,
  "temperatureAverageC": 25.4,
  "occupancyRate": 69.1
}
```

## 7. Error Handling
The API shall use consistent error payloads:
```json
{
  "error": {
    "code": "DEVICE_NOT_FOUND",
    "message": "The requested device was not found.",
    "timestamp": "2026-09-24T09:30:00Z"
  }
}
```

## 8. Status Codes
- 200 OK: successful retrieval or update
- 201 Created: successful device creation
- 400 Bad Request: invalid request payload or validation failure
- 401 Unauthorized: missing or invalid authentication
- 403 Forbidden: user lacks required permission
- 404 Not Found: target resource does not exist
- 409 Conflict: duplicate registration or conflicting operation state
- 500 Internal Server Error: unexpected backend failure
