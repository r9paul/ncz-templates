# NCZ Cisco Bridge Status by SNMPv2
## Overview
Template for monitoring Spanning Tree and Forwarding Database status in Cisco IOS network devices using BRIDGE-MIB and CISCO-STP-EXTENSIONS-MIB

Tested with Zabbix 6.0, assorted Cisco Catalyst switches IOS 12.2, 15.0, 15.2 IOSXE 17.3

## Zabbix configuration

BRIDGE-MIB is context aware, and uses [SNMP Community String Indexing](https://www.cisco.com/c/en/us/support/docs/ip/simple-network-management-protocol-snmp/40367-camsnmp40367.html) which means since Zabbix 5.4 now handles community strings at the host level, not the item level, we can only easily obtain data from one vlan on the switch, so if the switch has multiple spanning tree instances, we will only be able to obtain data for one of them.

By default, with no vlan id specified in the community string, this template will therefore only record data from vlan 1. Depending on your network configuration, you most likely want to obtain data for your management vlan, so if this isn't vlan 1, you will need to use the notation **{CommunityString}@{VlanID}** when setting the community string for this host (values from other MIBS will not be affected), you also need to adjust the **{$STP_VLANID}** macro as the Spanning Tree priority is offset by the vlan ID internally. 

## Items collected

- Spanning Tree Root Port (if zero then this switch is the root bridge)
- Spanning Tree Root Bridge (Identifier)
- Spanning Tree Configured Priority
- Spanning Tree Type 
- TP Forward Discards (Best indicator that the Forwarding Database is full)

## Known issues

On older Cisco Platforms I have seen BRIDGE-MIB not return any values unless a vlan ID is specified in the community string. Whilst this is not expected behaviour, if this occurs just add **@1** after your community string. 

Currently working on CAM table metrics, this is made difficult by the SNMP Community String Indexing. 


## Author and Credits

[Paul Nicholls](https://github.com/r9paul/ncz-templates)