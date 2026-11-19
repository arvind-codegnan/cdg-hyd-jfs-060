# CDG-HYD-JFS-060

## SQL Exercise Pack 2

This pack contains 10 standalone-table exercises. Each table uses only the following MySQL data types:

- `INT`
- `DECIMAL`
- `VARCHAR`
- `DATE`
- `TIME`
- `DATETIME`

Learners will practise:

- Creating tables using the six specified data types.
- Understanding how columns behave without constraints.
- Inserting single and multiple rows.
- Working with decimal, date, time, and datetime values.
- Updating individual and multiple rows.
- Deleting rows safely using precise `WHERE` conditions.

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

- Use only `INT`, `DECIMAL`, `VARCHAR`, `DATE`, `TIME`, and `DATETIME` for column definitions.
- Do not define any constraints or automatic value-generation rules.
- All columns are nullable; do not add `NOT NULL`.
- Supply values explicitly when inserting sample records.

## Recommended Order for Every Use Case

1. Read the scenario and column requirements.
2. Write and execute the `CREATE TABLE` statement.
3. Inspect the structure using `DESCRIBE` or `SHOW CREATE TABLE`.
4. Complete the insert exercises.
5. Review inserted rows using `SELECT`.
6. Complete the update exercises.
7. Complete the delete exercises.
8. Verify the final contents of the table.

---

# 1. Online Course Catalogue

**Suggested table:** `courses`

## Scenario

A training institute needs one table containing course details, fees, duration, schedule, and course creation information.

## Column Requirements

| Column | Data type | Description |
|---|---|---|
| `course_id` | `INT` | Numeric row number |
| `course_code` | `VARCHAR(15)` | Course identifier |
| `course_title` | `VARCHAR(150)` | Course name |
| `category` | `VARCHAR(60)` | Course category |
| `duration_hours` | `INT` | Total course duration |
| `fee` | `DECIMAL(10,2)` | Course fee in rupees |
| `discount_percentage` | `DECIMAL(5,2)` | Discount percentage |
| `delivery_mode` | `VARCHAR(20)` | ONLINE, CLASSROOM, HYBRID |
| `start_date` | `DATE` | Course start date |
| `class_start_time` | `TIME` | Daily class start time |
| `class_end_time` | `TIME` | Daily class end time |
| `created_at` | `DATETIME` | Record creation date and time |

## A. CREATE Exercises

1. **CRS-C1:** Create `courses` using the specified data types. Do not define constraints.
2. Inspect the table structure using `DESCRIBE`.
3. Use `SHOW CREATE TABLE` and verify that no constraints are defined.

## B. INSERT Exercises

| Course code | Title | Category | Hours | Fee | Discount | Mode | Start date | Start time | End time | Created at |
|---|---|---|---:|---:|---:|---|---|---|---|---|
| CRS-JAVA-101 | Java Fundamentals | Programming | 40 | 6500.00 | 10.00 | CLASSROOM | 2026-12-01 | 09:00:00 | 11:00:00 | 2026-11-19 09:00:00 |
| CRS-SQL-102 | MySQL Essentials | Database | 32 | 4500.50 | 5.00 | ONLINE | 2026-12-05 | 10:00:00 | 12:00:00 | 2026-11-19 09:15:00 |
| CRS-WEB-103 | Web Development | Web Development | 60 | 8500.00 | 12.50 | HYBRID | 2027-01-10 | 14:00:00 | 16:00:00 | 2026-11-19 09:30:00 |
| CRS-TST-104 | Software Testing | Testing | 24 | 3500.75 | 0.00 | ONLINE | 2026-12-15 | 15:00:00 | 17:00:00 | 2026-11-19 09:45:00 |
| CRS-PYT-105 | Python Basics | Programming | 36 | 5500.25 | 7.50 | CLASSROOM | 2027-01-05 | 09:30:00 | 11:30:00 | 2026-11-19 10:00:00 |

1. **CRS-I1:** Insert the Java course using an explicit column list.
2. **CRS-I2:** Insert the SQL and Web Development courses using one multi-row statement.
3. **CRS-I3:** Insert the remaining two courses.
4. Insert one additional course with a fractional fee and discount.
5. Insert a course whose class starts at `08:30:00` and ends at `10:30:00`.

## C. UPDATE Exercises

1. **CRS-U1:** Change the fee of `CRS-JAVA-101` to `7000.00`.
2. **CRS-U2:** Increase the fee of every online course by `8.50%`.
3. **CRS-U3:** Change `CRS-WEB-103` delivery mode to `ONLINE`.
4. **CRS-U4:** Change the start date of `CRS-PYT-105` to `2027-01-15`.
5. **CRS-U5:** Change the class timings of all classroom courses to `10:00:00`–`12:00:00`.
6. **CRS-U6:** Update the `created_at` value of one course to a different datetime.

---

# 2. Instructor Directory

**Suggested table:** `instructors`

## Scenario

