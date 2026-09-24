# Dashboard Design

## 1. Dashboard Wireframe

```text
+--------------------------------------------------------------------------------------+
| Smart Campus Digital Twin                              [Search] [Alerts: 7] [User] |
+--------------------------------------------------------------------------------------+
| Campus Overview | Buildings | Rooms | Devices | Analytics | Reports | Digital Twin |
+--------------------------------------------------------------------------------------+
| KPI Cards:                                                                       |
| Temperature avg 24.8C | Occupancy 72% | Energy 840kWh | Water 68% | Air Quality 76 |
+--------------------------------------------------------------------------------------+
| Campus Map / Building status panel                    | Alerts Center                 |
| - Academic Block A: Warning                          | - Temp anomaly (Room 101)    |
| - Academic Block B: Stable                          | - Parking 100% full          |
| - Library: Moderate                                | - Water tank low warning     |
| - Auditorium: Stable                                | - AQI elevated               |
| - Parking: Full                                     | - Device offline            |
| - Water Tank: Warning                               |                             |
| - Power Plant: Stable                               |                             |
+--------------------------------------------------------------------------------------+
| Recent Activity / Real-time Feed                          | Device Summary             |
| 09:40 TEMP-AB-A-101 -> 29.5C WARN                        | Sensor count: 126         |
| 09:41 OCC-LIB-201 -> 81% FULL                           | Active devices: 98       |
| 09:42 ENERGY-PWR-001 -> 0.91 load HIGH                  | Alerts: 7                 |
| 09:43 PARK-LOT-A-001 -> 100% occupancy                  | Critical devices: 2      |
+--------------------------------------------------------------------------------------+
```

## 2. Building View Wireframe

```text
+-----------------------------------------------------------------------+
| Academic Block A                                [Back] [Filter] |
+-----------------------------------------------------------------------+
| Floor 1 | Floor 2 | Floor 3 | Room Health Summary                    |
+-----------------------------------------------------------------------+
| Room 101: Temp 29.5C Warning    | Room 104: Occupancy 70%            |
| Room 102: Temp 24.1C Stable    | Room 105: Energy 0.78 load         |
| Room 103: AQI 88 Normal        | Room 106: Air Quality 92          |
| Room 107: Device Offline       | Room 108: Stable                   |
+-----------------------------------------------------------------------+
| Trend Charts: temperature / occupancy / energy                      |
+-----------------------------------------------------------------------+
```

## 3. Room View Wireframe

```text
+-----------------------------------------------------------------------+
| Room 101 - Academic Block A                                  [Back] |
+-----------------------------------------------------------------------+
| Current Metrics: Temp 29.5C | Humidity 52% | Occupancy 35/60         |
| Device Health: Temp Sensor: Warning | Occupancy: Active               |
+-----------------------------------------------------------------------+
| Device List:                                                         |
| TEMP-AB-A-101 | Occupancy: 35 | Status: WARNING                       |
| OCC-AB-A-101 | Occupancy 35/60 | Status: ACTIVE                      |
| AQ-AB-A-101 | AQI 88 | Status: ACTIVE                                |
+-----------------------------------------------------------------------+
| Historical Trend Panel                                               |
+-----------------------------------------------------------------------+
```

## 4. Device View Wireframe

```text
+-----------------------------------------------------------------------+
| TEMP-AB-A-101 - Temperature Sensor                           [Back] |
+-----------------------------------------------------------------------+
| Device Metadata: ID | Type | Building | Room | Status | Last Seen     |
| TEMP-AB-A-101 | Temperature | Block A | Room 101 | WARNING | 09:40     |
+-----------------------------------------------------------------------+
| Live Reading: 29.5C         | Threshold: 28C Warning | 32C Critical     |
| Alert history: 3 warnings in last 24h                                  |
| MQTT topic: campus/academic_block_a/room_101/temp/data                |
+-----------------------------------------------------------------------+
| Trend Graph | Threshold comparison | Event Log                        |
+-----------------------------------------------------------------------+
```

## 5. Alert Center Wireframe

```text
+-----------------------------------------------------------------------+
| Alert Center                                                  [Filter] |
+-----------------------------------------------------------------------+
| Severity | Device | Building | Room | Status | Time                  |
| CRITICAL | WATER-TANK-001 | Water Tank | Reservoir | ACTIVE | 09:36 |
| HIGH     | TEMP-AB-A-101 | Block A | Room 101 | ACTIVE | 09:40 |
| MEDIUM   | AQ-LIB-201 | Library | Room 201 | ACTIVE | 09:38 |
| LOW      | PARK-LOT-A-001 | Parking | Lot A | ACTIVE | 09:41 |
+-----------------------------------------------------------------------+
| Selected Alert Detail:                                                |
| Cause: Temperature threshold exceeded                                   |
| Action: acknowledge and dispatch maintenance review                   |
+-----------------------------------------------------------------------+
```

## 6. Analytics Page Wireframe

```text
+-----------------------------------------------------------------------+
| Analytics Dashboard                                  [Date Range] |
+-----------------------------------------------------------------------+
| Building selector | Metric selector | Report type | Export button      |
+-----------------------------------------------------------------------+
| Occupancy Trend (7D) | Energy Usage (7D) | Water Level (30D)          |
| [Line Chart]         | [Bar Chart]       | [Area Chart]                 |
+-----------------------------------------------------------------------+
| Top anomalies and KPIs                                                 |
| - Peak occupancy: 96% on Tuesday                                      |
| - Energy spike: +18% vs previous week                                  |
| - Water reserve below threshold for 2 days                             |
+-----------------------------------------------------------------------+
```

## 7. Dashboard UX Principles
- consistent color coding for severity and device state
- drill-down navigation from campus to device level
- clear operational alerts prioritized at top of page
- role-based visibility for administrators and viewers
- responsive layout for operational monitoring use cases
