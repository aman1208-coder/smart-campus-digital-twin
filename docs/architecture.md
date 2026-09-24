# Architecture

## 1. High-Level Architecture
```mermaid
flowchart LR
    S[Simulator]
    M[MQTT Broker]
    B[Java Backend]
    DB[(MySQL)]
    DT[Digital Twin Engine]
    D[Dashboard]
    A[Alerting]

    S -->|Telemetry / Status| M
    M -->|Messages| B
    B -->|Persist| DB
    B -->|State| DT
    DT -->|Live state| D
    B -->|Alert Events| A
    A -->|Notifications| D
```

## 2. Data Flow
```mermaid
flowchart TD
    D1[Device Data]
    D2[Telemetry Validation]
    D3[Persistence Layer]
    D4[Dashboard Queries]
    D5[Analytics]
    D6[Alerts]

    D1 --> D2 --> D3
    D3 --> D4
    D3 --> D5
    D3 --> D6
    D6 --> D4
```

## 3. MQTT Flow
```mermaid
flowchart LR
    SIM[Simulated Device]
    TOPIC[MQTT Topics]
    BROKER[MQTT Broker]
    SUB[Backend Consumer]
    VALID[Validation]
    PROC[Processing]

    SIM -->|campus/{building}/{room}/{device}/data| TOPIC
    SIM -->|campus/{building}/{room}/{device}/status| TOPIC
    TOPIC --> BROKER
    BROKER --> SUB
    SUB --> VALID --> PROC
```

## 4. Backend Flow
```mermaid
flowchart TD
    API[API Layer]
    CTRL[Controllers]
    SVC[Services]
    MSG[MQTT Integration]
    DB[(MySQL)]
    DT[Digital Twin Engine]
    AL[Alert Engine]
    REP[Reporting]
    DASH[Dashboard]

    API --> CTRL --> SVC
    SVC --> MSG
    SVC --> DB
    SVC --> DT
    SVC --> AL
    AL --> REP
    DT --> DASH
    REP --> DASH
```

## 5. Workflow
Simulator
↓
MQTT
↓
Java Backend
↓
MySQL
↓
Digital Twin
↓
Dashboard
↓
Alerts

## 6. Architectural Principles
- decouple simulation, messaging, processing, and visualization
- centralize domain rules in backend services
- preserve campus hierarchy and operational relationships in the digital twin model
- maintain clear notification and reporting pathways for alerts and trends
