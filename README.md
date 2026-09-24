# Smart Campus Digital Twin

## Project Overview
The Smart Campus Digital Twin is a software-only platform designed to model and monitor a modern campus environment through simulated IoT telemetry. The system integrates MQTT-based communications, Java backend services, MySQL storage, and a digital twin dashboard for operational awareness, alerting, and historical analysis.

## Objectives
- create a digital representation of the campus and key facilities
- simulate key IoT device families for environment, occupancy, energy, parking, water, and air quality
- process telemetry using a Java backend architecture
- provide a unified monitoring view for facilities and operations teams
- support alerting and simple reporting workflows
- construct a scalable foundation for future digital twin enhancements

## Architecture
The platform follows a layered architecture:
1. Simulator layer generates synthetic telemetry and device condition data.
2. MQTT layer distributes data, status, and alert messages.
3. Java backend layer validates, processes, persists, and correlates data.
4. MySQL layer stores users, locations, devices, readings, thresholds, and alerts.
5. Digital twin engine maintains the live campus state model.
6. Dashboard layer presents operational, historical, and alert-driven views.

## Technology Stack
- MQTT for event-driven telemetry communication
- Java Spring Boot for backend processing and API services
- MySQL for persistent storage
- Digital Twin modeling for campus entities and relationships
- Dashboard layer for monitoring, analytics, and alert center views
- Git and documentation-driven project governance for Phase 1 planning

## Development Phases
### Phase 1 - Requirement Analysis and Project Planning
- define the project scope, architecture, and requirements
- create the repository structure and design artifacts
- document functional and non-functional requirements
- define the campus model, MQTT strategy, and database design
- prepare the roadmap for implementation phases

### Phase 2 - Foundation and Implementation
- build backend, messaging, persistence, and service integration foundations
- implement simulator and telemetry generation
- establish MySQL schema and data flow
- connect dashboard to platform APIs

### Phase 3 - Operational Intelligence
- advanced analytics, alert workflows, and digital twin refinement
- operational reporting and historical analysis improvements
- performance tuning and production-grade monitoring

## Folder Structure
- `docs/` – project requirements, design, architecture, and planning documents
- `backend/` – future Java backend implementation
- `frontend/` – future dashboard and digital twin UI implementation
- `simulator/` – future synthetic telemetry generation and device simulation
- `database/` – future schema and persistence design artifacts
- `deployment/` – future deployment and environment configuration artifacts
- `tests/` – future validation and QA documentation

## MVP Scope
The MVP focuses on a limited yet representative smart campus setup:
- Temperature devices
- Occupancy devices
- Energy devices
- 5–10 virtual devices
- MQTT-based data flow
- Java backend processing design
- MySQL persistence design
- single digital twin dashboard

## Future Enhancements
- additional device classes like water and air quality in broader deployments
- predictive analytics and forecasting
- stronger automation and escalation workflows
- advanced reporting and executive dashboards
- deeper digital twin fidelity and simulation accuracy
- multi-campus and multi-building enterprise expansion

## Project Summary
This repository represents the foundational planning and design stage for the Smart Campus Digital Twin platform. It is intentionally structured to support a disciplined implementation roadmap without advancing into production code during Phase 1.
