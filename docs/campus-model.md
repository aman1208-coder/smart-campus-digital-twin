# Campus Model

## 1. Campus Structure
The campus is modeled as a hierarchical digital twin with site-level, building-level, room-level, and device-level relationships.

### Top-Level Campus
- Campus Name: Smart Campus Digital Twin
- Geography: Multi-building educational and operational site
- Operational Focus: environment, utilization, energy, safety, and services

## 2. Campus Asset Hierarchy

### Academic Block A
- Purpose: lecture halls, classrooms, faculty offices, and technical labs
- Typical room types:
  - lecture rooms
  - seminar rooms
  - faculty offices
  - lab spaces
- Device classes:
  - temperature sensors
  - occupancy sensors
  - energy and lighting monitors
  - air quality sensors

### Academic Block B
- Purpose: second teaching block with mixed-use classroom and research spaces
- Typical room types:
  - classrooms
  - laboratories
  - tutorial rooms
  - student collaboration spaces
- Device classes:
  - temperature and ventilation sensors
  - occupancy counters
  - energy meters

### Library
- Purpose: reading, research, and digital study environment
- Typical room types:
  - reading halls
  - study rooms
  - archives
  - circulation areas
- Device classes:
  - occupancy monitoring
  - environmental comfort sensors
  - air quality monitoring

### Auditorium
- Purpose: events, assemblies, and large meetings
- Typical room types:
  - main hall
  - stage area
  - foyer
  - backstage support spaces
- Device classes:
  - occupancy tracking
  - environmental control sensors
  - energy usage monitoring

### Parking Area
- Purpose: vehicle occupancy and parking utilization tracking
- Typical zones:
  - staff parking
  - student parking
  - visitor parking
  - EV parking bays
- Device classes:
  - parking sensors
  - occupancy counters
  - entry/exit monitors

### Water Tank
- Purpose: campus water storage and monitoring
- Typical zones:
  - storage reservoir
  - overflow monitoring
  - supply lines
  - inspection points
- Device classes:
  - water level sensors
  - tank status sensors
  - threshold alarm devices

### Power Plant
- Purpose: central utility and energy generation/monitoring
- Typical zones:
  - generator bay
  - switchgear area
  - transformer zones
  - energy monitoring rooms
- Device classes:
  - energy meters
  - equipment health sensors
  - load monitoring devices

## 3. Rooms and Spatial Model
Each building contains rooms with metadata including:
- room identifier
- room type
- floor
- maximum capacity
- occupancy policy
- environmental requirements
- associated devices

## 4. Device and Sensor Model
Each room may contain multiple devices and sensors. Device associations are tracked by:
- building
- room
- physical placement
- system type
- health state
- threshold profile

## 5. Metrics
The digital twin tracks the following metrics across campus entities:
- temperature in degrees Celsius
- occupancy count or percentage
- energy consumption in kWh or usage rate
- parking occupancy rate
- water level as a percentage or volume
- air quality index, PM2.5, CO2, and VOC indicators
- device availability and heartbeat status
- alert count and severity by building or room

## 6. Campus Operational View
The platform supports filtering and aggregation at the following levels:
- campus level: aggregate health and trends
- building level: building conditions and metrics
- room level: room-specific safety and usage metrics
- device level: current reading, status, health, and threshold compliance

## 7. Data Modeling Considerations
- every physical location belongs to the campus hierarchy
- every device belongs to one location and one device class
- every reading belongs to a sensor or device event stream
- every alert belongs to a device, room, or building context
- operational thresholds are managed centrally and used by alerting and analytics
