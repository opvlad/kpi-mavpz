Запит на бронювання вільних апартаментів
```plantuml
@startuml

actor Guest as guest
activate API


guest -> API : bookingApartment
API -> DB : requestApartmentData
DB --> API : apartmentData

alt apartment is availiable
API -> DB : createBooking

alt apartment requires confirmation
API ->> Celery : sendEmail
API --> guest : booking is created
Celery -> guest : sendEmail
else apartment does't require confirmation
API --> guest : booking is created
end
end


deactivate API
@enduml
```