A training organisation needs one table containing instructor personal details, experience, payment information, joining date, and working hours.

## Column Requirements

| Column | Data type | Description |
|---|---|---|
| `instructor_id` | `INT` | Numeric row number |
| `instructor_code` | `VARCHAR(12)` | Instructor identifier |
| `first_name` | `VARCHAR(60)` | First name |
| `last_name` | `VARCHAR(60)` | Last name |
| `email` | `VARCHAR(120)` | Email address |
| `specialization` | `VARCHAR(100)` | Technical specialization |
| `years_experience` | `INT` | Years of experience |
| `hourly_rate` | `DECIMAL(8,2)` | Payment per hour |
| `employment_type` | `VARCHAR(20)` | FULL_TIME, CONTRACT, PART_TIME |
| `joined_on` | `DATE` | Joining date |
| `work_start_time` | `TIME` | Working hours start |
| `work_end_time` | `TIME` | Working hours end |
| `created_at` | `DATETIME` | Record creation date and time |

## A. CREATE Exercises

1. **INS-C1:** Create `instructors` using the specified data types and no constraints.
2. Inspect the table structure using `DESCRIBE`.
3. Verify the table definition using `SHOW CREATE TABLE`.

## B. INSERT Exercises

| Code | First name | Last name | Specialization | Experience | Rate | Employment | Joined on | Start time | End time |
|---|---|---|---|---:|---:|---|---|---|---|
| INS-JV-001 | Kavya | Menon | Java | 8 | 1500.50 | FULL_TIME | 2021-06-14 | 09:00:00 | 18:00:00 |
| INS-DB-002 | Ritesh | Kumar | Databases | 12 | 1800.75 | CONTRACT | 2019-02-01 | 10:00:00 | 19:00:00 |
| INS-WB-003 | Farah | Ali | Web Development | 5 | 1200.00 | PART_TIME | 2023-08-21 | 14:00:00 | 18:00:00 |
| INS-QA-004 | Nitin | Bose | Software Testing | 7 | 1350.25 | PART_TIME | 2022-01-10 | 09:30:00 | 13:30:00 |
| INS-PY-005 | Leela | Shah | Python | 10 | 1650.00 | FULL_TIME | 2020-05-17 | 09:00:00 | 18:00:00 |

1. **INS-I1:** Insert the first instructor.
2. **INS-I2:** Insert the next two instructors using one multi-row statement.
3. **INS-I3:** Insert the remaining two instructors.
4. Insert one instructor with `0` years of experience.
5. Insert one instructor with an hourly rate containing decimal values.

## C. UPDATE Exercises

1. **INS-U1:** Increase the hourly rate of `INS-QA-004` to `1500.75`.
2. **INS-U2:** Increase the hourly rate of every active full-time instructor by `10%`.
3. **INS-U3:** Change the specialization of `INS-WB-003` to `Full-Stack Web Development`.
4. **INS-U4:** Update the joining date of `INS-PY-005` to `2020-06-01`.
5. **INS-U5:** Change the working hours of all part-time instructors to `10:00:00`–`14:00:00`.
6. **INS-U6:** Update the `created_at` value of one instructor.

---

# 3. Warehouse Capacity Register

**Suggested table:** `warehouses`

## Scenario

A logistics company needs one independent table for warehouse location, capacity, occupancy, rental cost, and operating schedule.

## Column Requirements

| Column | Data type | Description |
|---|---|---|
| `warehouse_id` | `INT` | Numeric row number |
| `warehouse_code` | `VARCHAR(10)` | Warehouse identifier |
| `warehouse_name` | `VARCHAR(100)` | Warehouse name |
| `city` | `VARCHAR(80)` | City |
| `state` | `VARCHAR(80)` | State |
| `capacity_units` | `INT` | Total storage capacity |
| `occupied_units` | `INT` | Currently occupied units |
| `monthly_rent` | `DECIMAL(12,2)` | Monthly rent |
| `temperature_controlled` | `INT` | 1 = yes, 0 = no |
| `operational_status` | `VARCHAR(20)` | ACTIVE, MAINTENANCE, CLOSED |
| `opening_time` | `TIME` | Daily opening time |
| `closing_time` | `TIME` | Daily closing time |
| `last_inspection` | `DATE` | Last inspection date |
| `created_at` | `DATETIME` | Record creation date and time |

## A. CREATE Exercises

1. **WHS-C1:** Create `warehouses` using the specified data types without constraints.
2. Inspect the structure using `DESCRIBE`.
3. Verify the definition using `SHOW CREATE TABLE`.

## B. INSERT Exercises

