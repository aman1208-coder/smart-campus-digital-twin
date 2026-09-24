# MQTT Design

## 1. Communication Overview
MQTT is used as the telemetry and event backbone for simulated device data, service status, commands, and alert propagation. All message flows are designed to align with campus-scale monitoring and operational awareness.

## 2. Topics

### 2.1 Telemetry Topics
- `campus/{building}/{room}/{device}/data`
- Purpose: contains the regular telemetry payload from the device
- Example: `campus/academic_block_a/room_101/temp/data`

### 2.2 Status Topics
- `campus/{building}/{room}/{device}/status`
- Purpose: contains availability, operational state, and last seen metadata
- Example: `campus/academic_block_a/room_101/temp/status`

### 2.3 Alert Topic
- `campus/alerts`
- Purpose: publishes alert events derived from thresholds or system anomalies

### 2.4 Command Topic
- `campus/commands`
- Purpose: carries control or configuration directives for future workflows

### 2.5 Heartbeat Topic
- `campus/heartbeat`
- Purpose: indicates that a node, service, or device is alive and reporting

## 3. Publishers and Subscribers

### Publishers
- Simulation services generate telemetry for each device type.
- Device monitoring agents publish device status updates.
- Alert engine publishes alert events to the `campus/alerts` topic.
- Backend service publishes operational commands or orchestration signals when required.

### Subscribers
- Java backend consumers subscribe to telemetry and health topics.
- Alert processing components subscribe to `campus/alerts`.
- Dashboard services may subscribe to aggregated state topics and alert feeds.
- Command consumers listen on `campus/commands` for control events.

## 4. Quality of Service (QoS)
- QoS 0: suitable for heartbeat and non-critical telemetry if message loss is acceptable.
- QoS 1: recommended for telemetry and alert delivery to avoid data loss.
- QoS 2: recommended for critical control or resolution events when strict delivery is required.

## 5. Retained Messages
- Retained messages are recommended for status and configuration topics to preserve last-known state.
- Retained telemetry payloads may be used selectively for last known readings, but should be applied carefully to avoid stale state confusion.
- `campus/alerts` should not be retained in a way that causes historical alerts to appear as current active conditions.

## 6. Security
- Use TLS for all broker communication.
- Require authentication and authorization for publishers and subscribers.
- Use role-specific topic access where possible.
- Validate payload schemas before ingesting telemetry into backend services.
- Ensure backend commands are filtered and audited.

## 7. Operational Considerations
- Use topic namespaces consistent with campus hierarchy and building mappings.
- Keep payload schemas consistent across device classes.
- Add device metadata and timestamp fields to every message.
- Use standardized error and health statuses to prevent parsing ambiguity.

## 8. MQTT Design Principles
- deterministic topics
- standardized message contracts
- low-latency communication for operations
- support for future air gap, failover, or multi-tenant environments
