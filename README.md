# ajax-spacecontrol-esphome-ESP8266  
(full instruction for Node-Red + Mqtt)  
Ajax security managed by esphome esp8266 device  
Board used - Wemos D1 mini  

Highlight: Zones in SIA are not rooms, in Ajax app these are groupes for independent control.  

Made two variations for ESPhome: HA & mqtt, you can chose preffered.  

-> With HA yaml - device / instances will be discovered by HA and exposed as switches.  

-> With MQTT yaml - you will be able to connect to control topic in you mqtt broker.  
MQTT broker topic to subscibe for control: ajax/alarm  
Payloads: arm_ajax, disarm_ajax, night_ajax (you can change for yours especially if you have zones)  

_**For me I've stoped on Node-Red FULL implementation.**_  
We would need to install:  
1. node-red-contrib-sia-ultimate (+ configure in Ajax app hub settings SIA monitoring station)  
2. mosquitto broker (I used docker instalaltion on the localhost)
3. node-red-contrib-homekit-bridged (Alarm node in my flow already preconfigured withot extra "Home" state unsupported by Ajax)
4. Solder SpaceControl + use ESPhome mqtt.yaml example  
5. Use my Nodered_Ajax_alarm.flow as draft (it saves Alarm State on reboot and elimenates Alarm SecuritySystem loop)  

_**For PARTIAL "read Alarm status" implementation in HomeKit you DO NOT need soldering, ESP and so on:**_  
1. node-red-contrib-sia-ultimate (+ configure in Ajax app hub settings SIA monitoring station)  
3. node-red-contrib-homekit-bridged (Alarm node in my flow already preconfigured withot extra "Home" state unsupported by Ajax)
5. Use my Nodered_Ajax_alarm.flow as draft (it saves Alarm State on reboot and elimenates Alarm SecuritySystem loop),   
but delete all nodes after HomeKit node made for controll state.

My soldering images are in folder /soldering  
Using that schematics allows not to use the cell battery later and power up the SpaceControl vith 3,3V from the board powered by usb adapter.  
Soldering instructions used from **iesus** project.  
He used the v8 plate, i had the older one v6 - it is the same in schematics.  
Link to project with photos:  
https://bitbucket.org/iesus_sonesson/d1-ajax-mqtt/src/master/  

As i studied in process - for Wemos D1 mini it's safe to use for soldering: D1,D2,D5,D6,D7  
(they are not triggered at boot and can be input / otput). 

HA version based on the work of **akarpenkoua** with tiny changes (inverted state needed for correct work).  
https://github.com/akarpenkoua/ajax-spacecontrol-esphome  

MQTT version based on jb567 project with small changes and correction.  
https://community.home-assistant.io/t/ajax-alarm-system/62853/442    

My soldering images:  

<img src="/soldering/1.jpeg" width="400"/>
<img src="/soldering/2.jpeg" width="400"/>
<img src="/soldering/3.jpeg" width="400"/>
<img src="/soldering/4.jpeg" width="400"/>
<img src="/soldering/5.jpeg" width="400"/>