| Code | Name | City | Capacity | Occupied | Monthly rent | Temperature controlled | Status | Opens | Closes | Inspection |
|---|---|---|---:|---:|---:|---:|---:|---|---|---|
| WH-BLR-01 | Bengaluru Central | Bengaluru | 10000 | 6400 | 125000.50 | 0 | ACTIVE | 08:00:00 | 20:00:00 | 2026-10-01 |
| WH-HYD-02 | Hyderabad North | Hyderabad | 8000 | 7900 | 98000.00 | 1 | ACTIVE | 07:00:00 | 22:00:00 | 2026-09-15 |
| WH-MUM-03 | Mumbai Port Store | Mumbai | 15000 | 9000 | 175500.75 | 0 | MAINTENANCE | 09:00:00 | 18:00:00 | 2026-08-20 |
| WH-KOC-04 | Kochi Cold Hub | Kochi | 6000 | 3200 | 85000.25 | 1 | ACTIVE | 06:00:00 | 21:00:00 | 2026-10-10 |
| WH-PUN-05 | Pune Distribution Hub | Pune | 5000 | 2500 | 75000.00 | 0 | ACTIVE | 08:30:00 | 19:30:00 | 2026-10-25 |

1. **WHS-I1:** Insert the Bengaluru warehouse.
2. **WHS-I2:** Insert the Hyderabad and Mumbai warehouses in one statement.
3. **WHS-I3:** Insert the remaining warehouses.
4. Insert a warehouse with a monthly rent containing decimal values.
5. Insert a warehouse whose opening time is `06:30:00`.

## C. UPDATE Exercises

1. **WHS-U1:** Add `500` occupied units to `WH-BLR-01`.
2. **WHS-U2:** Reduce `WH-HYD-02` occupancy by `1000` units.
3. **WHS-U3:** Change `WH-MUM-03` status to `ACTIVE`.
4. **WHS-U4:** Increase the monthly rent of every temperature-controlled warehouse by `5.50%`.
5. **WHS-U5:** Change the last inspection date of `WH-KOC-04` to `2026-11-15`.
6. **WHS-U6:** Change the operating hours of all active warehouses to `07:00:00`–`21:00:00`.

---

# 4. Shipment Tracking Register

**Suggested table:** `shipments`

## Scenario

A parcel service needs one table for shipment details, package weight, shipping cost, dispatch time, delivery date, and shipment status.

## Column Requirements

| Column | Data type | Description |
|---|---|---|
| `shipment_id` | `INT` | Numeric row number |
| `tracking_number` | `VARCHAR(20)` | Tracking identifier |
| `sender_name` | `VARCHAR(120)` | Sender |
| `recipient_name` | `VARCHAR(120)` | Recipient |
| `destination_city` | `VARCHAR(80)` | Destination |
| `package_weight_kg` | `DECIMAL(8,3)` | Package weight in kilograms |
| `shipping_cost` | `DECIMAL(10,2)` | Shipping cost |
| `shipped_date` | `DATE` | Dispatch date |
| `shipped_time` | `TIME` | Dispatch time |
| `expected_delivery_date` | `DATE` | Expected delivery date |
| `delivered_at` | `DATETIME` | Actual delivery date and time |
| `shipment_status` | `VARCHAR(20)` | CREATED, IN_TRANSIT, DELIVERED, CANCELLED |
| `priority` | `VARCHAR(10)` | NORMAL, EXPRESS |
| `created_at` | `DATETIME` | Record creation date and time |

## A. CREATE Exercises

1. **SHP-C1:** Create `shipments` using the specified data types and no constraints.
2. Inspect the table using `DESCRIBE`.
3. Verify the definition using `SHOW CREATE TABLE`.

## B. INSERT Exercises

| Tracking number | Sender | Recipient | Destination | Weight (kg) | Cost | Shipped date | Shipped time | Expected date | Delivered at | Status | Priority |
|---|---|---|---|---:|---:|---|---|---|---|---|---|
| TRK26000001 | Asha Stores | Nitin Rao | Chennai | 2.500 | 180.50 | 2026-11-10 | 09:30:00 | 2026-11-14 | NULL | IN_TRANSIT | NORMAL |
| TRK26000002 | Nova Tech | Isha Sen | Bengaluru | 0.800 | 250.75 | 2026-11-11 | 11:15:00 | 2026-11-13 | 2026-11-13 15:30:00 | DELIVERED | EXPRESS |
| TRK26000003 | Book Nest | Omar Ali | Kochi | 4.200 | 220.00 | 2026-11-12 | 14:00:00 | 2026-11-17 | NULL | CREATED | NORMAL |
| TRK26000004 | Green Foods | Meera Das | Hyderabad | 12.000 | 550.50 | 2026-11-12 | 08:45:00 | 2026-11-15 | NULL | IN_TRANSIT | EXPRESS |
| TRK26000005 | Test Sender | Test Receiver | Pune | 1.000 | 100.25 | 2026-11-13 | 16:30:00 | 2026-11-16 | NULL | CANCELLED | NORMAL |

1. **SHP-I1:** Insert the first shipment.
2. **SHP-I2:** Insert the delivered shipment and provide its actual delivery datetime.
3. **SHP-I3:** Insert the third shipment with explicit values for every column.
4. **SHP-I4:** Insert the remaining two shipments using one multi-row statement.
5. Insert another shipment with a package weight of `0.750` kg.

