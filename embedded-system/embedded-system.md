@startuml
left to right direction 

IReadoutApi <|-- ReadoutApi
IReadoutApi <|-- BluetoothReadoutApi
ReadoutService *-- IReadoutApi
IReadoutService <|-- ReadoutService  
ReadoutNotificationProxy <|-left- IReadoutService  
ReadoutNotificationProxy "delegate "*--  ReadoutService
ReadoutNotificationProxy *-right- vibrator
ASensorService "1..3"*-- Sensor
ASensorService -left- SensorsOutput
ISensorOutputMapper -left- Readout
ISensorOutputMapper -- SensorsOutput
ConfigSingleton *-up- IConfigApi
IConfigApi <|-up- ConfigApi
IConfigApi <|-up- BluetoothReadoutApiConfigApi
App *-right- IReadoutService 
App *-- ASensorService
App *-- ISensorOutputMapper
App -left- Readout
App *-up- ConfigSingleton
interface IReadoutApi{
}

class App {
    void setup()
    void loop()
  }
class ReadoutApi{

}

class BluetoothReadoutApi{

}

interface IReadoutService{

}

class ReadoutService{

  }

abstract ASensorService{
  }
interface ISensorOutputMapper{

}

class ReadoutNotificationProxy{

}
interface IConfigApi{

}

class ConfigSingleton{

}

class Readout{
    int dorsalAngle
    int cervicalAngle
  }

class Sensor{
    int pin
  }
class SensorsOutput{
    int dorsalOutput
    int cervicalOutput
  }
class vibrator{
    int pin
  }
@enduml

