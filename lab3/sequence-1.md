Підтвердження бронювання протягом 3 годин
```plantuml
@startuml

actor Guest as guest
activate API

guest -> API : confirmBooking
API -> DB : request booking data
DB --> API : send booking data

alt confirmation time is valid
API --> guest : send invoce
guest -> WFP : pay
WFP -> API : send transaction result
alt transaction status is approved
API -> DB : confirmBooking
end
API --> WFP : acceptTransaction

else confirmation time is expired
API --> guest : inform confirmation time is expired

end
deactivate API
@enduml
```