## C. UPDATE Exercises

1. **SHP-U1:** Change `TRK26000001` status to `DELIVERED` and set its delivery datetime.
2. **SHP-U2:** Change `TRK26000003` status from `CREATED` to `IN_TRANSIT`.
3. **SHP-U3:** Increase the shipping cost of every express shipment by `50.00`.
4. **SHP-U4:** Postpone the expected delivery date of `TRK26000004` to `2026-11-18`.
5. **SHP-U5:** Change the dispatch time of `TRK26000003` to `10:30:00`.
6. **SHP-U6:** Update the delivered datetime of `TRK26000002`.

---

# 5. Service Subscription Register

**Suggested table:** `subscriptions`

## Scenario

A digital service needs one independent table for subscriber details, plan information, billing amount, renewal schedule, payment time, and subscription status.

## Column Requirements

| Column | Data type | Description |
|---|---|---|
| `subscription_id` | `INT` | Numeric row number |
| `subscription_code` | `VARCHAR(16)` | Subscription identifier |
| `subscriber_name` | `VARCHAR(120)` | Subscriber name |
| `subscriber_email` | `VARCHAR(120)` | Email address |
| `plan_name` | `VARCHAR(60)` | Plan name |
| `billing_cycle` | `VARCHAR(20)` | MONTHLY, QUARTERLY, YEARLY |
| `amount` | `DECIMAL(10,2)` | Subscription amount |
| `start_date` | `DATE` | Subscription start date |
| `end_date` | `DATE` | Subscription end date |
| `renewal_time` | `TIME` | Scheduled renewal time |
| `last_payment_at` | `DATETIME` | Last payment date and time |
| `auto_renew` | `INT` | 1 = yes, 0 = no |
| `subscription_status` | `VARCHAR(20)` | ACTIVE, PAUSED, CANCELLED |
| `created_at` | `DATETIME` | Record creation date and time |

## A. CREATE Exercises

1. **SUB-C1:** Create `subscriptions` using the specified data types and no constraints.
2. Inspect the structure using `DESCRIBE`.
3. Verify the table definition using `SHOW CREATE TABLE`.

## B. INSERT Exercises

| Code | Subscriber | Plan | Cycle | Amount | Start date | End date | Renewal time | Last payment | Auto-renew | Status |
|---|---|---|---|---:|---|---|---|---|---:|---|
| SUB260001 | Aarav Nair | Standard | MONTHLY | 499.00 | 2026-11-01 | 2026-11-30 | 01:00:00 | 2026-11-01 01:05:00 | 1 | ACTIVE |
| SUB260002 | Diya Shah | Premium | YEARLY | 4999.50 | 2026-01-15 | 2027-01-14 | 02:00:00 | 2026-11-15 02:10:00 | 1 | ACTIVE |
| SUB260003 | Kabir Rao | Basic | MONTHLY | 199.00 | 2026-11-10 | 2026-12-09 | 03:00:00 | 2026-11-10 03:05:00 | 1 | ACTIVE |
| SUB260004 | Meera Bose | Premium | QUARTERLY | 1399.75 | 2026-10-01 | 2026-12-31 | 04:00:00 | 2026-10-01 04:15:00 | 0 | PAUSED |
| SUB260005 | Rohan Das | Standard | MONTHLY | 499.00 | 2026-08-01 | 2026-08-31 | 01:30:00 | 2026-08-01 01:35:00 | 0 | CANCELLED |

1. **SUB-I1:** Insert the first two subscriptions.
2. **SUB-I2:** Insert `SUB260003` with all column values explicitly supplied.
3. **SUB-I3:** Insert the remaining two subscriptions.
4. Insert another subscription with an amount containing decimal values.
5. Insert a subscription with a renewal time of `05:30:00`.

## C. UPDATE Exercises

1. **SUB-U1:** Upgrade `SUB260001` to Premium and change its amount to `799.50`.
2. **SUB-U2:** Change `SUB260004` from `PAUSED` to `ACTIVE` and enable auto-renewal.
3. **SUB-U3:** Increase the amount of every monthly active subscription by `5.00%`.
4. **SUB-U4:** Cancel `SUB260003`, disable auto-renewal, and update its end date.
5. **SUB-U5:** Change the renewal time of all yearly subscriptions to `02:30:00`.
6. **SUB-U6:** Update the last payment datetime of `SUB260002`.

---

# 6. Event Schedule

**Suggested table:** `events`

## Scenario

An event organiser needs one table containing event schedule, venue, capacity, registration fee, and event timings.

## Column Requirements

