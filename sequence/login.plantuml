@startuml SignIn_sequence
!pragma teoz true

actor User as user 

box "Front-end" #LightBlue
    boundary Tela as app
    participant Client as client
end box 

box "Back-end" #LightGreen
    box "Authentication_Server"
        boundary AuthApi  as auth_api 
    end box 
    box "Resource_Server"
        boundary ResourceApi  as resource_api 
    end box 
end box 

database Database as DB

user -> app: login
app -> client: login 
ref over client, auth_api : Authentication_Sequence
client -> resource_api: get user request 
resource_api -> auth_api: token validade request
return
ref over resource_api, DB : User_fetch_Sequence
@enduml

@startuml Authentication_sequence
!pragma teoz true
box "Front-end" #LightBlue
    participant Client as client
end box 
box "Back-end" #LightGreen
    box "Authentication_Server"
        boundary AuthApi  as auth_api 
    end box 

end box

database Database as DB
activate client
client -> auth_api: solicita token de acesso
activate auth_api
auth_api -> DB : consulta usuario 
activate DB
return  retorno da consulta 
    auth_api --> client: [user == null] notFound
    [<- client :
    auth_api --> client: [auth = false ] error
    [<- client :
    auth_api --> client: token de acesso 
    deactivate auth_api
    [<- client :
    
@enduml
