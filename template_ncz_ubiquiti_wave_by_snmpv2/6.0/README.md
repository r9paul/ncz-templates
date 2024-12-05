# NCZ Ubiquiti Wave by SNMPv2
## Overview
Template for monitoring Ubiquiti Wave 5/60GHz Wireless Equipment

Tested with Zabbix 6.0, Ubiquiti Wave-AP and Wave-Nano

## Zabbix configuration

Generally its considered only to monitor the "Base" or "Main" end of the link, as this will monitor all stations automatically.

## Items collected

- GPS, tilt and roll
- Network interfaces status and traffic
- Device memory and CPU usage
- Radio statistics including Channel, SSID etc.
- Station statistics including traffic rate, link capacity, link SNR etc.

## Known issues

We only seem to be able to monitor the 'active' link, there's no reporting of the backup link unless it actually fails over to the backup link.

## Author and Credits

[Paul Nicholls](https://github.com/r9paul/ncz-templates)