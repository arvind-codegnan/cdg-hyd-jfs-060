# SQL Exercise Pack 1

## Purpose

This pack contains 10 standalone-table exercises. Each table uses only `INT` and `VARCHAR` data types. No SQL constraints are used.

Learners will practise:

- creating tables using only `INT` and `VARCHAR`;
- understanding how columns behave when no constraints are defined;
- inserting single and multiple rows;
- updating individual and multiple rows; and
- deleting rows safely using precise WHERE conditions.

## Tables

1. `courses`
2. `instructors`
3. `warehouses`
4. `shipments`
5. `subscriptions`
6. `events`
7. `devices`
8. `restaurants`
9. `insurance_policies`
10. `job_postings`

## Environment and Safety Rules

- Use only `INT` and `VARCHAR` for column definitions.
- Do not define any constraints or automatic value-generation rules.
- All columns are nullable; do not add `NOT NULL`.
- Supply values explicitly when inserting sample records.
- Store dates only as `'YYYY-MM-DD'` text.

## Recommended Order for Every Use Case

1. Read the scenario and column requirements.
2. Write and execute the `CREATE TABLE` statement.
3. Inspect the structure using `DESCRIBE` OR `SHOW CREATE TABLE`.
4. Complete the valid insert exercises.
5. Review inserted rows using SELECT.
6. Complete the update exercises.
7. Complete the delete exercises.
8. Verify the final contents of the table.

---

# 1. Online Course Catalogue

**Suggested table:** `courses`

## Scenario

A training institute needs one table containing its independent course catalogue. Instructor assignments are outside the scope of this exercise.

## Column Requirements

| Column | Data type | Description |
|---|---|---|
| `course_id` | `INT` | Numeric row number |
| `course_code` | `VARCHAR(15)` | Business identifier |
| `course_title` | `VARCHAR(150)` | |
| `category` | `VARCHAR(60)` | |
| `duration_hours` | `INT` | Whole hours |
| `fee` | `INT` | Whole rupees |
| `delivery_mode` | `VARCHAR(20)` | |
| `course_status` | `VARCHAR(20)` | |
| `created_at` | `VARCHAR(10)` | `YYYY-MM-DD` text |

## A. CREATE Exercises

1. **CRS-C1:** Create `courses` using only INT and VARCHAR columns. Do not define constraints.
2. Inspect the table structure using `DESCRIBE`.
3. Use `SHOW CREATE TABLE` and verify the table definition.

## B. INSERT Exercises

| Course code | Title | Category | Hours | Fee | Delivery mode | Status |
|---|---|---|---:|---:|---|---|
| CRS-JAVA-101 | Java Fundamentals | Programming | 40 | 6000 | CLASSROOM | ACTIVE |
| CRS-SQL-102 | MySQL Essentials | Database | 32 | 4500 | ONLINE | ACTIVE |
| CRS-WEB-103 | Responsive Web Design | Web Development | 28 | 0 | ONLINE | ACTIVE |
| CRS-TST-104 | Software Testing Basics | Testing | 24 | 3500 | HYBRID | ACTIVE |
| CRS-OLD-105 | Legacy Systems Overview | Technology | 12 | 2000 | ONLINE | ARCHIVED |

1. **CRS-I1:** Insert `CRS-JAVA-101` using an explicit column list.
2. **CRS-I2:** Insert `CRS-SQL-102` and `CRS-WEB-103` using one multi-row statement. Provide explicit values for every column in both rows.
3. **CRS-I3:** Insert the remaining two courses.
4. Insert one additional valid sample row with values of your choice.

## C. UPDATE Exercises

1. **CRS-U1:** Change the fee of `CRS-JAVA-101` to `6500`.
2. **CRS-U2:** Increase the fee of every active course by `10%`, rounding to a whole number.
3. **CRS-U3:** Change `CRS-WEB-103` to `ACTIVE` and set its fee to `2500`.
4. **CRS-U4:** Increase the duration of every testing course by `4` hours.
5. **CRS-U5:** Change a course duration to `0` and verify the updated value with SELECT.

## D. DELETE Exercises

1. **CRS-D1:** Preview and delete the archived course `CRS-OLD-105`.
2. **CRS-D2:** Insert a temporary course with code `CRS-TEMP-999` and delete it using the course code.
3. **CRS-D3:** Preview and delete courses in the `Testing` category whose fee is below `5000`.

---

# 2. Instructor Directory

**Suggested table:** `instructors`

## Scenario

A training organisation needs one table containing instructor employment and payment information.

## Column Requirements

