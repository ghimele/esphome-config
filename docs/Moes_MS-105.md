# ESPHome MOES MS-105 Dimmer

![MOES MS-105 Dimmer](../assets/MOES-MS-105.png)

This device is a Tuya MCU Dimmer, I was able to flash via OTA using the [tuya-cloudcutter](https://github.com/tuya-cloudcutter/tuya-cloudcutter)

When you initially connect the device to the power it will go in EZ Mode, you wil ear a fast bip. To put the device in AP mode you need to connect a switch button like the image below and push it for 10 times, the bip will be slowly.

![Wire Connection](<../assets/MOES-MS-105-Dimmer WireConnection.png>)

> [!IMPORTANT]
> If CloudCutter pauses after a device requests DHCP information, the device is having issues with your wireless network, or the timing of its availability. Please [check this](https://github.com/tuya-cloudcutter/tuya-cloudcutter/wiki/FAQ#my-device-gets-stuck-after-dhcp-what-can-i-do)


this is the basic configuration I've used

```Yaml
esphome:
  name: ms-105-dimmer
  friendly_name: ms-105-dimmer

bk72xx:
  board: generic-bk7231n-qfn32-tuya

# Enable logging
logger:

web_server:

captive_portal:

# Enable Home Assistant API
api:

ota:

wifi:
  ssid: !secret WIFI_SSID
  password: !secret WIFI_PASSWORD

  # Enable fallback hotspot (captive portal) in case wifi connection fails
  ap:
    ssid: "Test Fallback Hotspot"
    password: "ELinxoUtPqYC"

sensor:
  - platform: uptime
    name: Uptime

text_sensor:
  - platform: libretiny
    version:
      name: LibreTiny Version

uart:
  rx_pin: RX1
  tx_pin: TX1
  baud_rate: 9600

tuya:
  # DPIDs processed from schema model: 0000004lra

# switch:
#   - platform: tuya
#     switch_datapoint: 1
#     name: Led Switch

number:
  # - platform: tuya
  #   number_datapoint: 2
  #   name: Bright Value
  #   min_value: 10
  #   max_value: 1000
  #   step: 1
  - platform: tuya
    number_datapoint: 3
    name: Brightness Min
    min_value: 10
    max_value: 1000
    step: 1
  - platform: tuya
    number_datapoint: 6
    name: Countdown
    min_value: 0
    max_value: 86400
    step: 1

select:
  - platform: tuya
    enum_datapoint: 4
    name: Led Type
    optimistic: true
    options:
      0: Led
      1: Incandescent
      2: Halogen

light:
  - platform: tuya
    name: "dim1"
    dimmer_datapoint: 2
    min_value_datapoint: 3
    switch_datapoint: 1
    max_value: 1000
    min_value: 10
```


## References
[tuya-cloudcutter with esphome bk7231 how toguide](https://digiblur.com/2023/08/19/updated-tuya-cloudcutter-with-esphome-bk7231-how-to-guide)

[How To Install ESPHome on Tuya Beken BK7231 w/ ltchiptool](https://www.youtube.com/watch?v=t0o8nMbqOSA)

[Device gets stuck after dhcp](https://github.com/tuya-cloudcutter/tuya-cloudcutter/wiki/FAQ#my-device-gets-stuck-after-dhcp-what-can-i-do)
