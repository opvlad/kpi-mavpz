# Specification: Booking ERD


## Goal
Create entity relationship diagram for booking apartment system.


## Data requirements

### Users
- id: int, PK,
- first_name: varchar(50), required
- last_name: varchar(100), required
- email: varchar(100), required, unique
- password_hash: varchar(100), required
- registered_at: timestamp, required

### Apartments
- id: int, PK
- owner_id: int, FK
- title: varchar(50), required
- description: text, required
- price_per_night: decimal, required
- max_guests: int, required
- address: varchar(100), required
- status: enum("active", "inactive"), required

### Bookings
- id: int, PK
- guest_id: int, FK
- apartment_id: int, FK
- check_in_date: date, required
- check_out_date: date, required
- total_price: decimal, required
- status: enum("pending", "confirmed", "cancelled"), required


## Relationships
- A user makes 0 or many bookings, each booking has 1 user
- A user owns 0 or many apartments, each apartment has 1 user
- A booking has 1 apartment, each apartment has 0 or many bookings


## Acceptance criteria
- Tables correspond 3NF
- All relationships show cardinality
