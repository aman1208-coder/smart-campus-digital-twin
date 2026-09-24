# Minimum Viable Product (MVP)

## 1. MVP Objective
The MVP establishes the essential smart campus digital twin foundation with a limited but representative set of campus IoT devices and operational views.

## 2. MVP Scope
The Phase 1 MVP includes the following device classes:
- Temperature devices
- Occupancy devices
- Energy devices

## 3. Device Coverage
- 5–10 virtual devices across the selected device classes
- representative room and building coverage
- single dashboard with basic building and room monitoring
- telemetry ingestion over MQTT
- centralized backend ingestion and persistence design
- MySQL-based data storage planning
- live digital twin view for active monitoring

## 4. Core Functional Requirements for MVP
- device registration and status tracking
- telemetry ingestion for temperature, occupancy, and energy data
- threshold evaluation and basic alert generation
- dashboard overview with live status indicators
- simple building-level and room-level drill-down
- historical data retention for trend analysis
- role-aware read access to the dashboard

## 5. Technology Choices for MVP
- MQTT for message transport and telemetry publishing
- Java backend for processing and business logic
- MySQL for persistence and reporting data stores
- single dashboard for operational view and alert visibility

## 6. Out-of-Scope for MVP
- advanced AI analytics
- full autonomous control operations
- large-scale multi-campus deployment
- full device lifecycle orchestration beyond essential monitoring
- expanded device families beyond the initial three categories

## 7. Success Criteria for MVP
The MVP is successful when it demonstrates:
- multiple virtual devices reporting telemetry
- operational dashboard visibility across the monitored campus area
- active alerting based on threshold conditions
- stable backend persistence and data retrieval flow
- a clear foundation for future device expansion and analytics modules
