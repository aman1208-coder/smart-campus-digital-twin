# Digital Twin Design

## 1. Design Objective
The digital twin layer provides a synchronized, entity-based representation of the campus. It links physical spatial structure, devices, sensor streams, and operational events so users can reason about campus state across all dimensions.

## 2. Core Entities

### Campus Entity
- Purpose: top-level operational boundary for the entire site
- Attributes:
  - campus_id
  - name
  - location
  - timezone
  - status
  - created_at
- Relationships:
  - one campus contains many buildings
  - one campus contains many devices and alerts at a mapped aggregate level

### Building Entity
- Purpose: represents a physical building or operational block
- Attributes:
  - building_id
  - campus_id
  - name
  - code
  - address or zone
  - building type
  - status
- Relationships:
  - many rooms per building
  - many devices per building

### Room Entity
- Purpose: represents an individual room or zone inside a building
- Attributes:
  - room_id
  - building_id
  - room_number
  - room_type
  - floor
  - capacity
  - status
- Relationships:
  - one room contains many devices
  - one room can raise one or more alerts

### Device Entity
- Purpose: models a physical or simulated measurement asset
- Attributes:
  - device_id
  - device_type
  - building_id
  - room_id
  - status
  - last_seen
  - enabled
  - MQTT topic mapping
- Relationships:
  - many readings per device
  - many alerts per device
  - one device belongs to one room and one building

### Sensor Entity
- Purpose: models the telemetry source behind a measured metric
- Attributes:
  - sensor_id
  - device_id
  - metric_type
  - unit
  - threshold_min
  - threshold_max
  - sampling_frequency
  - status
- Relationships:
  - one sensor belongs to one device
  - many reading records per sensor

### Alert Entity
- Purpose: records abnormal or operationally significant states
- Attributes:
  - alert_id
  - device_id
  - location_id
  - alert_type
  - severity
  - message
  - status
  - created_at
  - acknowledged_at
- Relationships:
  - alerts are associated to a device, room, or building
  - alerts are derived from threshold violations or heartbeat anomalies

## 3. Digital Twin Data Model Principles
- stateful representation of assets and conditions
- room/building/device graph model for drill-down and context analysis
- timestamped telemetry for historical reconstruction
- explicit health and status semantics aligned with monitoring operations

## 4. Operational State Model
The digital twin should maintain the following conceptual states:
- Healthy
- Warning
- Critical
- Offline
- Disabled
- Maintenance

## 5. Relationship Rules
1. Each building belongs to one campus.
2. Each room belongs to one building.
3. Each device belongs to one room.
4. Each sensor belongs to one device.
5. Each reading is associated with one sensor at a specific timestamp.
6. Each alert is associated with one device or its parent location context.

## 6. Digital Twin Benefits
- supports real-time situational awareness
- supports root-cause analysis for events and anomalies
- enables centralized alerting and operational context
- creates the foundation for advanced analytics and predictive modeling