| Column | Data type | Description |
|---|---|---|
| `instructor_id` | `INT` | Numeric row number |
| `instructor_code` | `VARCHAR(12)` | Business identifier |
| `first_name` | `VARCHAR(60)` | |
| `last_name` | `VARCHAR(60)` | |
| `email` | `VARCHAR(120)` | |
| `specialization` | `VARCHAR(100)` | |
| `years_experience` | `INT` | |
| `hourly_rate` | `INT` | Whole rupees |
| `employment_type` | `VARCHAR(20)` | |
| `is_active` | `INT` | `1` = active, `0` = inactive |
| `joined_on` | `VARCHAR(10)` | `YYYY-MM-DD` text |
| `created_at` | `VARCHAR(10)` | `YYYY-MM-DD` text |

## A. CREATE Exercises

1. **INS-C1:** Create `instructors` using only INT and VARCHAR columns and no constraints.
2. Inspect the table structure using `DESCRIBE`.
3. Use `SHOW CREATE TABLE` and verify the table definition.

## B. INSERT Exercises

| Code | First name | Last name | Email | Specialization | Experience | Rate | Employment type | Active | Joined on |
|---|---|---|---|---|---:|---:|---|---|---|
| INS-JV-001 | Kavya | Menon | kavya.menon@example.test | Java | 8 | 1500 | FULL_TIME | 1 | 2021-06-14 |
| INS-DB-002 | Ritesh | Kumar | ritesh.kumar@example.test | Databases | 12 | 1800 | CONTRACT | 1 | 2019-02-01 |
| INS-WB-003 | Farah | Ali | farah.ali@example.test | Web Development | 5 | 1200 | PART_TIME | 1 | 2023-08-21 |
| INS-QA-004 | Nitin | Bose | nitin.bose@example.test | Software Testing | 7 | 1350 | PART_TIME | 1 | 2022-01-10 |
| INS-OLD-005 | Leela | Shah | leela.shah@example.test | Mainframe Systems | 25 | 2000 | CONTRACT | 0 | 2010-05-17 |

1. **INS-I1:** Insert the first instructor.
2. **INS-I2:** Insert the next two instructors and supply every column value explicitly for `INS-WB-003`.
3. **INS-I3:** Insert the remaining two instructors using one multi-row statement.
4. Insert one additional valid sample row with values of your choice.

## C. UPDATE Exercises

1. **INS-U1:** Increase `INS-QA-004` hourly rate to `1500`.
2. **INS-U2:** Increase the hourly rate of every active contract instructor by `8%`, rounding to a whole number.
3. **INS-U3:** Change the specialization of `INS-WB-003` to `Full-Stack Web Development`.
4. **INS-U4:** Increase the experience of all active instructors by one year and then query for instructors whose experience exceeds `50`.
5. **INS-U5:** Deactivate `INS-OLD-005` only if it is not already inactive; observe the affected-row count.

## D. DELETE Exercises

1. **INS-D1:** Preview and delete inactive instructor `INS-OLD-005`.
2. **INS-D2:** Insert an instructor with code `INS-TEMP-99` and then delete only that row.
3. **INS-D3:** Preview and delete active part-time instructors having fewer than `6` years of experience.

---

# 3. Warehouse Capacity Register

**Suggested table:** `warehouses`

## Scenario

A logistics company needs one independent table for warehouse location, capacity, occupancy, facilities, and operating status.

## Column Requirements

| Column | Data type | Description |
|---|---|---|
| `warehouse_id` | `INT` | Numeric row number |
| `warehouse_code` | `VARCHAR(10)` | Business identifier |
| `warehouse_name` | `VARCHAR(100)` | |
| `city` | `VARCHAR(80)` | |
| `state` | `VARCHAR(80)` | |
| `capacity_units` | `INT` | |
| `occupied_units` | `INT` | |
| `manager_name` | `VARCHAR(100)` | |
| `temperature_controlled` | `INT` | `1` = yes, `0` = no |
| `operational_status` | `VARCHAR(20)` | |
| `created_at` | `VARCHAR(10)` | `YYYY-MM-DD` text |

## A. CREATE Exercises

1. **WHS-C1:** Create `warehouses` using only INT and VARCHAR columns and no constraints.
2. Inspect the table structure using `DESCRIBE`.
3. Use `SHOW CREATE TABLE` and verify the table definition.

## B. INSERT Exercises

