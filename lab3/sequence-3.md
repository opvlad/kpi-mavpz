Запит на бронювання зайнятих апартаментів
```plantuml
@startuml

actor Guest as guest
activate API
activate DB


guest -> API : bookingApartments
API -> DB : checkApartmentsAvailiable
DB --> API : apartments data

alt apartments are occupied
alt booking status is confirmed
API --> guest : apartments are occupied
else booking status is pending
API --> guest : apartments are occupied + offer notice about vacating
end
end


deactivate API
deactivate DB
@enduml
```