Steps to follow to flash multiple ESP32 with the same .bin file and be auto discovered and adopted by ESPHome - and then Home Assistant - as unique devices.
The devices can be discovered and adopted straight into Home Assistant without being adopted necessarily in ESPHome.
The purpose of having them in ESPHome as well though is to be able to Update them once in a while whenever new ESPHome/Home Assistant changes occur and deal with performance issues or even deprecate things.
I wanted to create a process with which the end user adding a sensor in ESPHome and Home Assistant, will not mess in any way with yaml and/or secrets files.
Just creat the bin, flash it and then the end user, will access the sensor with WIFI Access Point (ap:), add it in ESPHome and Home Assistant with autodiscovery.
Thats it. This way the system can also update the sensors. No messing with yaml for the end user whatsoever.
I have managed to accomplish it but... WITHOUT the use of API Encryption (key), OTA Password and WIFI credentials in secrets.

There are 3 main files:
Factory YAML file (Which you create the .bin file with)
Main YAML file (Which will automatically be embedded within your discovered device in ESPHome)
Remote_package YAML file (Where you have all the details of all your sensors)

**Steps to follow to flash the bin (Remember to change the folowing urls to YOUR urls):
**1. Fork this repository
2. Add a "New Device" in ESPHome
3. Select "New Device Setup"
4. Give it any name
5. Select your Device type (the current setup is for ESP32 - not variations)
6. Skip the Installation and "Edit" the yaml to include ONLY these 2 lines
```
packages:
  remote_package_shorthand: github://djgenesis/esp32-multisensor/factory.yaml@main
```
5. Click Install
6. Select "Plug into this Computer"
7. After the compilation of the bin file, download it and open https://web.esphome.io/?dashboard_install
8. Connect your device. here you might need to download and install some drivers.
9. Install the downloaded bin file. You might need to hold pressing a button of ESP32 for some seconds. If so do it before selecting Install and release after you see "Erasing". Wait until successfull installation.

**Steps to follow to add the device in ESPHome and Home Assistant (ie. End User):
**11. Connect to your ESP32 WIFI Access Point. No password needed
12. A portal to insert your WIFI credentials will open. These will permanently be stored in your ESP32s memory (Unless your reflash, erase etc your ESP32).
13. Head to ESPHome. After some seconds ESPHome should show it as "Discovered".
14. "Take Control" of the device.
15. Select "Update All" to test that updating also works. (Optional but suggested)
16. Head to HHome Assistant -> Settings - > Devices. You should see the sensor appear there as well.
17. Click "Add" and select and Area

**Congratulations! Thats it!**