| Code | Name | City | State | Capacity | Occupied | Manager | Temperature controlled | Status |
|---|---|---|---|---:|---:|---|---|---|
| WH-BLR-01 | Bengaluru Central | Bengaluru | Karnataka | 10000 | 6400 | Ajay Nair | 0 | ACTIVE |
| WH-HYD-02 | Hyderabad North | Hyderabad | Telangana | 8000 | 7900 | Sana Reddy | 1 | ACTIVE |
| WH-MUM-03 | Mumbai Port Store | Mumbai | Maharashtra | 15000 | 9000 | Rohit Shah | 0 | MAINTENANCE |
| WH-KOC-04 | Kochi Cold Hub | Kochi | Kerala | 6000 | 3200 | Meera Varma | 1 | ACTIVE |
| WH-OLD-05 | Training Closed Store | Pune | Maharashtra | 2000 | 0 | Test Manager | 0 | CLOSED |

1. **WHS-I1:** Insert the Bengaluru warehouse.
2. **WHS-I2:** Insert the Hyderabad and Mumbai warehouses in one statement.
3. **WHS-I3:** Insert the remaining warehouses and supply an explicit status for `WH-KOC-04`.
4. Insert another valid warehouse row with a different warehouse code.

## C. UPDATE Exercises

1. **WHS-U1:** Add `500` occupied units to `WH-BLR-01`.
2. **WHS-U2:** Reduce `WH-HYD-02` occupancy by `1000` units.
3. **WHS-U3:** Change `WH-MUM-03` from `MAINTENANCE` to `ACTIVE`.
4. **WHS-U4:** Increase the capacity of every temperature-controlled warehouse by `1000` units.
5. **WHS-U5:** Set occupied units above capacity and verify the updated value with SELECT.

## D. DELETE Exercises

1. **WHS-D1:** Preview and delete the closed warehouse `WH-OLD-05`.
2. **WHS-D2:** Insert a temporary empty warehouse with code `WH-TMP-99` and delete it by code.
3. **WHS-D3:** Preview and delete active warehouses whose occupied quantity is less than half of their capacity.

---

# 4. Shipment Tracking Register

**Suggested table:** `shipments`

## Scenario

A parcel service needs one table for basic shipment, delivery, cost, priority, and status information.

## Column Requirements

| Column | Data type | Description |
|---|---|---|
| `shipment_id` | `INT` | Numeric row number |
| `tracking_number` | `VARCHAR(20)` | Business identifier |
| `sender_name` | `VARCHAR(120)` | |
| `recipient_name` | `VARCHAR(120)` | |
| `destination_city` | `VARCHAR(80)` | |
| `package_weight_grams` | `INT` | Weight in grams |
| `shipping_cost` | `INT` | Whole rupees |
| `shipped_date` | `VARCHAR(10)` | `YYYY-MM-DD` text |
| `expected_delivery_date` | `VARCHAR(10)` | `YYYY-MM-DD` text |
| `delivered_date` | `VARCHAR(10)` | `YYYY-MM-DD` text, `NULL` until delivered |
| `shipment_status` | `VARCHAR(20)` | |
| `priority` | `VARCHAR(10)` | |
| `created_at` | `VARCHAR(10)` | `YYYY-MM-DD` text |

## A. CREATE Exercises

1. **SHP-C1:** Create `shipments` using only INT and VARCHAR columns and no constraints.
2. Inspect the table structure using `DESCRIBE`.
3. Use `SHOW CREATE TABLE` and verify the table definition.

## B. INSERT Exercises

| Tracking number | Sender | Recipient | Destination | Weight (g) | Cost | Shipped | Expected | Delivered | Status | Priority |
|---|---|---|---|---:|---:|---|---|---|---|---|
| TRK26000001 | Asha Stores | Nitin Rao | Chennai | 2500 | 180 | 2026-09-20 | 2026-09-24 | NULL | IN_TRANSIT | NORMAL |
| TRK26000002 | Nova Tech | Isha Sen | Bengaluru | 800 | 250 | 2026-09-21 | 2026-09-23 | 2026-09-23 | DELIVERED | EXPRESS |
| TRK26000003 | Book Nest | Omar Ali | Kochi | 4200 | 220 | 2026-09-22 | 2026-09-27 | NULL | CREATED | NORMAL |
| TRK26000004 | Green Foods | Meera Das | Hyderabad | 12000 | 550 | 2026-09-22 | 2026-09-25 | NULL | IN_TRANSIT | EXPRESS |
| TRK26000005 | Test Sender | Test Receiver | Pune | 1000 | 100 | 2026-09-23 | 2026-09-26 | NULL | CANCELLED | NORMAL |

1. **SHP-I1:** Insert the first shipment.
2. **SHP-I2:** Insert the delivered shipment and preserve its delivered date.
3. **SHP-I3:** Insert the third shipment by supplying explicit values for every column.
4. **SHP-I4:** Insert the remaining two shipments using one multi-row statement.

