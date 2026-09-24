# Backend Design

## 1. Design Overview
The Java backend is the orchestration layer connecting MQTT ingestion, device state management, data persistence, alerting, digital twin modeling, and dashboard access.

## 2. Layered Design

### Controllers
- DeviceController
  - manages registration, update, enablement, retrieval
- AlertController
  - exposes current and historical alerts
- DashboardController
  - exposes aggregated metrics for user-facing dashboards
- DigitalTwinController
  - exposes campus hierarchy and live twin state
- AuthController
  - handles login and role-based access workflows
- ReportingController
  - handles report generation requests

### Services
- DeviceService
  - handles device lifecycle operations and validation
- TelemetryService
  - stores and validates incoming readings
- AlertService
  - determines threshold breaches and alert dispatch
- DigitalTwinService
  - maintains entity state and campus relationships
- ReportingService
  - aggregates metrics and prepares reports
- AuthenticationService
  - validates credentials and permission scopes

### Repositories
- DeviceRepository
- LocationRepository
- SensorReadingRepository
- AlertRepository
- ThresholdRepository
- UserRepository
- RoleRepository

### MQTT Layer
- MQTT consumer for telemetry topics
- MQTT consumer for device status topics
- MQTT producer for alert topic publication and commands
- message validation and schema enforcement
- retry and dead-letter handling for robust processing

### Alert Engine
- monitored metrics include temperature, occupancy, energy, parking, water, and air quality
- threshold evaluation against configured policy
- alert severity classification and deduplication
- alert acknowledgment and state transitions

### Digital Twin Engine
- keeps synchronized entity graph representing campus environment
- calculates live health states by aggregation from devices and rooms
- supports drill-down from campus to building to room to device
- exposes state snapshots for dashboard and reporting views

### Authentication Module
- user login and credential validation
- JWT or session-based token mechanism (design-level only)
- role-based access checks for admin, operator, viewer, and analytics roles

### Reporting Module
- aggregates historical data for building, room, and device views
- supports time-based and filter-based reporting
- prepares summary tables for dashboard and operational reports

## 3. Backend Integration Principles
- clear separation between ingestion, business logic, persistence, and presentation
- event-driven flow from MQTT to backend services
- central alert evaluation based on thresholds and status checks
- consistent API response structure and validation rules

## 4. Processing Flow
1. Device publishes telemetry to MQTT broker.
2. Java backend consumes message via MQTT connector.
3. Telemetry service validates payload and stores reading.
4. Alert engine checks metric thresholds and device health.
5. Digital twin engine updates entity state.
6. Dashboard and reporting modules read latest state from application services.