| Column | Data type | Description |
|---|---|---|
| `event_id` | `INT` | Numeric row number |
| `event_code` | `VARCHAR(15)` | Event identifier |
| `event_name` | `VARCHAR(150)` | Event name |
| `venue` | `VARCHAR(150)` | Venue name |
| `city` | `VARCHAR(80)` | City |
| `start_date` | `DATE` | Event start date |
| `end_date` | `DATE` | Event end date |
| `start_time` | `TIME` | Event starting time |
| `end_time` | `TIME` | Event ending time |
| `capacity` | `INT` | Maximum participants |
| `registration_fee` | `DECIMAL(10,2)` | Registration fee |
| `event_type` | `VARCHAR(20)` | ONLINE, OFFLINE, HYBRID |
| `event_status` | `VARCHAR(20)` | OPEN, PLANNED, CANCELLED |
| `created_at` | `DATETIME` | Record creation date and time |

## A. CREATE Exercises

1. **EVT-C1:** Create `events` using `DATE` for event dates and `TIME` for event timings.
2. Inspect the structure using `DESCRIBE`.
3. Verify the definition using `SHOW CREATE TABLE`.

## B. INSERT Exercises

| Code | Event name | Venue | City | Start date | End date | Start time | End time | Capacity | Fee | Type | Status |
|---|---|---|---|---|---|---|---|---:|---:|---|---|
| EVT-JAVA-01 | Java Developer Meetup | Tech Hall | Bengaluru | 2026-12-10 | 2026-12-10 | 09:00:00 | 17:00:00 | 250 | 500.00 | OFFLINE | OPEN |
| EVT-CLOUD-02 | Cloud Fundamentals Webinar | Online Platform | Online | 2026-12-12 | 2026-12-12 | 10:00:00 | 12:00:00 | 1000 | 0.00 | ONLINE | OPEN |
| EVT-DATA-03 | Data Engineering Summit | Convention Centre | Hyderabad | 2027-01-05 | 2027-01-06 | 09:30:00 | 18:00:00 | 600 | 2500.50 | HYBRID | PLANNED |
| EVT-UI-04 | UI Design Workshop | Creative Hub | Chennai | 2026-12-20 | 2026-12-20 | 14:00:00 | 17:30:00 | 80 | 1200.75 | OFFLINE | PLANNED |
| EVT-PY-05 | Python Bootcamp | Learning Centre | Pune | 2027-01-10 | 2027-01-12 | 09:00:00 | 16:00:00 | 100 | 1800.00 | OFFLINE | OPEN |

1. **EVT-I1:** Insert the first event.
2. **EVT-I2:** Insert the webinar and summit using one multi-row statement.
3. **EVT-I3:** Insert the UI workshop with all column values explicitly supplied.
4. **EVT-I4:** Insert the Python bootcamp.
5. Insert an additional event with a registration fee of `999.99`.

## C. UPDATE Exercises

1. **EVT-U1:** Increase the summit capacity to `750`.
2. **EVT-U2:** Change `EVT-UI-04` status from `PLANNED` to `OPEN`.
3. **EVT-U3:** Increase the registration fee of every paid offline event by `10.00%`.
4. **EVT-U4:** Reschedule both dates of `EVT-CLOUD-02` one day later.
5. **EVT-U5:** Change the start time of `EVT-JAVA-01` to `10:00:00`.
6. **EVT-U6:** Update the event's `created_at` value for one selected event.

---

# 7. Organisation Device Register

**Suggested table:** `devices`

## Scenario

An organisation needs one table for its technology assets, purchase information, warranty, assignment, and maintenance schedule.

## Column Requirements

| Column | Data type | Description |
|---|---|---|
| `device_id` | `INT` | Numeric row number |
| `asset_tag` | `VARCHAR(20)` | Asset identifier |
| `serial_number` | `VARCHAR(50)` | Serial number |
| `device_name` | `VARCHAR(120)` | Device name |
| `device_type` | `VARCHAR(20)` | LAPTOP, DESKTOP, TABLET, ROUTER |
| `manufacturer` | `VARCHAR(80)` | Manufacturer |
| `model` | `VARCHAR(100)` | Model name |
| `purchase_date` | `DATE` | Purchase date |
| `purchase_price` | `DECIMAL(12,2)` | Purchase price |
| `warranty_expiry` | `DATE` | Warranty expiry date |
| `last_maintenance_at` | `DATETIME` | Last maintenance date and time |
| `maintenance_cost` | `DECIMAL(10,2)` | Maintenance cost |
| `device_status` | `VARCHAR(20)` | ASSIGNED, AVAILABLE, REPAIR, RETIRED |
| `created_at` | `DATETIME` | Record creation date and time |

## A. CREATE Exercises

1. **DEV-C1:** Create `devices` using the specified data types and no constraints.
2. Inspect the table structure using `DESCRIBE`.
3. Verify the table definition using `SHOW CREATE TABLE`.

## B. INSERT Exercises