## C. UPDATE Exercises

1. **SHP-U1:** Change `TRK26000001` to `DELIVERED` and set its delivered date to `2026-09-24`.
2. **SHP-U2:** Change `TRK26000003` status from `CREATED` to `IN_TRANSIT`.
3. **SHP-U3:** Increase the cost of every express shipment by `50`.
4. **SHP-U4:** Postpone the expected delivery of `TRK26000004` to `2026-09-27`.
5. **SHP-U5:** Set a delivered date earlier than the shipped date and inspect the stored value.

## D. DELETE Exercises

1. **SHP-D1:** Preview and delete the cancelled shipment `TRK26000005`.
2. **SHP-D2:** Insert a temporary shipment with tracking number `TRK-TEMP-999` and delete it by tracking number.
3. **SHP-D3:** Preview and delete delivered express shipments weighing less than `1000` grams.

---

# 5. Service Subscription Register

**Suggested table:** `subscriptions`

## Scenario

A digital service needs one independent table for subscriber, plan, billing, renewal, date, and status information.

## Column Requirements

| Column | Data type | Description |
|---|---|---|
| `subscription_id` | `INT` | Numeric row number |
| `subscription_code` | `VARCHAR(16)` | Business identifier |
| `subscriber_name` | `VARCHAR(120)` | |
| `subscriber_email` | `VARCHAR(120)` | |
| `plan_name` | `VARCHAR(60)` | |
| `billing_cycle` | `VARCHAR(20)` | |
| `amount` | `INT` | Whole rupees |
| `start_date` | `VARCHAR(10)` | `YYYY-MM-DD` text |
| `end_date` | `VARCHAR(10)` | `YYYY-MM-DD` text, may be `NULL` |
| `auto_renew` | `INT` | `1` = yes, `0` = no |
| `subscription_status` | `VARCHAR(20)` | |
| `created_at` | `VARCHAR(10)` | `YYYY-MM-DD` text |

## A. CREATE Exercises

1. **SUB-C1:** Create `subscriptions` using only INT and VARCHAR columns and no constraints.
2. Inspect the table structure using `DESCRIBE`.
3. Use `SHOW CREATE TABLE` and verify the table definition.

## B. INSERT Exercises

| Code | Subscriber | Email | Plan | Cycle | Amount | Start date | End date | Auto-renew | Status |
|---|---|---|---|---|---:|---|---|---|---|
| SUB260001 | Aarav Nair | aarav.nair@example.test | Standard | MONTHLY | 499 | 2026-09-01 | NULL | 1 | ACTIVE |
| SUB260002 | Diya Shah | diya.shah@example.test | Premium | YEARLY | 4999 | 2026-01-15 | 2027-01-14 | 1 | ACTIVE |
| SUB260003 | Kabir Rao | kabir.rao@example.test | Basic | MONTHLY | 199 | 2026-09-10 | NULL | 1 | ACTIVE |
| SUB260004 | Meera Bose | meera.bose@example.test | Premium | QUARTERLY | 1399 | 2026-07-01 | 2026-09-30 | 0 | PAUSED |
| SUB260005 | Test Subscriber | test.subscriber@example.test | Standard | MONTHLY | 499 | 2026-08-01 | 2026-08-31 | 0 | CANCELLED |

1. **SUB-I1:** Insert the first two subscriptions.
2. **SUB-I2:** Insert `SUB260003` by supplying explicit values for every column.
3. **SUB-I3:** Insert the remaining two subscriptions.
4. Insert one additional valid sample row with values of your choice.

## C. UPDATE Exercises

1. **SUB-U1:** Upgrade `SUB260001` to `Premium` and change its amount to `799`.
2. **SUB-U2:** Change `SUB260004` from `PAUSED` to `ACTIVE` and enable auto-renewal.
3. **SUB-U3:** Increase the amount of every monthly active subscription by `5%`, rounding to a whole number.
4. **SUB-U4:** Cancel `SUB260003`, disable auto-renewal, and set an appropriate end date.
5. **SUB-U5:** Set an end date earlier than the start date and inspect the stored value.

## D. DELETE Exercises

1. **SUB-D1:** Preview and delete the test subscription `SUB260005`.
2. **SUB-D2:** Insert a temporary subscription with code `SUB-TEMP-999` and delete it by code.
3. **SUB-D3:** Preview and delete cancelled subscriptions for which auto-renew is 0.

---

# 6. Event Schedule

**Suggested table:** `events`

## Scenario

An event organiser needs one table containing event schedule, venue, capacity, fee, format, and status information.

## Column Requirements

