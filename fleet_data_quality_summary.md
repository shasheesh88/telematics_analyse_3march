# Telematics Data — Exploratory Data Analysis Report

## Dataset Overview

| Parameter | Value |
|---|---|
| Total Records | 200,077 |
| Total Columns | 169 |
| Unique Vehicles (VEHICLE_ID) | 6,504 |
| Unique Organisations (ORG_ID) | 574 |
| Unique Drivers (DRIVER_ID) | 6,504 |
| Period Start | 2026-01-01 |
| Period End | 2026-01-31 |
| All Column Dtypes | object (169 columns) |

---

## Module 1 — Dataset Summary and Duration Analysis

Each record is expected to represent a full calendar day per vehicle, with a duration of exactly 23:59:59 (86,399 seconds). 199,994 records carry the expected duration. 83 records (0.04%) have non-standard durations ranging from approximately 2.5 hours to 13 hours. In all 83 cases, `SUMMARY_END_TIME` is 18:29:59 while `SUMMARY_START_TIME` falls mid-day, resulting in a partial-day window. No datetime parse errors were found.

**Sample — Records with Duration != 23:59:59**

| ID | VEHICLE_ID | SUMMARY_START_TIME | SUMMARY_END_TIME | DURATION (HH:MM:SS) |
|---|---|---|---|---|
| 4779 | 35552 | 2026-01-01 11:48:11 | 2026-01-01 18:29:59 | 06:41:48 |
| 5117 | 35551 | 2026-01-01 11:47:07 | 2026-01-01 18:29:59 | 06:42:52 |
| 6159 | 35553 | 2026-01-01 11:55:25 | 2026-01-01 18:29:59 | 06:34:34 |
| 6393 | 35550 | 2026-01-01 10:36:27 | 2026-01-01 18:29:59 | 07:53:32 |
| 12216 | 35554 | 2026-01-02 05:50:34 | 2026-01-02 18:29:59 | 12:39:25 |
| 18581 | 35556 | 2026-01-03 09:49:24 | 2026-01-03 18:29:59 | 08:40:35 |
| 19217 | 35555 | 2026-01-03 05:16:53 | 2026-01-03 18:29:59 | 13:13:06 |
| 19232 | 35557 | 2026-01-03 10:49:02 | 2026-01-03 18:29:59 | 07:40:57 |
| 28390 | 35559 | 2026-01-05 11:33:45 | 2026-01-05 18:29:59 | 06:56:14 |
| 30425 | 35561 | 2026-01-05 12:01:16 | 2026-01-05 18:29:59 | 06:28:43 |

---

## Module 2 — Structural Checks

### 2.1 Always-NULL Columns

5 columns are entirely null across all 200,077 records.

| Column | Null Count | Null % |
|---|---|---|
| MAX_HYDRAULIC_OCCURANCE_TIME | 200,077 | 100.00% |
| MAX_ENG_COOLANT_OCCURANCE_TIME | 200,077 | 100.00% |
| DRIVER_USER_ID | 200,077 | 100.00% |
| TRIP_START_ADDRESS | 200,077 | 100.00% |
| TRIP_END_ADDRESS | 200,077 | 100.00% |

### 2.2 Constant-Value Columns (All Zero)

62 columns hold the value zero across every single record. These span fuel ratios, alert counts, engine hours, fuel sensor fields, EV/CAN fields, power/charge fields, and overtime fields.

| Column | Value | Count |
|---|---|---|
| STOP_COUNT_MINS | 0 | 200,077 |
| IDLE_AC_COUNT_MINS | 0 | 200,077 |
| START_HRLFC | 0 | 200,077 |
| END_HRLFC | 0 | 200,077 |
| AVG_FUEL_CONSUMED_KM_HR | 0 | 200,077 |
| AVG_FUEL_CONSUMED_LH | 0 | 200,077 |
| IDLE_FUEL_PERCENT | 0 | 200,077 |
| MOVE_FUEL_PERCENT | 0 | 200,077 |
| IDLE_AC_ALERT_COUNT | 0 | 200,077 |
| FUEL_ALERT_COUNT | 0 | 200,077 |
| HARSH_ALERT_COUNT | 0 | 200,077 |
| OIL_PRESURE_ALERT_COUNT | 0 | 200,077 |
| ENGINE_SPEED_ALERT_COUNT | 0 | 200,077 |
| OVER_STEERING_ALERT_COUNT | 0 | 200,077 |
| SERVICE_ALERT_COUNT | 0 | 200,077 |
| SIM_REMOVAL_ALERT_COUNT | 0 | 200,077 |
| TAMPER_ALERT_COUNT | 0 | 200,077 |
| IDLE_ENGINE_HOURS | 0 | 200,077 |
| MOVE_ENGINE_HOURS | 0 | 200,077 |
| TOTAL_ENGINE_HOURS | 0 | 200,077 |
| START_FLS_LEVEL | 0 | 200,077 |
| END_FLS_LEVEL | 0 | 200,077 |
| SENSOR_REFUELED | 0 | 200,077 |
| FUEL_USED_HRLFC | 0 | 200,077 |
| FUEL_ECONOMY_TRIP_A | 0 | 200,077 |
| WORKING_MINS | 0 | 200,077 |
| BREAKER_OPERATING_MINS | 0 | 200,077 |
| MAX_HYDRAULIC_OIL_TEMP | 0 | 200,077 |
| AVERAGE_GFC | 0 | 200,077 |
| FUEL_USED_GFC | 0 | 200,077 |
| BREAKING_WARNING_COUNT | 0 | 200,077 |
| HIGH_SPEED_SHUTDOWN_COUNT | 0 | 200,077 |
| HIGH_COOLANT_SHUTDOWN_COUNT | 0 | 200,077 |
| POWER_MODE_1_MINS | 0 | 200,077 |
| POWER_MODE_2_MINS | 0 | 200,077 |
| POWER_MODE_1_TYPE | 0 | 200,077 |
| POWER_MODE_2_TYPE | 0 | 200,077 |
| CHARGE_MINS | 0 | 200,077 |
| CHARGE_COUNT | 0 | 200,077 |
| TOTAL_HOURMETER_SEC | 0 | 200,077 |
| BATTERY_ENERGY_CONSUMED | 0 | 200,077 |
| STATE_OF_HEALTH | 0 | 200,077 |
| BATTERY_ENERGY_MAX | 0 | 200,077 |
| BATTERY_TEMPERATURE_MAX | 0 | 200,077 |
| RESIDUAL_CAPACITY_CONSUMED | 0 | 200,077 |
| CAN_DISTANCE_PER_CAPACITY | 0 | 200,077 |
| DISTANCE_PER_CAPACITY | 0 | 200,077 |
| MOVE_ENERGY_CONSUMED | 0 | 200,077 |
| IDLE_ENERGY_CONSUMED | 0 | 200,077 |
| STOP_ENERGY_CONSUMED | 0 | 200,077 |
| CHARGING_COUNT | 0 | 200,077 |
| CHARGING_MINS | 0 | 200,077 |
| TARGETED_DIST | 0 | 200,077 |
| OVER_TIME_DISTANCE_TRAVELLED_TEST | 0 | 200,077 |
| OVER_TIME_OFFLINE_COUNT | 0 | 200,077 |
| OVER_TIME_OFFLINE_MINS | 0 | 200,077 |
| IS_TWOTHIRTY_AM | 0 | 200,077 |

