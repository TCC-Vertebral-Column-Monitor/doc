@startuml
left to right direction
skinparam actorStyle awesome
:User: --> (calibration)
(calibration) .. (login): extends 
"start calibration" as (calibration)
"login" as (login)
@enduml
