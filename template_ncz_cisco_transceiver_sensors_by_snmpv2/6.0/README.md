# NCZ Cisco Transceiver Sensors by SNMPv2
## Overview
Template for monitoring transceiver sensors and status in Cisco IOS network devices using ENTITY-MIB and CISCO-ENTITY-SENSOR

Tested with Zabbix 6.0, assorted Cisco Catalyst switches IOS 12.2, 15.0, 15.2 IOSXE 17.3

## Zabbix configuration

Where possible, the template will extract thresholds for each sensor using **entSensorThresholds**, however this is not supported on all platforms (for example [CSCvn58055](https://bst.cloudapps.cisco.com/bugsearch/bug/CSCvn58055) ), where threshold values can't be obtained seperate triggers will fire using preset thresholds stored in Macros. You may need to adjust these to suit your individual transceivers. 

## Items collected

- Transmit and Receive Power (dBm)
- Bias Current (A)
- Voltage (V)
- Temperature (°C)
- Threshold values for sensors where available
- Transciever Model and Serial numbers where available
- Transciever Link Status (used to mute alerts for down interfaces)

## Known issues

Obviously sensor values will only be shown from transceivers with capable DOM modules. If the values show up in `show interface transceiver` then they should be obtainable from the **entSensorValues** table.

**entSensorPrecison** is required to interpret values obtained from the **entSensorValues** table, I have implemented this for Voltage and Temperature sensors where I have found the precision to vary across platforms, but not for Bias Current or TX/RX power as so far these appear to have consistent precision. You will note a raw value is obtained, as well as the precison factor before using them to calculate the real sensor value in V or °C.

For Voltage and Temperature, the threshold values, where they are obtained need to be adjusted by **entSensorPrecision** before they are compared to a sensor value, as they are stored in the raw format as obtained from the device. 


## Author and Credits

[Paul Nicholls](https://github.com/r9paul/ncz-templates)