| Asset tag | Serial number | Name | Type | Manufacturer | Model | Purchased | Price | Warranty expiry | Maintenance at | Maintenance cost | Status |
|---|---|---|---|---|---|---|---:|---|---|---:|---|
| AST-LAP-001 | SN-LAP-260001 | Developer Laptop | LAPTOP | Lenovo | ThinkPad E14 | 2026-01-15 | 78000.50 | 2029-01-14 | 2026-10-10 10:30:00 | 1500.00 | ASSIGNED |
| AST-DES-002 | SN-DES-260002 | Lab Desktop | DESKTOP | Dell | OptiPlex 7010 | 2025-08-10 | 62000.00 | 2028-08-09 | 2026-09-15 11:00:00 | 900.50 | AVAILABLE |
| AST-TAB-003 | SN-TAB-260003 | Demo Tablet | TABLET | Samsung | Galaxy Tab S9 | 2026-03-05 | 68000.75 | 2028-03-04 | 2026-10-20 12:00:00 | 500.00 | AVAILABLE |
| AST-RTR-004 | SN-RTR-260004 | Office Router | ROUTER | Cisco | RV340 | 2024-06-20 | 28000.00 | 2027-06-19 | 2026-11-01 09:15:00 | 2500.75 | REPAIR |
| AST-PHN-005 | SN-PHN-260005 | Retired Phone | PHONE | Nokia | Test Model | 2020-01-10 | 8000.00 | 2021-01-09 | 2025-12-10 14:00:00 | 300.00 | RETIRED |

1. **DEV-I1:** Insert the laptop.
2. **DEV-I2:** Insert the desktop and tablet using one multi-row statement.
3. **DEV-I3:** Insert the remaining two devices.
4. Insert another device with a purchase price containing decimal values.
5. Insert a device with a maintenance cost of `0.00`.

## C. UPDATE Exercises

1. **DEV-U1:** Assign `AST-DES-002` to `Rohan Das` by adding an `assigned_to` column only if you included it in your table design. Alternatively, use the existing device status to mark it as `ASSIGNED`.
2. **DEV-U2:** Change `AST-RTR-004` from `REPAIR` to `AVAILABLE`.
3. **DEV-U3:** Extend the laptop warranty to `2030-01-14`.
4. **DEV-U4:** Increase the recorded purchase price of every tablet by `3.00%`.
5. **DEV-U5:** Update the maintenance datetime of `AST-TAB-003`.
6. **DEV-U6:** Change the maintenance cost of `AST-RTR-004` to `1750.50`.

---

# 8. Restaurant Directory

**Suggested table:** `restaurants`

## Scenario

A dining directory needs one table containing restaurant identity, contact information, seating capacity, average cost, rating, and operating hours.

## Column Requirements

| Column | Data type | Description |
|---|---|---|
| `restaurant_id` | `INT` | Numeric row number |
| `restaurant_code` | `VARCHAR(12)` | Restaurant identifier |
| `restaurant_name` | `VARCHAR(120)` | Restaurant name |
| `cuisine_type` | `VARCHAR(80)` | Cuisine |
| `city` | `VARCHAR(80)` | City |
| `phone` | `VARCHAR(15)` | Contact number |
| `seating_capacity` | `INT` | Number of seats |
| `average_cost_for_two` | `DECIMAL(10,2)` | Average cost for two |
| `rating` | `DECIMAL(3,2)` | Restaurant rating |
| `opening_time` | `TIME` | Opening time |
| `closing_time` | `TIME` | Closing time |
| `opened_date` | `DATE` | Date opened |
| `last_review_at` | `DATETIME` | Latest review date and time |
| `opening_status` | `VARCHAR(25)` | OPEN, CLOSED |

## A. CREATE Exercises

1. **RES-C1:** Create `restaurants` using the specified data types and no constraints.
2. Inspect the structure using `DESCRIBE`.
3. Verify the definition using `SHOW CREATE TABLE`.

## B. INSERT Exercises

| Code | Name | Cuisine | City | Phone | Seats | Cost for two | Rating | Opens | Closes | Opened date |
|---|---|---|---|---|---:|---:|---:|---|---|---|
| RES-BLR-001 | Spice Courtyard | Indian | Bengaluru | 9876601001 | 80 | 1200.50 | 4.40 | 11:00:00 | 23:00:00 | 2018-06-15 |
| RES-CHE-002 | Green Banana Leaf | South Indian | Chennai | 9876601002 | 60 | 700.75 | 4.60 | 08:00:00 | 22:00:00 | 2020-02-10 |
| RES-MUM-003 | Coastal Plate | Seafood | Mumbai | 9876601003 | 100 | 1800.00 | 4.20 | 12:00:00 | 23:30:00 | 2017-09-21 |
| RES-HYD-004 | Urban Bowl | Fusion | Hyderabad | 9876601004 | 45 | 950.50 | 4.00 | 10:00:00 | 22:30:00 | 2026-01-12 |
| RES-PUN-005 | The Coffee Table | Cafe | Pune | 9876601005 | 35 | 450.25 | 4.30 | 07:00:00 | 21:00:00 | 2022-05-01 |

