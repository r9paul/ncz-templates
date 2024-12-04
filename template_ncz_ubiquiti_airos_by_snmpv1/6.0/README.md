# NCZ Ubiquiti AirOS by SNMPv1
## Overview
Template for monitoring Ubiquiti 5GHz Wireless Link equipment. 

Tested with Zabbix 6.0, Ubiquiti aiMAX Lite AP GPS, airMAX NanoStation AP firmwares 8.7.12, 8.7.14

## Zabbix configuration

Generally its considered only to monitor the "Base" or "Main" end of the link, as this will monitor all stations automatically.

## Items collected

- GPS and Temperature Stats where supported by the device
- Network interfaces status and traffic
- Device memory and CPU usage
- Radio statistics including Channel, Noise Floor, Power Output etc
- Station statistics including traffic rate, link capacity, link quality etc.

## Known issues

I'd like be to able to capture a DFS wait as a specific trigger, but this doesn't seem to be supported. 

## Author and Credits

[Paul Nicholls](https://github.com/r9paul/ncz-templates)