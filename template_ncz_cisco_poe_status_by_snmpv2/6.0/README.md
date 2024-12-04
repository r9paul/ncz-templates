# NCZ Cisco PoE Status by SNMPv2
## Overview
Template for monitoring PoE and Power Sourcing Entities (PSE) on Cisco IOS network devices using POWER-ETHERNET-MIB and CISCO-POWER-ETHERNET-EXT

Tested with Zabbix 5.4, assorted Cisco Catalyst switches IOS 12.2, 15.0, 15.2 IOSXE 17.3

## Zabbix configuration

Where possible, the template configures a threshold alarm per PSE for PoE budget. This threshold is taken from the Device where possible using **pethMainPseUsageThreshold**, but on some platforms this doesn't appear to be implemented in which case we are using the macro **{$PSE_THRESHOLD_ALARM}** instead which can be tuned to suit.

## Items collected

We discover both Physical Ports, and Power Sourcing Entity (PSE) units - typically these are individual units in a stack or chassis with their own seperate power supply. This isn't the same as a single switch with multiple power supplies where they are internally linked anyway. 

- Power Max Capable, Current Allocation and Current (real) Usage per Physical Port (W)
- PoE Status and Device Detection per Physical Port
- Device Type connected by Physical Port
- Total Capable (Nominal), Current Allocation and Current (real) Usage per Power Sourcing Entity (PSE) (W)
- Total number of PD devices connected per Power Sourcing Entity (PSE)
- Total Capable (Nominal), Current Allocation and Current (real) Usage per Host (W)
- Total number of PD devices connected per Host

## Known issues

I'd love to be able to link the PoE ports back to the ifTable in order to compare against LinkStatus and so on, but the implementation of linking PoE ports back to the Entity table and then cross-referencing back to the ifTable seems to vary by platform.

## Author and Credits

[Paul Nicholls](https://github.com/r9paul/ncz-templates)