Steps to follow to flash multiple ESP32 with the same .bin file and be auto discovered and adopted by ESPHome - and then Home Assistant - as unique devices.
The devices can be discovered and adopted straight into Home Assistant without being adopted necessarily in ESPHome.
The purpose of having them in ESPHome as well though is to be able to Update them once in a while whenever new ESPHome/Home Assistant changes occur and deal with performance issues or even deprecate things.

There are 4 main files:
Secrets (to be used as a template for your your own secrets file inside ESPHome)
Factory YAML file (Which you create the .bin file with)
Main YAML file (Which will automatically be embedded within your discovered device in ESPHome)
Remote_package YAML file (Where you have all the details of all your sensors)
