@startuml Envio_de_email
participant sendEmailService as sendEmail
participant emailRepository as email_R
database Database as DB
boundary SmptServer as smtp

?-> sendEmail : sendEmail()
activate sendEmail
    sendEmail -> smtp : solicitação de envio de email
    activate smtp
        smtp --> sendEmail : email enviado 
    deactivate smtp
    sendEmail -> email_R : salvar codigo de verificação
    activate email_R
        email_R -> DB : salva codigo de verificação 
        activate DB
            DB --> email_R:
        deactivate DB
        email_R --> sendEmail:
    deactivate email_R
deactivate sendEmail
@enduml

