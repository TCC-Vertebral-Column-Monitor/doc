@startuml RegisterUserSequence 
!pragma teoz true
    box "Back-end" #LightGreen

        box "Resource_Server"
            boundary ResourceApi  as resource_api
            control userController as user_c
            participant userService as user_s
            participant userRepository as user_r
        end box 

    end box        
    database Database as DB
    resource_api -> user_c : registerUser(RegisterRequest) 
    user_c -> user_s : registerUser(UserEntity)
    user_s -> user_r: findByEmail(String) 
    user_r -> DB : consulta usuario pelo email
    return retorno da consulta
    user_r --> user_s : retorno da consulta
    alt  email disponivel 
        user_s -> user_r : save(userEntity)
        user_r --> DB : salva o usuario no banco 
        return usuario salvo
        user_r --> user_s: usuario salvo
        user_s --> user_c: usuario salvo 
        user_c --> resource_api: userRegisterdMessage  
    else email ja cadastrado  
    user_s --> user_c: erro 
    user_c --> resource_api: erro

end 
@enduml