| Column | Data type | Description |
|---|---|---|
| `event_id` | `INT` | Numeric row number |
| `event_code` | `VARCHAR(15)` | Business identifier |
| `event_name` | `VARCHAR(150)` | |
| `venue` | `VARCHAR(150)` | |
| `city` | `VARCHAR(80)` | |
| `start_date` | `VARCHAR(10)` | `YYYY-MM-DD` text |
| `end_date` | `VARCHAR(10)` | `YYYY-MM-DD` text |
| `capacity` | `INT` | |
| `registration_fee` | `INT` | Whole rupees |
| `event_type` | `VARCHAR(20)` | |
| `event_status` | `VARCHAR(20)` | |
| `created_at` | `VARCHAR(10)` | `YYYY-MM-DD` text |

## A. CREATE Exercises

1. **EVT-C1:** Create `events` using VARCHAR(10) columns for the event dates. Do not use DATE, DATETIME, or constraints.
2. Inspect the table structure using `DESCRIBE`.
3. Use `SHOW CREATE TABLE` and verify the table definition.

## B. INSERT Exercises

| Code | Event name | Venue | City | Start | End | Capacity | Fee | Type | Status |
|---|---|---|---|---|---|---:|---:|---|---|
| EVT-JAVA-01 | Java Developer Meetup | Tech Hall | Bengaluru | 2026-10-10 | 2026-10-10 | 250 | 500 | OFFLINE | OPEN |
| EVT-CLOUD-02 | Cloud Fundamentals Webinar | Online Platform | Online | 2026-10-12 | 2026-10-12 | 1000 | 0 | ONLINE | OPEN |
| EVT-DATA-03 | Data Engineering Summit | Convention Centre | Hyderabad | 2026-11-05 | 2026-11-06 | 600 | 2500 | HYBRID | PLANNED |
| EVT-UI-04 | UI Design Workshop | Creative Hub | Chennai | 2026-10-20 | 2026-10-20 | 80 | 1200 | OFFLINE | PLANNED |
| EVT-OLD-05 | Cancelled Training Event | Test Venue | Pune | 2026-10-01 | 2026-10-01 | 30 | 100 | OFFLINE | CANCELLED |

1. **EVT-I1:** Insert the first event.
2. **EVT-I2:** Insert the webinar and summit using one multi-row statement.
3. **EVT-I3:** Insert the workshop by supplying explicit values for every column.
4. **EVT-I4:** Insert the cancelled event.

## C. UPDATE Exercises

1. **EVT-U1:** Increase the summit capacity to `750`.
2. **EVT-U2:** Change `EVT-UI-04` status from `PLANNED` to `OPEN`.
3. **EVT-U3:** Increase the registration fee of every paid offline event by `10%`, rounding to a whole number.
4. **EVT-U4:** Reschedule both dates of `EVT-CLOUD-02` one day later. The new values must still be stored as `YYYY-MM-DD` text.
5. **EVT-U5:** Set the event end date equal to its start date and inspect the stored value.

## D. DELETE Exercises

1. **EVT-D1:** Preview and delete `EVT-OLD-05`.
2. **EVT-D2:** Insert an event with code `EVT-TEMP-99` and delete it by code.
3. **EVT-D3:** Preview and delete free online events whose status is `OPEN`.

---

# 7. Organisation Device Register

**Suggested table:** `devices`

## Scenario

An organisation needs one table for its technology assets, purchase information, warranty, assignment, and status.

## Column Requirements

| Column | Data type | Description |
|---|---|---|
| `device_id` | `INT` | Numeric row number |
| `asset_tag` | `VARCHAR(20)` | Business identifier |
| `serial_number` | `VARCHAR(50)` | |
| `device_name` | `VARCHAR(120)` | |
| `device_type` | `VARCHAR(20)` | |
| `manufacturer` | `VARCHAR(80)` | |
| `model` | `VARCHAR(100)` | |
| `purchase_date` | `VARCHAR(10)` | `YYYY-MM-DD` text |
| `purchase_price` | `INT` | Whole rupees |
| `warranty_expiry` | `VARCHAR(10)` | `YYYY-MM-DD` text, may be `NULL` |
| `assigned_to` | `VARCHAR(120)` | |
| `device_status` | `VARCHAR(20)` | |
| `created_at` | `VARCHAR(10)` | `YYYY-MM-DD` text |

## A. CREATE Exercises

1. **DEV-C1:** Create `devices` using only INT and VARCHAR columns and no constraints.
2. Inspect the table structure using `DESCRIBE`.
3. Use `SHOW CREATE TABLE` and verify the table definition.

## B. INSERT Exercises

