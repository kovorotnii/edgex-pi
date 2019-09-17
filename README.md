## Running Edgex services on Raspberry PI 3B+

Components
----------
 - Basic Edgex services
 
 - Modbus service for communication with modbus-tcp devices
 
 - MQTT-connector, which allows you to establish communication with [Rightech IoT cloud sandbox](https://sandbox.rightech.io/)
 

Prerequisites
-------------
 - For better experience use 16 gb sd card.
  
 - Use Ubuntu 18.04 Server for arm64. Link: https://ubuntu.com/download/server/arm.
 
 - Install docker, docker-compose.
 
 - You can use modbus emulator. Link: http://modbuspal.sourceforge.net/.
 
 - The main instruction how to use these services are [there](https://github.com/kovorotniy/edgex-modbus-ric-tutorial).
 
 - Execute `docker pull kovorotniy/mqtt-connector-arm64:v1` for pulling mqtt-connector. Use it for establishing communication bentween cloud and modbus emulator.
 
 - Execute `docker pull kovorotniy/modbus-arm64:v2` for pulling modbus-service.
 
 - Finally, execute `docker-compose up -d` for launching all services. 
 
 - UI will be available at `your-ip:4000`, there you can monitor all devices and services.
 

 
 
