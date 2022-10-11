@startuml
 User --> App : inicia calibração
 loop 10 segundos 
   PostureMonitor --> App : leitura 
   App -->  App : armazena leitura 
 end 
  App --> App : calcula  media 
  App --> Server: calibração
@enduml
