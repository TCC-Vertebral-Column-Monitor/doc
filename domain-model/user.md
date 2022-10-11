@startuml
left to right direction 

User "1" *-- "1" UserSettings
User "1" -- "*"  Training 
Role "1" *-- "*" Permission 
User "*" *-- "*" Role 
Training --> ObjetiveTraining
class User{
    String name
    String email
    String password
    Date createdAt
    Date birthDate 
  }

class Role {
    String name
    String description
  }

class Permission{
    string name 
    string description 
  }

class UserSettings{
    int dorsalNormalAngle   
    int cervucalNortmalAngle
    Intensity intensity
    boolean notify
    boolean notifyVibrate
    int vibrateIntensity
    duration objectiveTargetTime
  }
class Training{
    period period 
    Intensity intensity
  }
class ObjetiveTraining{
    period period 
    Intensity intensity
    boolean sucess
    duration  targetTime 
  }

class Intensity{
    LOW
    MEDIUM
    HIGHT
  }
@enduml