### 2.3 Near-Constant Columns (>=99% Same Value)

24 columns have 99% or more of their values as zero.

| Column | Top Value | Top Value % |
|---|---|---|
| WORKING_OFFLINE_MINS | 0 | 100.00% |
| DRIVER_SCORE | 0 | 100.00% |
| IMPACT_ALERT_COUNT | 0 | 99.98% |
| IDLE_AC_COUNT | 0 | 99.96% |
| IDLE_AC_MINS | 0 | 99.96% |
| TRIP_REFILL_EVENT | 0 | 99.94% |
| TRIP_FUEL_REFILL_VALUE | 0 | 99.94% |
| MAX_RPM_OIL_PRESSURE | 0 | 99.93% |
| AVG_ENG_OIL_PRESSURE | 0 | 99.92% |
| MAX_ENG_OIL_PRESSURE | 0 | 99.92% |
| REVERSE_MOVE_MINS | 0 | 99.84% |
| CAN_DISTANCE_TRAVELLED | 0 | 99.83% |
| WORKING_DISTANCE_TRAVELLED | 0 | 99.82% |
| IDLE_ALERT_COUNT | 0 | 99.82% |
| CAN_START_ODOMETER | 0 | 99.80% |
| CAN_END_ODOMETER | 0 | 99.80% |
| FUEL_CONSUMED | 0 | 99.79% |
| OVER_TIME_DISTANCE_TRAVELLED | 0 | 99.73% |
| OVER_TIME_MOVE_MINS | 0 | 99.63% |
| OVER_TIME_MOVE_COUNT | 0 | 99.63% |
| OVER_TIME_STOP_COUNT | 0 | 99.60% |
| OVER_TIME_STOP_MINS | 0 | 99.59% |
| OVER_TIME_IDLE_COUNT | 0 | 99.57% |
| OVER_TIME_IDLE_MINS | 0 | 99.57% |

### 2.4 Partial-NULL Columns

| Column | Null Count | Null % |
|---|---|---|
| TRIP_END_TIME_DAY | 89,711 | 44.84% |
| TRIP_START_TIME_DAY | 88,597 | 44.28% |
| END_LOCATION | 70,643 | 35.31% |
| START_LOCATION | 70,643 | 35.31% |
| FREQUENT_SPEED | 70,643 | 35.31% |
| AD_BLUE_CONSUMPTION | 70,643 | 35.31% |
| DEALER_NAME | 42,363 | 21.17% |
| RESELLER_NAME | 79 | 0.04% |

---

## Module 3 — Duplicate Checks

### 3.1 Checks with No Issues

- Full row duplicates: 0
- Duplicate primary key (ID): 0
- Duplicate VEHICLE_ID + CREATED_DATE: 0

### 3.2 Duplicate VIN_NUMBER + CREATED_DATE — 6,136 Records (3.07%)

6,136 records share a VIN and date combination with at least one other record, meaning a single physical vehicle (VIN) is registered under more than one VEHICLE_ID in the system.

**Sample Records**

| ID | VEHICLE_ID | VIN_NUMBER | CREATED_DATE | VEHICLE_NO |
|---|---|---|---|---|
| 32 | 29176 | DL1LAC7303 | 2026-01-01 | DL1LAC7303 |
| 37 | 29171 | DL1LAB0484 | 2026-01-01 | DL1LAB0484 |
| 38 | 29172 | DL1LAB0931 | 2026-01-01 | DL1LAB0931 |
| 41 | 29169 | AS01EV6926 | 2026-01-01 | AS01EV6926 |
| 42 | 29179 | DL1LAD8977 | 2026-01-01 | DL1LAD8977 |
| 46 | 29170 | DL1LAB0468 | 2026-01-01 | DL1LAB0468 |
| 48 | 29180 | DL1LAL1428 | 2026-01-01 | DL1LAL1428 |
| 56 | 29167 | AP39US6778 | 2026-01-01 | AP39US6778 |
| 57 | 29200 | DL2CBF1805 | 2026-01-01 | DL2CBF1805 |
| 60 | 29199 | DL2CBF1804 | 2026-01-01 | DL2CBF1804 |

### 3.3 VEHICLE_NO Appearing More Than 31 Times — 109 Vehicles

A full January dataset is expected to have a maximum of 31 records per vehicle. 109 vehicle numbers exceed this, indicating the same vehicle number exists under multiple VEHICLE_IDs.

**Sample Records**

