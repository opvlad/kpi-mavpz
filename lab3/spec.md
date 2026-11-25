# Sequence diagram for UC 3 Create Booking


## UC 3 Create Booking Scenarios

- Підтвердження бронювання протягом 3 годин
- Створення запиту на бронювання вільних апартаментів
- Спроба забронювати апартаменти на зайняті дати


## Participants
- Guest
- API
- Database
- WayForPay
- Celery


## Out of scope
- Celery worker that removes bookings not confirmed within 3 hours


## Acceptance criteria
- All scenarios have their own diagrams
- Every diagram has opt/alt/loop/par
- Every synchronus call has response

