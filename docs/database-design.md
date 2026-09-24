# Database Design

## 1. Design Objective
The database layer provides persistent storage for users, facility hierarchy, device metadata, sensor readings, thresholds, and alerts. The relational model supports both operational monitoring and historical reporting.

## 2. Core Entities

### Users
- Purpose: stores application users and role assignment
- Key fields:
  - user_id (PK)
  - username
  - password_hash
  - email
  - role
  - status
  - created_at

### Locations
- Purpose: models the campus hierarchy for spatial context
- Key fields:
  - location_id (PK)
  - parent_location_id (FK)
  - location_type
  - name
  - code
  - description
- Notes: supports campus, building, room, parking lot, and utility area representations

### Devices
- Purpose: stores operational metadata for devices and sensors
- Key fields:
  - device_id (PK)
  - location_id (FK)
  - device_type
  - status
  - enabled
  - last_seen
  - mqtt_topic
  - metadata_json

### SensorReadings
- Purpose: stores time-series measurement values and metadata
- Key fields:
  - reading_id (PK)
  - device_id (FK)
  - metric_name
  - metric_value
  - unit
  - captured_at
  - quality_flag

### Alerts
- Purpose: stores event and incident records generated from thresholds or device issues
- Key fields:
  - alert_id (PK)
  - device_id (FK, nullable)
  - location_id (FK, nullable)
  - alert_type
  - severity
  - message
  - status
  - created_at
  - acknowledged_at
  - resolved_at

### Thresholds
- Purpose: stores policy thresholds by metric and device type
- Key fields:
  - threshold_id (PK)
  - device_type
  - metric_name
  - min_value
  - max_value
  - severity
  - active
  - created_at

## 3. PK/FK Mapping
- Users: `user_id` PK
- Locations: `location_id` PK; `parent_location_id` FK to `Locations.location_id`
- Devices: `device_id` PK; `location_id` FK to `Locations.location_id`
- SensorReadings: `reading_id` PK; `device_id` FK to `Devices.device_id`
- Alerts: `alert_id` PK; `device_id` FK to `Devices.device_id`; `location_id` FK to `Locations.location_id`
- Thresholds: `threshold_id` PK

## 4. Relationships
- One campus contains many buildings and rooms.
- One building contains many rooms.
- One room contains many devices.
- One device produces many sensor readings.
- One device may raise many alerts.
- One location may be associated with many alerts.
- Thresholds are referenced by device type and metric name for alert evaluation.

## 5. ER Diagram
```mermaid
erDiagram
    USERS ||--o{ : "role-based access"
    LOCATIONS ||--o{ DEVICES : contains
    LOCATIONS ||--o{ LOCATIONS : parent_child
    LOCATIONS ||--o{ ALERTS : scoped_to
    DEVICES ||--o{ SENSORREADINGS : emits
    DEVICES ||--o{ ALERTS : triggers
    DEVICES ||--o{ THRESHOLDS : configures

    USERS {
        bigint user_id PK
        varchar username
        varchar email
        varchar role
        varchar status
    }

    LOCATIONS {
        bigint location_id PK
        bigint parent_location_id FK
        varchar location_type
        varchar name
        varchar code
    }

    DEVICES {
        bigint device_id PK
        bigint location_id FK
        varchar device_type
        varchar status
        boolean enabled
        timestamp last_seen
    }

    SENSORREADINGS {
        bigint reading_id PK
        bigint device_id FK
        varchar metric_name
        decimal metric_value
        varchar unit
        timestamp captured_at
    }

    ALERTS {
        bigint alert_id PK
        bigint device_id FK
        bigint location_id FK
        varchar alert_type
        varchar severity
        text message
        varchar status
        timestamp created_at
    }

    THRESHOLDS {
        bigint threshold_id PK
        varchar device_type
        varchar metric_name
        decimal min_value
        decimal max_value
        varchar severity
        boolean active
    }
```

## 6. Storage Principles
- Use indexed timestamps for time-series efficiency.
- Keep location and device metadata normalized.
- Separate operational alerts from telemetry data to preserve reporting integrity.
- Support future growth with clear referential constraints and partitioning strategy considerations.
