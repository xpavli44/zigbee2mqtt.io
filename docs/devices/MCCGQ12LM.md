---
title: "Xiaomi MCCGQ12LM control via MQTT"
description: "Integrate your Xiaomi MCCGQ12LM via Zigbee2MQTT with whatever smart home
 infrastructure you are using without the vendors bridge or gateway."
---

*To contribute to this page, edit the following
[file](https://github.com/Koenkk/zigbee2mqtt.io/blob/master/docs/devices/MCCGQ12LM.md)*

# Xiaomi MCCGQ12LM

| Model | MCCGQ12LM  |
| Vendor  | Xiaomi  |
| Description | Aqara T1 door & window contact sensor |
| Exposes | contact, battery, voltage, linkquality |
| Picture | ![Xiaomi MCCGQ12LM](../images/devices/MCCGQ12LM.jpg) |

## Notes


### Pairing
Press and hold the reset button on the device for +- 5 seconds (until the blue light starts blinking).
After this the device will automatically join, but the interview process may not finish.
If that happens, keep doing short presses to the reset button to keep the light flashing, until the interview process finishes successfully.

### Recommendation
If the contact is being made via a horizontal slide (e.g. the sensor is placed at the top of a sliding door), the sensor may provide three or more messages with conflicting states. To get around this issue, consider using the `debounce` option in your device specific configuration.

E.g. (devices.yaml)

{% raw %}
```yaml
'0xabc457fffe679xyz':
    friendly_name: my_sensor
    debounce: 1
```
{% endraw %}



## Exposes

### Contact (binary)
Indicates if the contact is closed (= true) or open (= false).
Value can be found in the published state on the `contact` property.
It's not possible to read (`/get`) or write (`/set`) this value.
If value equals `false` contact is ON, if `true` OFF.

### Battery (numeric)
Remaining battery in %.
Value can be found in the published state on the `battery` property.
It's not possible to read (`/get`) or write (`/set`) this value.
The minimal value is `0` and the maximum value is `100`.
The unit of this value is `%`.

### Voltage (numeric)
Voltage of the battery in millivolts.
Value can be found in the published state on the `voltage` property.
It's not possible to read (`/get`) or write (`/set`) this value.
The unit of this value is `mV`.

### Linkquality (numeric)
Link quality (signal strength).
Value can be found in the published state on the `linkquality` property.
It's not possible to read (`/get`) or write (`/set`) this value.
The minimal value is `0` and the maximum value is `255`.
The unit of this value is `lqi`.
