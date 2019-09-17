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
 
Customizing
-----------

- For using other profiles and configurations, change the paths of them.

```yaml

  device-modbus:
    image: device-modbus
    ports:
      - "49999:49999"
    container_name: edgex-device-modbus
    hostname: edgex-device-modbus
    networks:
      edgex-network:
        aliases:
            - edgex-device-modbus
    volumes:
      - db-data:/data/db
      - log-data:/edgex/logs
      - consul-config:/consul/config
      - consul-data:/consul/data
      - ./configuration.toml:/res/docker/configuration.toml
      - ./modbus.test.device.profile.yml:/res/docker/modbus.test.device.profile.yml
    depends_on:
      - data
      - command
```

It's necessary to modified the last two rows in volumes section. 
 

 
 