| Asset tag | Serial number | Name | Type | Manufacturer | Model | Purchased | Price | Warranty | Assigned to | Status |
|---|---|---|---|---|---|---|---:|---|---|---|
| AST-LAP-001 | SN-LAP-260001 | Developer Laptop | LAPTOP | Lenovo | ThinkPad E14 | 2026-01-15 | 78000 | 2029-01-14 | Kavya Menon | ASSIGNED |
| AST-DES-002 | SN-DES-260002 | Lab Desktop | DESKTOP | Dell | OptiPlex 7010 | 2025-08-10 | 62000 | 2028-08-09 | NULL | AVAILABLE |
| AST-TAB-003 | SN-TAB-260003 | Demo Tablet | TABLET | Samsung | Galaxy Tab S9 | 2026-03-05 | 68000 | 2028-03-04 | NULL | AVAILABLE |
| AST-RTR-004 | SN-RTR-260004 | Office Router | ROUTER | Cisco | RV340 | 2024-06-20 | 28000 | NULL | Network Team | REPAIR |
| AST-OLD-005 | SN-OLD-260005 | Retired Phone | PHONE | Nokia | Test Model | 2020-01-10 | 8000 | 2021-01-09 | NULL | RETIRED |

1. **DEV-I1:** Insert the laptop.
2. **DEV-I2:** Insert the desktop and tablet, using the explicit status value `AVAILABLE`.
3. **DEV-I3:** Insert the remaining two devices.
4. Insert one additional valid sample row with values of your choice.

## C. UPDATE Exercises

1. **DEV-U1:** Assign `AST-DES-002` to `Rohan Das` and change its status to `ASSIGNED`.
2. **DEV-U2:** Change `AST-RTR-004` from `REPAIR` to `AVAILABLE` and clear its assignee.
3. **DEV-U3:** Extend the laptop warranty to `2030-01-14`.
4. **DEV-U4:** Increase the recorded purchase price of every tablet by `3%` for a valuation exercise, rounding to a whole number.
5. **DEV-U5:** Change a warranty date to a value before the purchase date and inspect the stored value.

## D. DELETE Exercises

1. **DEV-D1:** Preview and delete the retired test device `AST-OLD-005`.
2. **DEV-D2:** Insert a temporary device tagged `AST-TEMP-999` and delete it by asset tag.
3. **DEV-D3:** Preview and delete available devices that have no assignee but still have a warranty-expiry date.

---

# 8. Restaurant Directory

**Suggested table:** `restaurants`

## Scenario

A dining directory needs one table containing restaurant identity, contact, capacity, price, rating, food preference, and operating status.

## Column Requirements

| Column | Data type | Description |
|---|---|---|
| `restaurant_id` | `INT` | Numeric row number |
| `restaurant_code` | `VARCHAR(12)` | Business identifier |
| `restaurant_name` | `VARCHAR(120)` | |
| `cuisine_type` | `VARCHAR(80)` | |
| `city` | `VARCHAR(80)` | |
| `phone` | `VARCHAR(15)` | |
| `seating_capacity` | `INT` | |
| `average_cost_for_two` | `INT` | Whole rupees |
| `rating_x10` | `INT` | Rating in tenths (`4.4` is stored as `44`) |
| `vegetarian_only` | `INT` | `1` = yes, `0` = no |
| `opening_status` | `VARCHAR(25)` | |
| `opened_date` | `VARCHAR(10)` | `YYYY-MM-DD` text |
| `created_at` | `VARCHAR(10)` | `YYYY-MM-DD` text |

## A. CREATE Exercises

1. **RES-C1:** Create `restaurants` using only INT and VARCHAR columns and no constraints.
2. Inspect the table structure using `DESCRIBE`.
3. Use `SHOW CREATE TABLE` and verify the table definition.

## B. INSERT Exercises

| Code | Name | Cuisine | City | Phone | Seats | Cost for two | Rating (x10) | Vegetarian only | Status | Opened date |
|---|---|---|---|---|---:|---:|---:|---|---|---|
| RES-BLR-001 | Spice Courtyard | Indian | Bengaluru | 9876601001 | 80 | 1200 | 44 | 0 | OPEN | 2018-06-15 |
| RES-CHE-002 | Green Banana Leaf | South Indian | Chennai | 9876601002 | 60 | 700 | 46 | 1 | OPEN | 2020-02-10 |
| RES-MUM-003 | Coastal Plate | Seafood | Mumbai | 9876601003 | 100 | 1800 | 42 | 0 | OPEN | 2017-09-21 |
| RES-HYD-004 | Urban Bowl | Fusion | Hyderabad | 9876601004 | 45 | 950 | 0 | 0 | OPEN | 2026-01-12 |
| RES-OLD-005 | Training Cafe | Cafe | Pune | 9876601005 | 20 | 400 | 20 | 0 | PERMANENTLY_CLOSED | 2015-05-01 |