| VEHICLE_NO | Record Count | Days Expected | Excess Records |
|---|---|---|---|
| KA51AF7044 | 93 | 31 | 62 |
| DL3CCY2354 | 62 | 31 | 31 |
| DL4SDU6337 | 62 | 31 | 31 |
| DL2CBF1848 | 62 | 31 | 31 |
| HR55AQ4918 | 62 | 31 | 31 |
| GJ01XF3160 | 62 | 31 | 31 |
| HR55AQ0589 | 62 | 31 | 31 |
| AS01EK1982 | 62 | 31 | 31 |
| DL2CAL0719 | 62 | 31 | 31 |
| GJ01KT3581 | 62 | 31 | 31 |

---

## Module 4 — Odometer Checks

### 4.1 START_ODOMETER Greater Than END_ODOMETER — 1 Record (0.0005%)

**Sample Records**

| ID | VEHICLE_ID | VEHICLE_NO | CREATED_DATE | START_ODOMETER | END_ODOMETER | DIFFERENCE |
|---|---|---|---|---|---|---|
| 136377 | 35585 | DL10DA9570 | 2026-01-27 | 398,903.00 | 398,881.00 | 22.00 |

### 4.2 Both START_ODOMETER and END_ODOMETER = 0 — 77,893 Records (38.93%)

**Sample Records**

| ID | VEHICLE_ID | VEHICLE_NO | CREATED_DATE | START_ODOMETER | END_ODOMETER | DISTANCE_TRAVELED |
|---|---|---|---|---|---|---|
| 193705 | 29011 | TN19AV7381 | 2026-01-31 | 0.00 | 0.00 | 0.00 |
| 3 | 29019 | TN38BR8867 | 2026-01-01 | 0.00 | 0.00 | 0.00 |
| 6410 | 29019 | TN38BR8867 | 2026-01-02 | 0.00 | 0.00 | 0.00 |
| 12819 | 29019 | TN38BR8867 | 2026-01-03 | 0.00 | 0.00 | 0.00 |
| 19235 | 29019 | TN38BR8867 | 2026-01-04 | 0.00 | 0.00 | 0.00 |
| 25649 | 29019 | TN38BR8867 | 2026-01-05 | 0.00 | 0.00 | 0.00 |
| 32039 | 29019 | TN38BR8867 | 2026-01-06 | 0.00 | 0.00 | 0.00 |
| 38203 | 29019 | TN38BR8867 | 2026-01-07 | 0.00 | 0.00 | 0.00 |
| 44586 | 29019 | TN38BR8867 | 2026-01-08 | 0.00 | 0.00 | 0.00 |
| 51018 | 29019 | TN38BR8867 | 2026-01-09 | 0.00 | 0.00 | 0.00 |

### 4.3 Odometer Continuity Jumps (Consecutive Days) — 8,683 Records (4.34%)

For these records, the START_ODOMETER of a given day does not match the END_ODOMETER of the previous day for the same vehicle.

**Sample Records**

| ID | VEHICLE_ID | VEHICLE_NO | CREATED_DATE | START_ODOMETER | PREV_END_ODO | ODO_GAP | END_ODOMETER |
|---|---|---|---|---|---|---|---|
| 193705 | 29011 | TN19AV7381 | 2026-01-31 | 0.00 | 11,545.10 | 11,545.10 | 0.00 |
| 193721 | 29044 | TN18BR4024 | 2026-01-31 | 0.00 | 30,123.10 | 30,123.10 | 0.00 |
| 110532 | 29058 | TN18AD7960 | 2026-01-24 | 0.00 | 1,851.82 | 1,851.82 | 0.00 |
| 193715 | 29059 | TN18AD3802 | 2026-01-31 | 0.00 | 1,996.87 | 1,996.87 | 0.00 |
| 109571 | 29062 | TN18AD9457 | 2026-01-23 | 0.00 | 129.54 | 129.54 | 0.00 |
| 51035 | 29065 | TN18AD4430 | 2026-01-09 | 458.07 | 448.94 | 9.13 | 488.75 |
| 193726 | 29065 | TN18AD4430 | 2026-01-31 | 578.61 | 560.09 | 18.53 | 578.92 |
| 193733 | 29070 | TN18BR4082 | 2026-01-31 | 0.00 | 12,673.80 | 12,673.80 | 0.00 |
| 193744 | 29074 | TN18AD3760 | 2026-01-31 | 0.00 | 74,826.20 | 74,826.20 | 0.00 |
| 105403 | 29075 | TN18BR4068 | 2026-01-19 | 0.00 | 41,668.60 | 41,668.60 | 0.00 |

### 4.4 DISTANCE_TRAVELED != END_ODO - START_ODO (>1 km difference) — 13 Records (0.01%)

**Sample Records**

| ID | VEHICLE_ID | VEHICLE_NO | CREATED_DATE | DISTANCE_TRAVELED | ODO_DISTANCE | DIST_DIFF |
|---|---|---|---|---|---|---|
| 45041 | 29544 | DL1CAK0143 | 2026-01-08 | 30.00 | 150.00 | 120.00 |
| 194030 | 29552 | DL8CBH0884 | 2026-01-31 | 10.00 | 233.00 | 223.00 |
| 20589 | 29564 | TN01BP9837 | 2026-01-04 | 109.00 | 92.00 | 17.00 |
| 57866 | 29564 | TN01BP9837 | 2026-01-10 | 42.00 | 44.00 | 2.00 |
| 38886 | 29565 | TN01BP9839 | 2026-01-07 | 123.00 | 83.00 | 40.00 |
| 86141 | 29565 | TN01BP9839 | 2026-01-15 | 27.00 | 18.00 | 9.00 |
| 108946 | 29565 | TN01BP9839 | 2026-01-22 | 110.00 | 98.00 | 12.00 |
| 109959 | 29565 | TN01BP9839 | 2026-01-23 | 118.00 | 104.00 | 14.00 |
| 130331 | 29565 | TN01BP9839 | 2026-01-27 | 102.00 | 90.00 | 12.00 |
| 181218 | 29565 | TN01BP9839 | 2026-01-29 | 113.00 | 92.00 | 21.00 |

