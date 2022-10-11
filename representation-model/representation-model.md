@startuml
left to right direction 


class registerRequest{
    String name
    String email
    String password
  }

class UserSummary{
    Long id
    String name
    String email
    String password
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

class TrainingRequest{
    timestamp startdate 
    boolean objective
  }

class TrainingResponse{
    Period period 
    Intensity intensity
    duration targetTime
    boolean sucess
  }

class Intensity{
    LOW
    MEDIUM
    HIGHT
  }
@enduml
