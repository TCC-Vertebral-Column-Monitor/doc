@startuml SignUp_sequence
!pragma teoz true
actor User as user 
box "Front-end" #LightBlue
    boundary App as app
    participant Client as client
end box 
box "Back-end" #LightGreen
    box "Resource_Server"
        boundary ResourceApi  as resource_api   
    end box 
end box 
database Database as DB
user -> app : formulario de cadastro 
app -> client : dados cadastrais 
client -> resource_api: solicitação de \n cadastro  de usuario 
ref over resource_api, DB:  cadastro-back-end
alt sucess 
    resource_api --> client: UserRegisteredMessage
    client --> app: confirmar email 
    app --> user : confirmar email 
else error  
    resource_api --> client: problemDetails
    client --> app : erro
    app --> user: erro
end
@enduml