**Odometer Value Distribution**

| Field | Min | Max | Zero Count | Zero % |
|---|---|---|---|---|
| START_ODOMETER | -79,919.80 | 718,960.00 | 77,893 | 38.93% |
| END_ODOMETER | -79,919.80 | 718,984.00 | 77,893 | 38.93% |

ODO distance (END - START): Min = -22.00 km, Max = 7,843.00 km, Mean = 80.29 km, Median = 1.10 km, Negative count = 1

---

## Module 5 — Extreme Value Checks

### 5.1 MAX_RPM > 7,000 — 290 Records (0.14%)

Maximum observed: 16,383 RPM.

**Sample Records**

| ID | VEHICLE_ID | VEHICLE_NO | CREATED_DATE | MAX_RPM |
|---|---|---|---|---|
| 6173 | 35164 | HR38AE5679 | 2026-01-01 | 10,901 |
| 7378 | 29716 | TN87F3742 | 2026-01-02 | 8,160.5 |
| 8038 | 34219 | HR38AE3072 | 2026-01-02 | 10,901 |
| 8052 | 33191 | HR55AR5335 | 2026-01-02 | 10,901 |
| 10738 | 33344 | HR38AE6256 | 2026-01-02 | 10,901 |
| 11261 | 34354 | TN09DD4781 | 2026-01-02 | 10,901 |
| 11420 | 34533 | TS07UM5524 | 2026-01-02 | 10,901 |
| 12432 | 33337 | HR38AE4915 | 2026-01-02 | 10,901 |
| 12498 | 33647 | HR55AQ5963 | 2026-01-02 | 10,901 |
| 12751 | 35117 | HR38AE8660 | 2026-01-02 | 10,901 |

### 5.2 MAX_SPEED >= 200 km/h — 14 Records (0.007%)

Maximum observed: 271,679,000.00 km/h.

**Sample Records**

| ID | VEHICLE_ID | VEHICLE_NO | CREATED_DATE | MAX_SPEED |
|---|---|---|---|---|
| 6844 | 30639 | FBA48-4850-02178 | 2026-01-02 | 262 |
| 8963 | 31126 | FBA48-4850-02487 | 2026-01-02 | 417.1 |
| 13594 | 30631 | FBA48-3690-01913 | 2026-01-03 | 201 |
| 17058 | 30135 | BLRSM0016 | 2026-01-03 | 320 |
| 76663 | 35558 | C2C-BENCH_TEST | 2026-01-12 | 569.11 |
| 78308 | 30831 | FBA48-3690-01922 | 2026-01-13 | 210 |
| 86822 | 30280 | KA05AM2566 | 2026-01-15 | 232 |
| 97536 | 32734 | HR55AS7741 | 2026-01-17 | 278.8 |
| 103655 | 33254 | KA05AN2963 | 2026-01-18 | 227 |
| 109536 | 35595 | TN07CC4309 | 2026-01-22 | 1,130.5 |

### 5.3 DISTANCE_TRAVELED > 2,000 km — 2 Records (0.001%)

**Records**

| ID | VEHICLE_ID | VEHICLE_NO | CREATED_DATE | DISTANCE_TRAVELED |
|---|---|---|---|---|
| 117825 | 35391 | TG07T6237 | 2026-01-25 | 3,618.94 |
| 198452 | 33807 | TS07UM8434 | 2026-01-31 | 7,842.56 |

### 5.4 Negative Odometer Values — 31 Records (0.015%)

All 31 records belong to a single vehicle: KA05AM7253 (VEHICLE_ID 33757). Both START and END odometers consistently read -65.536 across every day of January.

**Sample Records**

| ID | VEHICLE_ID | VEHICLE_NO | CREATED_DATE | START_ODOMETER | END_ODOMETER |
|---|---|---|---|---|---|
| 4534 | 33757 | KA05AM7253 | 2026-01-01 | -65.536 | -65.536 |
| 12520 | 33757 | KA05AM7253 | 2026-01-02 | -65.536 | -65.536 |
| 18824 | 33757 | KA05AM7253 | 2026-01-03 | -65.536 | -65.536 |
| 25283 | 33757 | KA05AM7253 | 2026-01-04 | -65.536 | -65.536 |
| 31761 | 33757 | KA05AM7253 | 2026-01-05 | -65.536 | -65.536 |
| 36850 | 33757 | KA05AM7253 | 2026-01-06 | -65.536 | -65.536 |
| 43320 | 33757 | KA05AM7253 | 2026-01-07 | -65.536 | -65.536 |
| 50145 | 33757 | KA05AM7253 | 2026-01-08 | -65.536 | -65.536 |
| 55536 | 33757 | KA05AM7253 | 2026-01-09 | -65.536 | -65.536 |
| 62048 | 33757 | KA05AM7253 | 2026-01-10 | -65.536 | -65.536 |

### 5.5 Ghost Speed — MAX_SPEED > 0 but DISTANCE_TRAVELED = 0 — 3,300 Records (1.65%)

**Sample Records**

| ID | VEHICLE_ID | VEHICLE_NO | CREATED_DATE | MAX_SPEED | DISTANCE_TRAVELED | MOVE_MINS |
|---|---|---|---|---|---|---|
| 17 | 29021 | TN64Q4226 | 2026-01-01 | 4.4 | 0 | 4 |
| 340 | 29661 | MB1AUPCC7SEHT7575 | 2026-01-01 | 63 | 0 | 170 |
| 344 | 29671 | MB1G9VHD8SPGH1233 | 2026-01-01 | 54 | 0 | 407 |
| 376 | 29669 | MB1A5RCD8SEHT8056 | 2026-01-01 | 38 | 0 | 11 |
| 377 | 29660 | MB1AUPCC5SEGT9709 | 2026-01-01 | 76 | 0 | 287 |
| 379 | 29670 | MB1NGVHD7SPJG3720 | 2026-01-01 | 59 | 0 | 128 |
| 400 | 29792 | MB1AYGCD3SADU8825 | 2026-01-01 | 50 | 0 | 258 |
| 413 | 29802 | MB1NGVHD9SPHG6137 | 2026-01-01 | 460 | 0 | 460 |
| 421 | 29812 | MB1A5HCDXSRHK4548 | 2026-01-01 | 35 | 0 | 156 |
| 447 | 29832 | MB1AUPCC5SEGU1394 | 2026-01-01 | 54 | 0 | 0 |

