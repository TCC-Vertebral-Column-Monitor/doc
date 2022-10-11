@startuml
left to right direction
skinparam actorStyle awesome

:User: as user
user -- (L)
user -- (R)
(L) .r-> (R) : extend
(L) .-> (CE) : extend 
(R) .-> (CE) : include  

usecase "Login" as (L)
usecase "Registration" as (R)
usecase "Confirm email" as (CE)
@enduml

