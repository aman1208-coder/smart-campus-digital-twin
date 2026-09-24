# Device Catalog

## 1. Overview
This catalog defines device types, telemetry semantics, operational thresholds, and message design for the smart campus digital twin. Each device is represented as a logical asset associated with a campus building and room.

## 2. Device Types

### 2.1 Temperature Device
- Device IDs: `TEMP-AB-A-101`, `TEMP-AB-A-102`, `TEMP-LIB-201`
- MQTT Topics:
  - `campus/academic_block_a/room_101/temp/data`
  - `campus/academic_block_a/room_101/temp/status`
- Payload Example:
  - Data: `{ "deviceId": "TEMP-AB-A-101", "timestamp": "2026-09-24T09:00:00Z", "temperatureC": 23.4, "humidity": 52 }`
  - Status: `{ "deviceId": "TEMP-AB-A-101", "status": "ACTIVE", "batteryLevel": 92, "lastSeen": "2026-09-24T09:00:00Z" }`
- Thresholds:
  - warning if temperature > 28C or < 18C
  - critical if > 32C or < 15C
- Sampling Frequency: 60 seconds
- Status States: ACTIVE, INACTIVE, WARNING, CRITICAL, OFFLINE

### 2.2 Occupancy Device
- Device IDs: `OCC-AB-A-101`, `OCC-AUD-001`, `OCC-LIB-201`
- MQTT Topics:
  - `campus/academic_block_a/room_101/occupancy/data`
  - `campus/academic_block_a/room_101/occupancy/status`
- Payload Example:
  - Data: `{ "deviceId": "OCC-AB-A-101", "timestamp": "2026-09-24T09:05:00Z", "occupancyCount": 38, "capacity": 60, "occupancyRate": 63.3 }`
  - Status: `{ "deviceId": "OCC-AB-A-101", "status": "ACTIVE", "lastSeen": "2026-09-24T09:05:00Z" }`
- Thresholds:
  - warning if occupancy rate > 80%
  - critical if occupancy rate > 95%
- Sampling Frequency: 30 seconds
- Status States: ACTIVE, WARNING, FULL, OFFLINE

### 2.3 Energy Device
- Device IDs: `ENERGY-AB-A-101`, `ENERGY-PWR-001`, `ENERGY-LIB-201`
- MQTT Topics:
  - `campus/power_plant/switchgear/energy/data`
  - `campus/power_plant/switchgear/energy/status`
- Payload Example:
  - Data: `{ "deviceId": "ENERGY-PWR-001", "timestamp": "2026-09-24T09:10:00Z", "powerKw": 120.4, "energyKwh": 45.8, "loadFactor": 0.72 }`
  - Status: `{ "deviceId": "ENERGY-PWR-001", "status": "ACTIVE", "lastSeen": "2026-09-24T09:10:00Z" }`
- Thresholds:
  - warning if load factor > 0.8
  - critical if load factor > 0.95 or power spike exceeds configured limit
- Sampling Frequency: 60 seconds
- Status States: ACTIVE, DEGRADED, CRITICAL, OFFLINE

### 2.4 Parking Device
- Device IDs: `PARK-LOT-A-001`, `PARK-LOT-B-010`, `PARK-VIS-005`
- MQTT Topics:
  - `campus/parking_area/lot_a/parking/data`
  - `campus/parking_area/lot_a/parking/status`
- Payload Example:
  - Data: `{ "deviceId": "PARK-LOT-A-001", "timestamp": "2026-09-24T09:15:00Z", "occupiedSpaces": 110, "totalSpaces": 150, "occupancyRate": 73.3 }`
  - Status: `{ "deviceId": "PARK-LOT-A-001", "status": "ACTIVE", "lastSeen": "2026-09-24T09:15:00Z" }`
- Thresholds:
  - warning if occupancy rate > 85%
  - critical if occupancy rate >= 100%
- Sampling Frequency: 45 seconds
- Status States: ACTIVE, FULL, WARNING, OFFLINE

### 2.5 Water Level Device
- Device IDs: `WATER-TANK-001`, `WATER-TANK-002`, `WATER-OUT-001`
- MQTT Topics:
  - `campus/water_tank/reservoir/water/data`
  - `campus/water_tank/reservoir/water/status`
- Payload Example:
  - Data: `{ "deviceId": "WATER-TANK-001", "timestamp": "2026-09-24T09:20:00Z", "waterLevelPercent": 68.1, "volumeLiters": 123500 }`
  - Status: `{ "deviceId": "WATER-TANK-001", "status": "ACTIVE", "lastSeen": "2026-09-24T09:20:00Z" }`
- Thresholds:
  - warning if level < 40%
  - critical if level < 25%
- Sampling Frequency: 120 seconds
- Status States: ACTIVE, LOW, CRITICAL, OFFLINE

### 2.6 Air Quality Device
- Device IDs: `AQ-AB-A-101`, `AQ-LIB-201`, `AQ-AUD-001`
- MQTT Topics:
  - `campus/library/room_201/air_quality/data`
  - `campus/library/room_201/air_quality/status`
- Payload Example:
  - Data: `{ "deviceId": "AQ-LIB-201", "timestamp": "2026-09-24T09:25:00Z", "aqi": 76, "pm25": 18.4, "co2": 820, "voc": 0.6 }`
  - Status: `{ "deviceId": "AQ-LIB-201", "status": "ACTIVE", "lastSeen": "2026-09-24T09:25:00Z" }`
- Thresholds:
  - warning if AQI > 100 or CO2 > 1000 ppm
  - critical if AQI > 150 or CO2 > 1400 ppm
- Sampling Frequency: 60 seconds
- Status States: ACTIVE, WARNING, CRITICAL, OFFLINE

## 3. Common Device Status Model
All devices shall support the following conceptual states:
- ACTIVE
- INACTIVE
- WARNING
- DEGRADED
- CRITICAL
- OFFLINE
- DISABLED
- MAINTENANCE

## 4. Threshold Governance
Thresholds shall be configured centrally and associated with:
- device type
- building or room context
- operational policy
- severity classification

## 5. Device Catalog Governance
The device catalog must remain extensible to accommodate:
- additional sensor families
- dynamic room-level reclassification
- future building systems and HVAC integrations
- emergency and safety monitoring devices
