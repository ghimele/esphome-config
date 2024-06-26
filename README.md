# Ghimele's ESPHome configuration

![Project Maintenance][maintenance-shield]
[![License][license-shield]](LICENSE)

[![GitHub Actions][actions-shield]][actionci]
[![GitHub Activity][commits-shield]][commits]
[![GitHub Last Commit][last-commit-shield]][commits]

![ESPHome Logo](https://esphome.io/_images/logo-text.png)


This repository contains the various configuration files I use for the various ESPHome devices I have and use around my home.

# Devices
I have a number of ESPHome devices around my Smart Home and I've to provide a description and readme for each of these devices to share how I built the device and what I use it for. I also use these readme to document any special components I've used with the device and any specific build steps I followed.

| Device | Description | Config files | Readme |
|--------|-------------|--------------|--------|
| Refoss P11 | Refoss P11 Power Monitoring Plug |[epp-plg01.yaml](/epp-plg01.yaml)<br>[epp-plg02.yaml](/epp-plg01.yaml)| [Refoss P11 readme](docs/Refoss_P11.md)|
| MOES MS-105 | MOES MS-105 Smart Dimmer |[epp-dmr01.yaml](/epp-dmr01.yaml)| [MOES MS-105 readme](docs/Moes_MS-105.md)|
| Crono | Custom Crono Thermostat that runs the heaters on my house  |[epp-crn01.yaml](/epp-crn01.yaml)| [Crono readme](docs/Crono.md)|

# Splitting up the ESPHome configuration

A pattern I have seen used by a others in the community which makes an ESPHome config much more readable is to split out common components to their own .yaml files. 

I took inspiration from this repository [jcallaghan ESPHome Configs](https://github.com/jcallaghan/esphome-config/tree/main)

```
|-- ESPHome-Config
    |-- .build (local directory not pushed to this repo)
    |-- .esphome (local directory not push to this repo)
    |-- assets (storage for images used in my configs)
    |-- boards (definitions for each board type)
    |   |-- .esphome.yaml
    |   |-- board_definition.yaml
    |-- components (used to organised yaml files)
    |   |-- binary_sensors
    |   |-- buttons
    |   |-- common (used with both ESP32 and ESP8266 boards)   
    |   |-- common_esp32 (used just for ESP32 board)
    |   |-- debug
    |   |-- dusplay (collect all the display devices used in my projects)
    |   |-- fonts (used within the display devices)
    |   |-- sensors
    |   |-- switches
    |   |-- text_sensors
    |   |-- time
    |-- devices (device definitions)
    |   |-- ESPC3_Relay_X1.yaml
    |   |-- Refoss_P11_PMP.yaml
    |-- docs (collection of readme for each device configured)
    |-- .gitignore
    |-- esph_device_configuration_1.yaml (definition for each ESP board I run ESPHome on)
    |-- esph_device_configuration_2.yaml
    |-- esph_device_configuration_3.yaml
    |-- readme.md (this readme)
    |-- secrets.yaml (where passwords and other secrets are stored and not pushed to this repo)
```

# References 
* [jcallaghan ESPHome Configs](https://github.com/jcallaghan/esphome-config/tree/main)

* [frenck home-assistant-config](https://github.com/frenck/home-assistant-config)


[actionci]: https://github.com/ghimele/esphome-config/actions/workflows/ESPHomeCI.yaml
[commits]: https://github.com/ghimele/esphome-config/commits/main

[maintenance-shield]: https://img.shields.io/maintenance/yes/2024?style=flat-square
[license-shield]: https://img.shields.io/github/license/ghimele/esphome-config?style=flat-square

[actions-shield]: https://img.shields.io/github/actions/workflow/status/ghimele/esphome-config/ESPHomeCI.yaml?style=flat-square&logo=github&label=EXPHome%20CI
[last-commit-shield]: https://img.shields.io/github/last-commit/ghimele/esphome-config?style=flat-square
[commits-shield]: https://img.shields.io/github/commit-activity/m/ghimele/esphome-config?style=flat-square