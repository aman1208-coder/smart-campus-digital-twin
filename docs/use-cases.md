# Use Cases

## 1. Use Case: Login
- Actor: Campus Operator / Administrator
- Preconditions: The user has a valid account and the application is available.
- Main Flow:
  1. User opens the application.
  2. User enters username and password.
  3. System validates credentials.
  4. System grants access based on assigned role.
  5. User lands on the main dashboard.
- Alternate Flow:
  1. Invalid credentials are entered.
  2. System shows an authentication error.
  3. User retries or resets credentials.
- Postconditions: The user is authenticated and can access permitted campus monitoring functions.

## 2. Use Case: Device Registration
- Actor: Administrator
- Preconditions: User is authenticated and has permission to configure devices.
- Main Flow:
  1. Administrator navigates to device registration view.
  2. Administrator enters device metadata including ID, type, building, room, and MQTT configuration.
  3. System validates completeness and uniqueness.
  4. System stores the device registration in the platform.
  5. Device becomes available for monitoring.
- Alternate Flow:
  1. Device data is incomplete or duplicate.
  2. System rejects the registration and prompts for corrections.
- Postconditions: The device is available in the digital twin model and can begin publishing readings.

## 3. Use Case: Device Monitoring
- Actor: Campus Operator
- Preconditions: Devices are registered and connected to monitoring flow.
- Main Flow:
  1. Operator opens device monitoring view.
  2. System displays active devices, health indicators, and current telemetry.
  3. Operator filters by building, room, or device type.
  4. Operator inspects status and reading trends.
- Alternate Flow:
  1. A device is offline or degraded.
  2. System highlights the issue and displays a health warning.
- Postconditions: Operator has a current understanding of device operational health and telemetry state.

## 4. Use Case: Enable/Disable Device
- Actor: Administrator
- Preconditions: Device already exists in the registry.
- Main Flow:
  1. Administrator selects a device.
  2. Administrator toggles the device enablement state.
  3. System updates the operational status.
  4. System reflects the updated state in the digital twin and monitoring views.
- Alternate Flow:
  1. Device is in a critical state and cannot be disabled.
  2. System prompts for confirmation or prevents the action.
- Postconditions: The device is either actively monitored or excluded from operational monitoring.

## 5. Use Case: Alert Management
- Actor: Campus Operator / Administrator
- Preconditions: At least one threshold or uptime rule is configured.
- Main Flow:
  1. System detects alert condition from telemetry or heartbeat status.
  2. System creates alert with severity, time, and affected location.
  3. Operator views alert center and triages the issue.
  4. Operator acknowledges or escalates the alert.
  5. System records the resolution workflow.
- Alternate Flow:
  1. Alert is stale or duplicate.
  2. System suppresses duplicate events and marks the original alert as active.
- Postconditions: Alert is resolved, acknowledged, or escalated with audit trail retained.

## 6. Use Case: Historical Analytics
- Actor: Analyst / Campus Manager
- Preconditions: Telemetry history is available in storage.
- Main Flow:
  1. User selects analytics view.
  2. User chooses a metric, building, and time range.
  3. System retrieves historical records and aggregates trend data.
  4. System displays charts and summary analysis.
- Alternate Flow:
  1. Data is incomplete for a given time period.
  2. System displays partial data with a warning marker.
- Postconditions: User gains analytical insight into historical conditions and trends.

## 7. Use Case: Digital Twin Monitoring
- Actor: Administrator / Operator
- Preconditions: Campus model and devices are registered.
- Main Flow:
  1. User opens digital twin dashboard.
  2. System renders entity relationships for campus, buildings, rooms, and devices.
  3. User explores a building or room and views live status.
  4. System updates visualization based on live telemetry.
- Alternate Flow:
  1. A device is missing or disconnected.
  2. System highlights the entity in a stale or unknown state.
- Postconditions: User can visualize the dynamic health of the campus environment.

## 8. Use Case: Report Generation
- Actor: Campus Manager / Analyst
- Preconditions: Historical data and report parameters are available.
- Main Flow:
  1. User selects reporting module.
  2. User selects date range, facility area, and report type.
  3. System compiles aggregated operational metrics and alert summaries.
  4. System presents the report or exports it in a supported format.
- Alternate Flow:
  1. Requested data is too sparse or not available.
  2. System informs the user and suggests a broader time range.
- Postconditions: User receives a documented summary of campus operational performance.

## 9. Summary of Core Actors
- Administrator: device configuration, access control, operational oversight
- Campus Operator: real-time monitoring, alert triage, issue resolution
- Analyst: historical data review, trend analysis, report generation
- Viewer: read-only dashboard access for general monitoring
