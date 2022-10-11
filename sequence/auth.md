@startuml Authentication_sequence
!pragma teoz true
actor User as user
box "Front-end" #LightBlue
    participant Client as client
end box 
box "Back-end" #LightGreen
    box "Authentication_Server"
        boundary AuthApi  as auth_api 
    end box 

end box

database Database as DB
 --> client  
activate client
client -> auth_api: /authorize?cliendid,callbackURI
activate auth_api
auth_api --> client : redirect /login
client --> user: redirect /login
user -> auth_api : login form
alt sucesso 
  auth_api -> DB : consulta usuario 
  activate DB
  DB --> auth_api : 
  auth_api -> auth_api: autentica usuário 
  auth_api --> client: /callbackURI?authorization-code
  client --> auth_api: /oauth2/token : authorization-code
  auth_api --> auth_api: validate authorization-code
 auth_api --> client: [user == null] notFound
    [<- client :
    auth_api --> client: [auth = false ] error
    [<- client :
    auth_api --> client: token
    deactivate auth_api
    [<- client :   
else erro
  auth_api --> user : redirect /login?error
end 
    
@enduml