### 5.6 Ghost Distance — DISTANCE_TRAVELED > 0 but MOVE_MINS = 0 — 581 Records (0.29%)

**Sample Records**

| ID | VEHICLE_ID | VEHICLE_NO | CREATED_DATE | DISTANCE_TRAVELED | MOVE_MINS | MAX_SPEED |
|---|---|---|---|---|---|---|
| 279 | 29277 | KA51C9920 | 2026-01-01 | 0.20 | 0 | 0 |
| 291 | 29601 | NMR WOW 2 | 2026-01-01 | 0.60 | 0 | 0 |
| 402 | 29335 | MH12WK2098 | 2026-01-01 | 0.30 | 0 | 13 |
| 1043 | 29817 | TN64R1417 | 2026-01-01 | 6.28 | 0 | 0 |
| 5062 | 33583 | HR55AQ5923 | 2026-01-01 | 0.20 | 0 | 0 |
| 5405 | 33576 | HR55AQ6338 | 2026-01-01 | 0.23 | 0 | 0 |
| 6325 | 35160 | HR38AE6721 | 2026-01-01 | 0.10 | 0 | 0 |
| 7237 | 32259 | TN09DD9860 | 2026-01-02 | 0.18 | 0 | 0 |
| 7246 | 31161 | TN12AZ6507 | 2026-01-02 | 4.93 | 0 | 0 |
| 7286 | 31301 | TG07T3760 | 2026-01-02 | 0.02 | 0 | 3 |

**Key Field Ranges**

| Field | Min | Max | Mean | Non-Zero Count | Non-Zero % |
|---|---|---|---|---|---|
| MAX_RPM | 0.00 | 16,383.00 | 1,066.20 | 63,782 | 31.88% |
| MAX_SPEED | 0.00 | 271,679,000.00 | 1,391.61 | 107,360 | 53.66% |
| AVG_SPEED | 0.00 | 75,004.40 | 12.70 | 107,246 | 53.60% |
| DISTANCE_TRAVELED | 0.00 | 7,842.56 | 80.28 | 104,293 | 52.13% |

---

## Module 6 — Negative Value and Range Checks

### 6.1 Business-Critical Negative Value Scan
No negative values were found in any business-critical numeric field (distances, durations, counts). This check passed cleanly for all fields.

### 6.2 DRIVER_SCORE Distribution

| Score Band | Count | % |
|---|---|---|
| Score = 0 | 200,072 | 100.00% |
| Score 1–59 | 0 | 0.00% |
| Score 60–79 | 0 | 0.00% |
| Score 80–99 | 5 | 0.00% |
| Score = 100 | 0 | 0.00% |
| Score > 100 | 0 | 0.00% |
| Score NULL | 0 | 0.00% |

DRIVER_SCORE range: min = 0.00, max = 92.26, mean = 0.00

### 6.3 AVG_SPEED Greater Than MAX_SPEED — 16 Records (0.008%)

**Sample Records**

| ID | VEHICLE_ID | VEHICLE_NO | CREATED_DATE | AVG_SPEED | MAX_SPEED |
|---|---|---|---|---|---|
| 802 | 30221 | SESEAG10202200395 | 2026-01-01 | 18.6 | 18 |
| 1298 | 30378 | KA05AM4014 | 2026-01-01 | 27.25 | 27 |
| 25095 | 35324 | WAGONR | 2026-01-04 | 20.18 | 20 |
| 54977 | 33292 | KA05AN0578 | 2026-01-09 | 10 | 6 |
| 77328 | 29783 | MB1AUGCC5SRDL7877 | 2026-01-13 | 64.14 | 60 |
| 80498 | 32878 | HR55AS9579 | 2026-01-13 | 1.9 | 1.3 |
| 83645 | 29792 | MB1AYGCD3SADU8825 | 2026-01-14 | 31 | 22 |
| 107426 | 35590 | MB1A4RCD0SETU9962 | 2026-01-20 | 43 | 36 |
| 130578 | 29812 | MB1A5HCDXSRHK4548 | 2026-01-27 | 57 | 47 |
| 130850 | 30027 | KA01AN5038 | 2026-01-27 | 13 | 11 |

---

## Module 7 — Cross-Field Validations

### 7.1 END_HOURMETER - START_HOURMETER != TOTAL_HOUR_METER — 122,491 Records (61.22%)

For these records, the daily hourmeter delta (END minus START) does not equal TOTAL_HOUR_METER. The most common pattern is both START and END hourmeters being zero while TOTAL_HOUR_METER holds a large non-zero value.

**Sample Records**

| ID | VEHICLE_ID | VEHICLE_NO | CREATED_DATE | START_HOURMETER | END_HOURMETER | TOTAL_HOUR_METER |
|---|---|---|---|---|---|---|
| 5 | 29020 | TN20AP2032 | 2026-01-01 | 0 | 0 | 34,177 |
| 6 | 29023 | TN64Y8271 | 2026-01-01 | 0 | 0 | 8,789 |
| 7 | 29018 | TN38CY0940 | 2026-01-01 | 0 | 0 | 19,565 |
| 8 | 29022 | TN64T6849 | 2026-01-01 | 0 | 0 | 35,636 |
| 9 | 29024 | TN64T9921 | 2026-01-01 | 0 | 0 | 34,160 |
| 11 | 29017 | TN87E0353 | 2026-01-01 | 0 | 0 | 3,631 |
| 17 | 29021 | TN64Q4226 | 2026-01-01 | 0 | 0 | 52,152 |
| 23 | 29038 | TN45CD3164 | 2026-01-01 | 0 | 0 | 58,834 |
| 25 | 29060 | TN18BR4081 | 2026-01-01 | 0 | 0 | 16,866 |
| 26 | 29066 | TN18AD8302 | 2026-01-01 | 0 | 0 | 12,504 |

