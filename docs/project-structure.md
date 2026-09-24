# Project Structure

## 1. Repository Root
The repository root contains the full Phase 1 planning artifact set for the Smart Campus Digital Twin project.

## 2. Folder Definitions

### `docs/`
Purpose: stores all planning, architecture, and specification documents for the project. This directory is the canonical source of requirements, use cases, data design, and system design.

### `backend/`
Purpose: reserved for the Java Spring Boot backend implementation work in later phases. This folder will hold source code, configuration, and service modules for controllers, services, repositories, MQTT consumers, alert processing, and reporting.

### `frontend/`
Purpose: reserved for the dashboard and digital twin user interface implementation in later phases. This directory will contain UI application assets, routing, components, state management, and dashboard views.

### `simulator/`
Purpose: reserved for device simulation logic and telemetry generation. This folder will house scripts or applications that generate MQTT payloads and status updates for temperature, occupancy, parking, water, and air quality sensors.

### `database/`
Purpose: reserved for data modeling artifacts, schema planning, migration planning, and database configuration documentation. This directory is not used for SQL generation in Phase 1, but it provides the structure for future schema and migration work.

### `deployment/`
Purpose: reserved for deployment artifacts, environment configuration, orchestration guidance, and infrastructure documentation for future application deployment and monitoring.

### `tests/`
Purpose: reserved for test plans, quality gates, and validation strategies for backend, MQTT, integration, and dashboard functionality in later phases.

## 3. Project Planning Intent
This structure intentionally separates implementation concerns so each phase can evolve independently while maintaining architectural alignment.

## 4. Expected Future Evolution
- backend: business logic, APIs, persistence, messaging integration
- frontend: interactive digital twin dashboard
- simulator: synthetic data generation and health simulation
- database: schema and backup/recovery design
- deployment: infrastructure, CI/CD, environment management
- tests: validation strategy for unit, integration, end-to-end, and performance checks
