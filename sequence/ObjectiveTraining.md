@startuml
actor User as user 
participant App as app
participant ColumnMonitor as monitor
participant Server as server 

user --> app : iniciar treino com objetivo 
app --> monitor: iniciar treino com configurações do objetivo 
loop objetiveTimeTarget 
 monitor --> monitor : verifica leituras 
 else falha 
    monitor --> app: evento de falha 
  else finish error handling
    app --> server: treinamento 
end 

@enduml