### 7.2 DISTANCE_TRAVELED > 0 AND FUEL_CONSUMED = 0 — 103,945 Records (51.95%)

**Sample Records**

| ID | VEHICLE_ID | VEHICLE_NO | CREATED_DATE | DISTANCE_TRAVELED | FUEL_CONSUMED |
|---|---|---|---|---|---|
| 7 | 29018 | TN38CY0940 | 2026-01-01 | 45.38 | 0.00 |
| 8 | 29022 | TN64T6849 | 2026-01-01 | 64.64 | 0.00 |
| 9 | 29024 | TN64T9921 | 2026-01-01 | 122.25 | 0.00 |
| 25 | 29060 | TN18BR4081 | 2026-01-01 | 61.70 | 0.00 |
| 26 | 29066 | TN18AD8302 | 2026-01-01 | 28.41 | 0.00 |
| 27 | 29068 | TN18BR7697 | 2026-01-01 | 17.75 | 0.00 |
| 31 | 29065 | TN18AD4430 | 2026-01-01 | 60.33 | 0.00 |
| 33 | 29069 | TN18BS1143 | 2026-01-01 | 59.84 | 0.00 |
| 34 | 29071 | TN18BS1170 | 2026-01-01 | 61.30 | 0.00 |
| 36 | 29072 | TN18AD4997 | 2026-01-01 | 7.17 | 0.00 |

### 7.3 OFFLINE_COUNT_MINS < 0 (Corrupt) — 88,157 Records (44.06%)

**Sample Records**

| ID | VEHICLE_ID | VEHICLE_NO | CREATED_DATE | OFFLINE_COUNT_MINS | OFFLINE_MINS |
|---|---|---|---|---|---|
| 6434 | 29066 | TN18AD8302 | 2026-01-02 | -785 | 11 |
| 6438 | 29060 | TN18BR4081 | 2026-01-02 | -875 | 14 |
| 6439 | 29068 | TN18BR7697 | 2026-01-02 | -5,669 | 7 |
| 6440 | 29071 | TN18BS1170 | 2026-01-02 | -2,080 | 2 |
| 6442 | 29069 | TN18BS1143 | 2026-01-02 | -2,468 | 4 |
| 6447 | 29065 | TN18AD4430 | 2026-01-02 | -3,616 | 7 |
| 6448 | 29070 | TN18BR4082 | 2026-01-02 | -874 | 9 |
| 6450 | 29181 | DL1LAL1435 | 2026-01-02 | -803 | 2 |
| 6452 | 29043 | TN18BR4025 | 2026-01-02 | -4,867 | 2 |
| 6454 | 29199 | DL2CBF1804 | 2026-01-02 | -1,138 | 8 |

### 7.4 IDLE + MOVE + STOP + OFFLINE Minutes != 1,440 — 74,771 Records (37.37%)

| Balance | Count | % |
|---|---|---|
| Exactly 1,440 mins | 125,306 | 62.63% |
| Less than 1,440 mins | 70,643 | 35.31% |
| Greater than 1,440 mins | 4,128 | 2.06% |
| Min total observed | 212 mins | — |
| Max total observed | 2,874 mins | — |

**Sample Records**

| ID | VEHICLE_ID | VEHICLE_NO | CREATED_DATE | IDLE_MINS | MOVE_MINS | STOP_MINS | OFFLINE_MINS |
|---|---|---|---|---|---|---|---|
| 1 | 29026 | KA51AL0250 | 2026-01-01 | 0 | 0 | 0 | 1,439 |
| 2 | 29011 | TN19AV7381 | 2026-01-01 | 0 | 0 | 0 | 1,439 |
| 3 | 29019 | TN38BR8867 | 2026-01-01 | 0 | 0 | 0 | 1,439 |
| 4 | 29025 | KL07DF3325 | 2026-01-01 | 0 | 0 | 0 | 1,439 |
| 10 | 29030 | TN09DK4557 | 2026-01-01 | 0 | 0 | 0 | 1,439 |
| 12 | 29028 | TN09DK9057 | 2026-01-01 | 0 | 0 | 0 | 1,439 |
| 13 | 29033 | TN09DE8454 | 2026-01-01 | 0 | 0 | 0 | 1,439 |
| 14 | 29029 | TN09DL1392 | 2026-01-01 | 0 | 0 | 0 | 1,439 |
| 15 | 29032 | TN09DE8467 | 2026-01-01 | 0 | 0 | 0 | 1,439 |
| 16 | 29044 | TN18BR4024 | 2026-01-01 | 0 | 0 | 0 | 1,439 |

### 7.5 RPM_AT_MAX_SPEED = 0 AND MAX_SPEED > 0 — 45,146 Records (22.56%)

**Sample Records**

| ID | VEHICLE_ID | VEHICLE_NO | CREATED_DATE | RPM_AT_MAX_SPEED | MAX_SPEED |
|---|---|---|---|---|---|
| 7 | 29018 | TN38CY0940 | 2026-01-01 | 0.00 | 66.30 |
| 8 | 29022 | TN64T6849 | 2026-01-01 | 0.00 | 54.10 |
| 9 | 29024 | TN64T9921 | 2026-01-01 | 0.00 | 76.60 |
| 17 | 29021 | TN64Q4226 | 2026-01-01 | 0.00 | 4.40 |
| 25 | 29060 | TN18BR4081 | 2026-01-01 | 0.00 | 45.90 |
| 26 | 29066 | TN18AD8302 | 2026-01-01 | 0.00 | 34.80 |
| 27 | 29068 | TN18BR7697 | 2026-01-01 | 0.00 | 43.90 |
| 31 | 29065 | TN18AD4430 | 2026-01-01 | 0.00 | 37.70 |
| 33 | 29069 | TN18BS1143 | 2026-01-01 | 0.00 | 46.60 |
| 34 | 29071 | TN18BS1170 | 2026-01-01 | 0.00 | 37.60 |

