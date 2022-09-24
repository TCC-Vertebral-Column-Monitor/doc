
@startuml Handle_registration_email_event 
participant userService as user_s
entity userRegistrationEvent as userR_event
participant userRegistationListener as userR_listener
participant sendEmailService as sendEmail
participant emailRepository as email_R
database Database as DB
boundary SmptServer as smtp
        
activate user_s
    [-> user_s :
    user_s -> userR_event ** : create
    activate userR_event
     ?-> userR_listener : handle(event)
        activate userR_listener
            userR_listener -> userR_event: getUser()
            userR_event --> userR_listener
            userR_listener --> sendEmail: enviar email de confirmação 
        deactivate userR_listener
ref over sendEmail, smtp : envio de email 
deactivate userR_event
destroy userR_event
@enduml
