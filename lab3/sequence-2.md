Запит на бронювання вільних апартаментів
```plantuml
@startuml

actor Guest as guest

guest -> API : booking apartment

activate API
API -> DB : getApartment
activate DB
DB --> API : apartment
deactivate DB

opt apartment is available
API -> DB : createBooking
activate DB 
DB --> API : booking 
deactivate DB
alt apartment requires confirmation
API ->> Celery : sendEmail
activate Celery
API --> guest : booking is created
Celery -> guest : sendEmail
deactivate Celery
else apartment doesn't require confirmation
API --> guest : booking is created
end
end
deactivate API

@enduml
```