1. **RES-I1:** Insert the first restaurant.
2. **RES-I2:** Insert the next two restaurants using one multi-row statement.
3. **RES-I3:** Insert `RES-HYD-004` with all column values explicitly supplied.
4. **RES-I4:** Insert the Pune restaurant.
5. Insert another restaurant with a rating of `3.85`.

## C. UPDATE Exercises

1. **RES-U1:** Change the rating of `RES-BLR-001` to `4.55`.
2. **RES-U2:** Increase average cost by `10.00%` for restaurants in Mumbai.
3. **RES-U3:** Change `RES-HYD-004` rating to `4.25`.
4. **RES-U4:** Change the opening time of every open restaurant to `10:00:00`.
5. **RES-U5:** Update the last review datetime of `RES-CHE-002`.
6. **RES-U6:** Increase seating capacity by `10` for restaurants with fewer than `60` seats.

---

# 9. Insurance Policy Register

**Suggested table:** `insurance_policies`

## Scenario

A fictional training system needs one simplified table for policyholder, coverage, premium, policy term, payment schedule, and policy status.

## Column Requirements

| Column | Data type | Description |
|---|---|---|
| `policy_id` | `INT` | Numeric row number |
| `policy_number` | `VARCHAR(14)` | Policy identifier |
| `policyholder_name` | `VARCHAR(120)` | Policyholder name |
| `policy_type` | `VARCHAR(20)` | HEALTH, VEHICLE, LIFE, TRAVEL |
| `coverage_amount` | `DECIMAL(14,2)` | Coverage amount |
| `premium_amount` | `DECIMAL(10,2)` | Premium amount |
| `start_date` | `DATE` | Policy start date |
| `end_date` | `DATE` | Policy end date |
| `payment_frequency` | `VARCHAR(20)` | MONTHLY, QUARTERLY, ANNUAL |
| `payment_time` | `TIME` | Scheduled payment time |
| `last_payment_at` | `DATETIME` | Last payment date and time |
| `nominee_name` | `VARCHAR(120)` | Nominee name |
| `policy_status` | `VARCHAR(20)` | ACTIVE, EXPIRED, CANCELLED |
| `created_at` | `DATETIME` | Record creation date and time |

## A. CREATE Exercises

1. **POL-C1:** Create `insurance_policies` using the specified data types and no constraints.
2. Inspect the structure using `DESCRIBE`.
3. Verify the table definition using `SHOW CREATE TABLE`.

## B. INSERT Exercises

All policy information below is fictional.

| Policy number | Holder | Type | Coverage | Premium | Start | End | Frequency | Payment time | Last payment | Nominee | Status |
|---|---|---|---:|---:|---|---|---|---|---|---|---|
| POL00000000001 | Aditi Rao | HEALTH | 1000000.00 | 18000.50 | 2026-01-01 | 2026-12-31 | ANNUAL | 09:00:00 | 2026-01-01 09:05:00 | Rohan Rao | ACTIVE |
| POL00000000002 | Dev Kapoor | VEHICLE | 800000.00 | 22000.75 | 2026-04-15 | 2027-04-14 | QUARTERLY | 10:00:00 | 2026-10-15 10:15:00 | NULL | ACTIVE |
| POL00000000003 | Meera Nair | LIFE | 5000000.00 | 36000.00 | 2026-06-01 | 2046-05-31 | ANNUAL | 11:00:00 | 2026-06-01 11:05:00 | Arun Nair | ACTIVE |
| POL00000000004 | Kabir Shah | TRAVEL | 500000.00 | 4500.50 | 2026-10-01 | 2026-10-31 | MONTHLY | 08:30:00 | 2026-10-01 08:35:00 | NULL | ACTIVE |
| POL00000000005 | Sara Das | HOME | 2000000.00 | 15000.25 | 2025-01-01 | 2025-12-31 | ANNUAL | 12:00:00 | 2025-01-01 12:05:00 | NULL | CANCELLED |

1. **POL-I1:** Insert the health and vehicle policies.
2. **POL-I2:** Insert the life policy.
3. **POL-I3:** Insert the remaining two policies.
4. Insert another fictional policy with a premium containing decimal values.
5. Insert a policy with a payment time of `15:30:00`.

## C. UPDATE Exercises

1. **POL-U1:** Increase the coverage of `POL00000000001` to `1250000.00`.
2. **POL-U2:** Add nominee `Sara Kapoor` to `POL00000000002`.
3. **POL-U3:** Increase premiums of active vehicle policies by `5.00%`.
4. **POL-U4:** Change `POL00000000004` payment frequency to `ANNUAL`.
5. **POL-U5:** Update the last payment datetime of `POL00000000003`.
6. **POL-U6:** Change the end date of `POL00000000002` to `2027-05-14`.

---

# 10. Job Posting Board

**Suggested table:** `job_postings`