### 7.6 MAX_RPM_COOL_TEMP = 0 AND DISTANCE_TRAVELED > 0 — 42,499 Records (21.24%)

**Sample Records**

| ID | VEHICLE_ID | VEHICLE_NO | CREATED_DATE | MAX_RPM_COOL_TEMP | DISTANCE_TRAVELED |
|---|---|---|---|---|---|
| 7 | 29018 | TN38CY0940 | 2026-01-01 | 0 | 45.38 |
| 8 | 29022 | TN64T6849 | 2026-01-01 | 0 | 64.64 |
| 9 | 29024 | TN64T9921 | 2026-01-01 | 0 | 122.25 |
| 25 | 29060 | TN18BR4081 | 2026-01-01 | 0 | 61.70 |
| 26 | 29066 | TN18AD8302 | 2026-01-01 | 0 | 28.41 |
| 27 | 29068 | TN18BR7697 | 2026-01-01 | 0 | 17.75 |
| 31 | 29065 | TN18AD4430 | 2026-01-01 | 0 | 60.33 |
| 33 | 29069 | TN18BS1143 | 2026-01-01 | 0 | 59.84 |
| 34 | 29071 | TN18BS1170 | 2026-01-01 | 0 | 61.30 |
| 36 | 29072 | TN18AD4997 | 2026-01-01 | 0 | 7.17 |

### 7.7 MOVE_MINS > 0 AND DISTANCE_TRAVELED = 0 — 3,960 Records (1.98%)

**Sample Records**

| ID | VEHICLE_ID | VEHICLE_NO | CREATED_DATE | MOVE_MINS | DISTANCE_TRAVELED | MAX_SPEED |
|---|---|---|---|---|---|---|
| 17 | 29021 | TN64Q4226 | 2026-01-01 | 4 | 0.00 | 4.4 |
| 157 | 29245 | KA03MX3575 | 2026-01-01 | 4 | 0.00 | 0 |
| 340 | 29661 | MB1AUPCC7SEHT7575 | 2026-01-01 | 170 | 0.00 | 63 |
| 344 | 29671 | MB1G9VHD8SPGH1233 | 2026-01-01 | 407 | 0.00 | 54 |
| 376 | 29669 | MB1A5RCD8SEHT8056 | 2026-01-01 | 11 | 0.00 | 38 |
| 377 | 29660 | MB1AUPCC5SEGT9709 | 2026-01-01 | 287 | 0.00 | 76 |
| 379 | 29670 | MB1NGVHD7SPJG3720 | 2026-01-01 | 128 | 0.00 | 59 |
| 400 | 29792 | MB1AYGCD3SADU8825 | 2026-01-01 | 258 | 0.00 | 50 |
| 413 | 29802 | MB1NGVHD9SPHG6137 | 2026-01-01 | 460 | 0.00 | 53 |
| 421 | 29812 | MB1A5HCDXSRHK4548 | 2026-01-01 | 156 | 0.00 | 35 |

### 7.8 NIGHT_MOVING_MINS > 0 AND NIGHT_DRIVING_DISTANCE = 0 — 3,944 Records (1.97%)

**Sample Records**

| ID | VEHICLE_ID | VEHICLE_NO | CREATED_DATE | NIGHT_DRIVING_DISTANCE | NIGHT_MOVING_MINS |
|---|---|---|---|---|---|
| 77 | 29195 | DL2CAZ0612 | 2026-01-01 | 0.00 | 2 |
| 88 | 29216 | DL4SDK8489 | 2026-01-01 | 0.00 | 1 |
| 139 | 29289 | KL39G1023 | 2026-01-01 | 0.00 | 15 |
| 171 | 29218 | DL4SDU6337 | 2026-01-01 | 0.00 | 22 |
| 267 | 29390 | TS08EQ9987 | 2026-01-01 | 0.00 | 4 |
| 377 | 29660 | MB1AUPCC5SEGT9709 | 2026-01-01 | 0.00 | 95 |
| 438 | 29769 | TN52AB5466 | 2026-01-01 | 0.00 | 11 |
| 449 | 29799 | MB1JJVPD8SRKH7554 | 2026-01-01 | 0.00 | 4 |
| 506 | 29663 | MB1ASPCC9SEHT8104 | 2026-01-01 | 0.00 | 102 |
| 651 | 29664 | MB1AUGCCXSRHK1234 | 2026-01-01 | 0.00 | 91 |

### 7.9 NIGHT_DRIVING_DISTANCE > 0 AND NIGHT_MOVING_MINS = 0 — 483 Records (0.24%)

**Sample Records**

| ID | VEHICLE_ID | VEHICLE_NO | CREATED_DATE | NIGHT_DRIVING_DISTANCE | NIGHT_MOVING_MINS |
|---|---|---|---|---|---|
| 659 | 29588 | TIR Mini WOW | 2026-01-01 | 0.20 | 0 |
| 1043 | 29817 | TN64R1417 | 2026-01-01 | 1.23 | 0 |
| 1493 | 31171 | ECE02187VR0037022 | 2026-01-01 | 1.41 | 0 |
| 1567 | 30274 | KA05AM6372 | 2026-01-01 | 0.48 | 0 |
| 1574 | 30216 | KA05AM6276 | 2026-01-01 | 0.05 | 0 |
| 2354 | 32522 | KA05AN2914 | 2026-01-01 | 0.24 | 0 |
| 4805 | 34918 | TN09DD4613 | 2026-01-01 | 0.10 | 0 |
| 4844 | 34237 | HR55AQ8982 | 2026-01-01 | 0.22 | 0 |
| 5209 | 33300 | HR55AS1066 | 2026-01-01 | 0.11 | 0 |
| 5852 | 34284 | TS07UM5502 | 2026-01-01 | 0.12 | 0 |