1. **RES-I1:** Insert the first restaurant.
2. **RES-I2:** Insert the next two restaurants using one multi-row statement.
3. **RES-I3:** Insert `RES-HYD-004` by supplying explicit values for every column.
4. **RES-I4:** Insert the permanently closed training restaurant.

## C. UPDATE Exercises

1. **RES-U1:** Change the rating of `RES-BLR-001` to `4.5` (store `45`).
2. **RES-U2:** Increase average cost by `10%` for restaurants in Mumbai, rounding to a whole number.
3. **RES-U3:** Change `RES-HYD-004` rating to `4.0` (store `40`) and mark it vegetarian-only.
4. **RES-U4:** Increase seating capacity by `10` for every open restaurant with fewer than `60` seats.
5. **RES-U5:** Set a rating above `5.0` (a value above `50`) and inspect the stored value.

## D. DELETE Exercises

1. **RES-D1:** Preview and delete `RES-OLD-005`.
2. **RES-D2:** Insert a restaurant with code `RES-TEMP-999` and delete it by code.
3. **RES-D3:** Preview and delete open restaurants having a rating below `4.1` (a value below `41`).

---

# 9. Insurance Policy Register

**Suggested table:** `insurance_policies`

## Scenario

A fictional training system needs one simplified table for policyholder, coverage, premium, term, payment, nominee, and status information.

## Column Requirements

| Column | Data type | Description |
|---|---|---|
| `policy_id` | `INT` | Numeric row number |
| `policy_number` | `VARCHAR(14)` | Business identifier |
| `policyholder_name` | `VARCHAR(120)` | |
| `policy_type` | `VARCHAR(20)` | |
| `coverage_amount` | `INT` | Whole rupees |
| `premium_amount` | `INT` | Whole rupees |
| `start_date` | `VARCHAR(10)` | `YYYY-MM-DD` text |
| `end_date` | `VARCHAR(10)` | `YYYY-MM-DD` text |
| `payment_frequency` | `VARCHAR(20)` | |
| `nominee_name` | `VARCHAR(120)` | |
| `policy_status` | `VARCHAR(20)` | |
| `created_at` | `VARCHAR(10)` | `YYYY-MM-DD` text |

## A. CREATE Exercises

1. **POL-C1:** Create `insurance_policies` using only INT and VARCHAR columns and no constraints.
2. Inspect the table structure using `DESCRIBE`.
3. Use `SHOW CREATE TABLE` and verify the table definition.

## B. INSERT Exercises

All policy information below is fictional.

| Policy number | Holder | Type | Coverage | Premium | Start | End | Frequency | Nominee | Status |
|---|---|---|---:|---:|---|---|---|---|---|
| POL00000000001 | Aditi Rao | HEALTH | 1000000 | 18000 | 2026-01-01 | 2026-12-31 | ANNUAL | Rohan Rao | ACTIVE |
| POL00000000002 | Dev Kapoor | VEHICLE | 800000 | 22000 | 2026-04-15 | 2027-04-14 | QUARTERLY | NULL | ACTIVE |
| POL00000000003 | Meera Nair | LIFE | 5000000 | 36000 | 2026-06-01 | 2046-05-31 | ANNUAL | Arun Nair | ACTIVE |
| POL00000000004 | Kabir Shah | TRAVEL | 500000 | 4500 | 2026-10-01 | 2026-10-31 | MONTHLY | NULL | ACTIVE |
| POL00000000005 | Test Policyholder | HOME | 2000000 | 15000 | 2025-01-01 | 2025-12-31 | ANNUAL | NULL | CANCELLED |

1. **POL-I1:** Insert the health and vehicle policies.
2. **POL-I2:** Insert the life policy and use the explicit values shown in the sample data.
3. **POL-I3:** Insert the remaining two policies.
4. Insert one additional valid sample row with values of your choice.

## C. UPDATE Exercises

1. **POL-U1:** Increase the coverage of `POL00000000001` to `1250000`.
2. **POL-U2:** Add nominee `Sara Kapoor` to `POL00000000002`.
3. **POL-U3:** Increase premiums of active vehicle policies by `5%`, rounding to a whole number.
4. **POL-U4:** Change `POL00000000004` payment frequency to `ANNUAL`.
5. **POL-U5:** Set a premium greater than its coverage amount and inspect the stored value.

## D. DELETE Exercises