## Scenario

A recruitment portal needs one independent table for job descriptions, location, employment type, salary range, vacancies, application dates, and interview schedule.

## Column Requirements

| Column | Data type | Description |
|---|---|---|
| `job_id` | `INT` | Numeric row number |
| `job_code` | `VARCHAR(15)` | Job identifier |
| `job_title` | `VARCHAR(150)` | Job title |
| `department` | `VARCHAR(100)` | Department |
| `location` | `VARCHAR(100)` | Job location |
| `employment_type` | `VARCHAR(20)` | FULL_TIME, CONTRACT, INTERNSHIP |
| `minimum_salary` | `DECIMAL(12,2)` | Minimum annual salary |
| `maximum_salary` | `DECIMAL(12,2)` | Maximum annual salary |
| `vacancies` | `INT` | Number of vacancies |
| `posted_date` | `DATE` | Posting date |
| `closing_date` | `DATE` | Application closing date |
| `interview_start_time` | `TIME` | Interview starting time |
| `interview_end_time` | `TIME` | Interview ending time |
| `last_updated_at` | `DATETIME` | Last update date and time |
| `job_status` | `VARCHAR(20)` | OPEN, DRAFT, CLOSED, CANCELLED |

## A. CREATE Exercises

1. **JOB-C1:** Create `job_postings` using the specified data types and no constraints.
2. Inspect the structure using `DESCRIBE`.
3. Verify the definition using `SHOW CREATE TABLE`.

## B. INSERT Exercises

| Job code | Title | Department | Location | Type | Minimum salary | Maximum salary | Vacancies | Posted | Closing | Interview start | Interview end | Status |
|---|---|---|---|---|---:|---:|---:|---|---|---|---|---|
| JOB-JAVA-001 | Java Developer | Engineering | Bengaluru | FULL_TIME | 700000.00 | 1200000.00 | 3 | 2026-11-01 | 2026-12-01 | 10:00:00 | 12:00:00 | OPEN |
| JOB-QA-002 | QA Automation Engineer | Quality Assurance | Hyderabad | CONTRACT | 600000.50 | 900000.00 | 2 | 2026-11-02 | 2026-11-25 | 14:00:00 | 16:00:00 | OPEN |
| JOB-INT-003 | Software Intern | Engineering | Chennai | INTERNSHIP | 180000.00 | 240000.00 | 5 | 2026-11-03 | 2026-11-20 | 09:00:00 | 11:00:00 | OPEN |
| JOB-HR-004 | HR Coordinator | Human Resources | Mumbai | PART_TIME | 300000.00 | 450000.75 | 1 | 2026-11-04 | 2026-11-28 | 11:00:00 | 13:00:00 | DRAFT |
| JOB-OLD-005 | Cancelled Test Role | Training | Pune | FULL_TIME | 250000.00 | 350000.00 | 1 | 2026-10-01 | 2026-10-15 | 15:00:00 | 17:00:00 | CANCELLED |

1. **JOB-I1:** Insert the Java and QA positions.
2. **JOB-I2:** Insert the internship with all column values explicitly supplied.
3. **JOB-I3:** Insert the remaining positions.
4. Insert an additional job with salary values containing decimal places.
5. Insert a job with an interview schedule from `09:30:00` to `11:30:00`.

## C. UPDATE Exercises

1. **JOB-U1:** Increase the maximum salary of `JOB-JAVA-001` to `1300000.00`.
2. **JOB-U2:** Increase vacancies for `JOB-QA-002` from `2` to `4`.
3. **JOB-U3:** Change `JOB-HR-004` from `DRAFT` to `OPEN`.
4. **JOB-U4:** Increase both salary limits of every open engineering job by `8.00%`.
5. **JOB-U5:** Change the closing date of `JOB-INT-003` to `2026-11-30`.
6. **JOB-U6:** Change the interview timings of `JOB-JAVA-001` to `14:00:00`–`16:00:00`.
7. **JOB-U7:** Update the `last_updated_at` value of one selected job.

---

# Submission Checklist

- [ ] All 10 tables were created successfully.
- [ ] Every column uses only the six specified data types.
- [ ] No constraints or automatic value-generation rules were defined.
- [ ] `INT` columns were used for whole-number values.
- [ ] `DECIMAL` columns were used for fractional numeric values.
- [ ] `VARCHAR` columns were used for text.
- [ ] `DATE` columns were used for dates.
- [ ] `TIME` columns were used for times.
- [ ] `DATETIME` columns were used for combined date and time values.
- [ ] Single-row inserts were completed.
- [ ] Multi-row inserts were completed.
- [ ] Decimal values were inserted and updated.
- [ ] Date, time, and datetime values were inserted and updated.
- [ ] Single-row updates were completed.
- [ ] Multi-row updates were completed using carefully reviewed conditions.
- [ ] Every delete contains a precise `WHERE` clause.
- [ ] Final table contents were verified.

---
