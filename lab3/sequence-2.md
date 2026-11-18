Запит на бронювання вільних апартаментів
```plantuml
@startuml

actor Guest as guest

guest -> API : bookingApartment

activate API
API -> DB : requestApartmentData
activate DB
DB --> API : apartmentData
deactivate DB

opt apartment is availiable
API -> DB : createBooking
activate DB 
DB --> API : booking data 
deactivate DB
alt apartment requires confirmation
API ->> Celery : sendEmail
activate Celery
API --> guest : booking is created
Celery -> guest : sendEmail
deactivate Celery
else apartment does't require confirmation
API --> guest : booking is created
end
end
deactivate API

@enduml
```