1. **POL-D1:** Preview and delete fictional cancelled policy `POL00000000005`.
2. **POL-D2:** Insert a temporary fictional policy numbered `POL99999999999` and delete it by policy number.
3. **POL-D3:** Preview and delete travel policies having no nominee and a premium below `5000`.

> Real insurance systems normally retain or archive policy history. Physical deletion here is strictly for database practice.

---

# 10. Job Posting Board

**Suggested table:** `job_postings`

## Scenario

A recruitment portal needs one independent table for job descriptions, location, employment type, salary range, vacancies, dates, and status.

## Column Requirements

| Column | Data type | Description |
|---|---|---|
| `job_id` | `INT` | Numeric row number |
| `job_code` | `VARCHAR(15)` | Business identifier |
| `job_title` | `VARCHAR(150)` | |
| `department` | `VARCHAR(100)` | |
| `location` | `VARCHAR(100)` | |
| `employment_type` | `VARCHAR(20)` | |
| `minimum_salary` | `INT` | Annual, whole rupees |
| `maximum_salary` | `INT` | Annual, whole rupees |
| `vacancies` | `INT` | |
| `posted_date` | `VARCHAR(10)` | `YYYY-MM-DD` text |
| `closing_date` | `VARCHAR(10)` | `YYYY-MM-DD` text |
| `job_status` | `VARCHAR(20)` | |
| `created_at` | `VARCHAR(10)` | `YYYY-MM-DD` text |

## A. CREATE Exercises

1. **JOB-C1:** Create `job_postings` using only INT and VARCHAR columns and no constraints.
2. Inspect the table structure using `DESCRIBE`.
3. Use `SHOW CREATE TABLE` and verify the table definition.

## B. INSERT Exercises

| Job code | Title | Department | Location | Type | Minimum salary | Maximum salary | Vacancies | Posted | Closing | Status |
|---|---|---|---|---|---:|---:|---:|---|---|---|
| JOB-JAVA-001 | Java Developer | Engineering | Bengaluru | FULL_TIME | 700000 | 1200000 | 3 | 2026-09-20 | 2026-10-20 | OPEN |
| JOB-QA-002 | QA Automation Engineer | Quality Assurance | Hyderabad | CONTRACT | 600000 | 900000 | 2 | 2026-09-21 | 2026-10-15 | OPEN |
| JOB-INT-003 | Software Intern | Engineering | Chennai | INTERNSHIP | 180000 | 240000 | 1 | 2026-09-22 | 2026-10-10 | OPEN |
| JOB-HR-004 | HR Coordinator | Human Resources | Mumbai | PART_TIME | 300000 | 450000 | 1 | 2026-09-23 | 2026-10-18 | DRAFT |
| JOB-OLD-005 | Cancelled Test Role | Training | Pune | FULL_TIME | 250000 | 350000 | 1 | 2026-09-01 | 2026-09-15 | CANCELLED |

1. **JOB-I1:** Insert the Java and QA positions.
2. **JOB-I2:** Insert the internship with all column values explicitly supplied.
3. **JOB-I3:** Insert the remaining positions.
4. Insert one additional valid sample row with values of your choice.

## C. UPDATE Exercises

1. **JOB-U1:** Increase the maximum salary of `JOB-JAVA-001` to `1300000`.
2. **JOB-U2:** Increase vacancies for `JOB-QA-002` from `2` to `4`.
3. **JOB-U3:** Change `JOB-HR-004` from `DRAFT` to `OPEN`.
4. **JOB-U4:** Increase both salary limits of every open engineering job by `8%`, rounding to a whole number.
5. **JOB-U5:** Set maximum salary lower than minimum salary and inspect the stored value.

## D. DELETE Exercises

1. **JOB-D1:** Preview and delete `JOB-OLD-005`.
2. **JOB-D2:** Insert a temporary posting with code `JOB-TEMP-999` and delete it by code.
3. **JOB-D3:** Preview and delete internship postings whose maximum salary is at most `250000`.

---

# Submission Checklist

- [ ] All 10 tables were created successfully.
- [ ] Every column uses only INT or VARCHAR.
- [ ] No constraints or automatic value-generation rules were defined.
- [ ] Dates were stored as `YYYY-MM-DD` text.
- [ ] Valid single-row inserts were completed.
- [ ] Valid multi-row inserts were completed.
- [ ] NULL and duplicate values were explored.
- [ ] Single-row updates use meaningful identifying conditions.
- [ ] Multi-row updates use carefully reviewed conditions.
- [ ] Every delete was previewed using SELECT.
- [ ] Every delete contains a precise WHERE clause.
- [ ] Final table contents were verified.

---
