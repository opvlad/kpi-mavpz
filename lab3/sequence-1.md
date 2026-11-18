Підтвердження бронювання протягом 3 годин
```plantuml
@startuml

actor Guest as guest

guest -> API : confirmBooking

activate API
API -> DB : request booking data
DB --> API : send booking data
alt confirmation time is valid
API --> guest : send invoce
else confirmation time is expired
API --> guest : inform confirmation time is expired
end
deactivate API

opt confirmation time is valid
guest -> WFP : pay
WFP -> API : send transaction result
activate API
opt transaction status is approved
API -> DB : confirmBooking
API ->> Celery : sendEmail
Celery -> guest : sendEmail
end
API --> WFP : acceptTransaction
deactivate API
end

@enduml
```