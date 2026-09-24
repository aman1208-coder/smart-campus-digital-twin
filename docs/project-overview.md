# Project Overview

## 1. Vision
The Smart Campus Digital Twin project envisions a unified digital representation of a modern campus environment that transforms raw IoT telemetry into operational intelligence. By simulating and monitoring campus buildings, rooms, devices, and environmental conditions in near real time, the platform helps administrators detect inefficiencies, respond to anomalies, and optimize resource usage across academic, operational, and infrastructure domains.

## 2. Problem Statement
Campus operations are increasingly complex due to distributed facilities, high energy demand, occupant variability, parking pressure, water consumption, and environmental quality monitoring. Traditional monitoring systems are fragmented, slow to respond, and often lack a holistic model that correlates device behavior across buildings and systems.

The lack of a single campus-wide operational view results in:
- delayed facility response to critical events
- inefficient energy and water management
- poor visibility into occupancy trends and room usage
- limited predictive awareness for maintenance and capacity planning
- disconnected alerting and reporting workflows

## 3. Objectives
- Build a software-only digital twin for a smart campus ecosystem.
- Simulate IoT sensors and devices for key campus systems.
- Stream telemetry using MQTT-based communication patterns.
- Centralize event processing and telemetry handling in a Java-based backend.
- Model campus assets, buildings, rooms, and devices in a digital twin layer.
- Persist operational data in a relational system for analysis and reporting.
- Provide a dashboard for real-time monitoring and operational insight.
- Deliver actionable alerts based on threshold violations and device health conditions.

## 4. Scope
The platform covers the following campus domains:
- academic operations and classroom utilization
- building environmental monitoring
- energy consumption visibility
- parking occupancy and utilization
- water storage monitoring
- air quality and comfort conditions
- alerting, reporting, and digital twin visualization

### In Scope
- simulated IoT devices across campus assets
- MQTT-based telemetry and status messaging
- backend ingestion, validation, and persistence
- digital twin entity modeling
- alerts, dashboards, and historical analytics
- role-based campus monitoring workflow

### Out of Scope
- physical hardware deployment
- direct integration with live building management systems
- autonomous control of actuators beyond event orchestration
- advanced AI-driven predictive maintenance beyond planning phase
- custom mobile app development in Phase 1

## 5. Stakeholders
### Primary Stakeholders
- Campus operations team
- Facilities management team
- Security and safety administrators
- IT and infrastructure support team
- Building administrators

### Secondary Stakeholders
- Academic leadership
- Maintenance contractors
- Students and staff as end users of campus services
- Data analysts and reporting stakeholders
- System integrators and solution architects

## 6. Constraints
- The solution must be software-only and rely on simulated device telemetry.
- Communication pattern is expected to follow MQTT messaging semantics.
- Backend processing must be designed for Java Spring Boot architecture.
- Data must be persisted in a MySQL-compatible relational model.
- The platform must support campus-scale modeling without depending on live physical deployments.
- Phase 1 is documentation and planning only; no implementation code is produced.

## 7. Assumptions
- Each building contains multiple rooms with defined device coverage.
- Simulated devices publish telemetric updates on a consistent schedule.
- Device states and thresholds can be managed centrally.
- Campus administrators require both operational visibility and historical analytics.
- The dashboard is a business-facing visualization layer rather than a fully autonomous control console.
- MQTT topics follow a standardized naming pattern for routing and filtering.

## 8. Expected Outcomes
By the end of the project lifecycle, the platform is expected to provide:
- a campus-wide operational view of environmental, usage, and infrastructure indicators
- near real-time device telemetry monitoring
- automated alert generation for threshold breaches or unhealthy states
- historical insights for reporting and optimization decisions
- a clear digital twin representation of campus operations
- scalable foundations for future predictive analytics and advanced automation

## 9. Success Criteria
The project is considered successful when the platform demonstrates:
- complete device modeling across key campus systems
- reliable telemetry flow from simulator to backend to dashboard
- role-aware alert and monitoring workflow
- maintainable architecture across digital twin, backend, and data layers
- transparent documentation supporting implementation in later phases
