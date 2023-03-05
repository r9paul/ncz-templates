# NCZ Ruckus SmartZone by SNMPv2
## Overview
Template for monitoring Ruckus SmartZone Wireless Controller 

Tested with Zabbix 5.4, Ruckus SmartZone vSZ-H 5.2, 6.1

## Zabbix configuration

If running a cluster of controllers, each controller will respond with all data for the entire cluter, so you may wish to only monitor a single member, or mute alerts on other cluster members to avoid multiple trigger alerts for the same problem. 

## Items collected

- Overall WLAN Traffic Stats as bps/pps
- Device, and Cluster Node status and system information
- Overall access points and clients connected
- Clients and access points connected by Zone
- Clients and access points connected by Domain
- Per Access Point status, clients connected and system information
- Per WLAN Traffic Stats (bps) and clients connected

## Known issues

This is a work in progress, and does not feature many triggers. In particular due to my own prefered method of also monitoring access points individually (in order to obtain better per-radio stats).

**{#APZONE} - {#APNAME}** is used as a key for naming items and graphs, therefore Access Points should be set to have unique names within each zone to avoid missing data. 

The per-Domain stats do not understand Domain heirarchy, and work only the basis of the immediate parent Domain of a Zone.

## Author and Credits

[Paul Nicholls](https://github.com/r9paul/ncz-templates)