### 7.10 OVER_SPEED_COUNT > 0 AND MAX_SPEED = 0 — 144 Records (0.07%)

**Sample Records**

| ID | VEHICLE_ID | VEHICLE_NO | CREATED_DATE | OVER_SPEED_COUNT | MAX_SPEED |
|---|---|---|---|---|---|
| 157 | 29245 | KA03MX3575 | 2026-01-01 | 3 | 0.00 |
| 239 | 29370 | TN09DC8626 | 2026-01-01 | 3 | 0.00 |
| 42884 | 34260 | TN09DE0155 | 2026-01-07 | 9 | 0.00 |
| 44094 | 34813 | KA05AM7097 | 2026-01-07 | 1 | 0.00 |
| 55117 | 33307 | HR55AQ2550 | 2026-01-09 | 4 | 0.00 |
| 55327 | 33443 | HR55AR5855 | 2026-01-09 | 3 | 0.00 |
| 55536 | 33757 | KA05AM7253 | 2026-01-09 | 1 | 0.00 |
| 55574 | 33546 | TN09DE1584 | 2026-01-09 | 1 | 0.00 |
| 55643 | 33345 | TN09DE1485 | 2026-01-09 | 3 | 0.00 |
| 55648 | 34032 | TN09DE0399 | 2026-01-09 | 4 | 0.00 |

### 7.11 MOVE_MINS > 0 AND IGNITION_COUNT = 0 — 823 Records (0.41%)

**Sample Records**

| ID | VEHICLE_ID | VEHICLE_NO | CREATED_DATE | MOVE_MINS | IGNITION_COUNT | DISTANCE_TRAVELED |
|---|---|---|---|---|---|---|
| 157 | 29245 | KA03MX3575 | 2026-01-01 | 4 | 0 | 0 |
| 1301 | 31152 | TN12AZ6573 | 2026-01-01 | 27 | 0 | 0 |
| 2203 | 31160 | FDA41-2620-03391 | 2026-01-01 | 68 | 0 | 0 |
| 3073 | 33452 | TN09DE1420 | 2026-01-01 | 84 | 0 | 0 |
| 3439 | 33345 | TN09DE1485 | 2026-01-01 | 35 | 0 | 0 |
| 3476 | 34032 | TN09DE0399 | 2026-01-01 | 105 | 0 | 0 |
| 3534 | 33485 | TS07UM9661 | 2026-01-01 | 46 | 0 | 0 |
| 3882 | 33698 | KA05AN3268 | 2026-01-01 | 2 | 0 | 0 |
| 4103 | 34285 | HR55AR2122 | 2026-01-01 | 1 | 0 | 0 |
| 4169 | 33307 | HR55AQ2550 | 2026-01-01 | 39 | 0 | 0 |

---

## Full Anomaly Summary

| Finding | Count | % of Total |
|---|---|---|
| END_HOURMETER - START_HOURMETER != TOTAL_HOUR_METER | 122,491 | 61.22% |
| DISTANCE_TRAVELED > 0 AND FUEL_CONSUMED = 0 | 103,945 | 51.95% |
| OFFLINE_COUNT_MINS < 0 | 88,157 | 44.06% |
| Both START_ODOMETER and END_ODOMETER = 0 | 77,893 | 38.93% |
| IDLE+MOVE+STOP+OFFLINE mins != 1,440 | 74,771 | 37.37% |
| Constant-value columns (all zero) | 62 columns | 36.69% of columns |
| RPM_AT_MAX_SPEED = 0 AND MAX_SPEED > 0 | 45,146 | 22.56% |
| MAX_RPM_COOL_TEMP = 0 AND DISTANCE_TRAVELED > 0 | 42,499 | 21.24% |
| Near-constant columns (>=99% zero) | 24 columns | 14.20% of columns |
| Odometer continuity jumps (consecutive days) | 8,683 | 4.34% |
| Duplicate VIN_NUMBER + CREATED_DATE | 6,136 | 3.07% |
| Always-NULL columns | 5 columns | 2.96% of columns |
| MOVE_MINS > 0 AND DISTANCE_TRAVELED = 0 | 3,960 | 1.98% |
| NIGHT_MOVING_MINS > 0 AND NIGHT_DRIVING_DISTANCE = 0 | 3,944 | 1.97% |
| Ghost speed (MAX_SPEED > 0, DISTANCE_TRAVELED = 0) | 3,300 | 1.65% |
| VEHICLE_NO appearing more than 31 times | 109 vehicles | — |
| MOVE_MINS > 0 AND IGNITION_COUNT = 0 | 823 | 0.41% |
| Ghost distance (DISTANCE_TRAVELED > 0, MOVE_MINS = 0) | 581 | 0.29% |
| NIGHT_DRIVING_DISTANCE > 0 AND NIGHT_MOVING_MINS = 0 | 483 | 0.24% |
| MAX_RPM > 7,000 | 290 | 0.14% |
| OVER_SPEED_COUNT > 0 AND MAX_SPEED = 0 | 144 | 0.07% |
| Duration != 23:59:59 | 83 | 0.04% |
| Negative odometer values | 31 | 0.02% |
| AVG_SPEED > MAX_SPEED | 16 | 0.01% |
| MAX_SPEED >= 200 km/h | 14 | 0.01% |
| DISTANCE_TRAVELED != END_ODO - START_ODO (>1 km) | 13 | 0.01% |
| DISTANCE_TRAVELED > 2,000 km | 2 | 0.001% |
| START_ODOMETER > END_ODOMETER | 1 | 0.0005% |
| Full row duplicates | 0 | 0.00% |
| Duplicate primary key (ID) | 0 | 0.00% |
| Duplicate VEHICLE_ID + CREATED_DATE | 0 | 0.00% |
| Negative values in business-critical fields | 0 | 0.00% |
| DRIVER_SCORE > 100 | 0 | 0.00% |
| ENGINE_RUN_MINS > 1,440 | 0 | 0.00% |
| HARSH_ALERT_COUNT > 50 | 0 | 0.00% |
