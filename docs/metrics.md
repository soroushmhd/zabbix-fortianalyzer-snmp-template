# Metrics

The template monitors Fortinet FortiAnalyzer appliances through SNMP using numeric OIDs.

## System monitoring

| Item | Key |
|---|---|
| System name | `faz.system.name` |
| System object ID | `faz.system.object_id` |
| Serial number | `faz.system.serial` |
| Firmware version | `faz.system.firmware` |
| Uptime | `faz.system.uptime` |
| CPU utilization | `faz.system.cpu.util` |
| CPU utilization excluding nice processes | `faz.system.cpu.util.excluding_nice` |
| Memory total | `faz.system.memory.total` |
| Memory used | `faz.system.memory.used` |
| Memory utilization | `faz.system.memory.util` |

## Log processing

| Item | Key |
|---|---|
| Log receiving rate | `faz.log.rate` |
| Log receiving rate average | `faz.log.rate.average` |
| Log indexing rate | `faz.log.indexing.rate` |
| Log indexing lag | `faz.log.indexing.lag` |
| Log volume received today | `faz.log.volume.today` |
| Log volume received yesterday | `faz.log.volume.yesterday` |
| Log volume daily average over seven days | `faz.log.volume.week.average` |

## ADOM summary

| Item | Key |
|---|---|
| ADOM enabled state | `faz.adom.enabled` |
| Number of administrative domains | `faz.adom.count` |
| Maximum number of administrative domains | `faz.adom.max` |

## Managed resource summary

| Item | Key |
|---|---|
| Total managed devices | `faz.device.count` |
| Total managed VDOMs | `faz.vdom.count` |

## High availability

| Item | Key |
|---|---|
| HA mode | `faz.ha.mode` |
| HA cluster ID | `faz.ha.cluster.id` |
| HA peer count | `faz.ha.peer.count` |

HA metrics have been validated on a standalone appliance. HA peer discovery and trigger behavior have not been validated against an active FortiAnalyzer HA cluster.

## Discovery rules

| Discovery rule | Key |
|---|---|
| ADOM discovery | `faz.adom.discovery` |
| Managed device discovery | `faz.device.discovery` |
| FortiAnalyzer disk I/O discovery | `faz.disk.io.discovery` |
| Storage discovery | `faz.storage.discovery` |

## ADOM discovery

ADOMs without managed devices are excluded by the default discovery filter.

| Item prototype | Key |
|---|---|
| Analytics quota | `faz.adom.analytics.quota[{#SNMPINDEX}]` |
| Analytics retention | `faz.adom.analytics.retention[{#SNMPINDEX}]` |
| Analytics used space | `faz.adom.analytics.used[{#SNMPINDEX}]` |
| Analytics utilization | `faz.adom.analytics.utilization[{#SNMPINDEX}]` |
| Archive quota | `faz.adom.archive.quota[{#SNMPINDEX}]` |
| Archive retention | `faz.adom.archive.retention[{#SNMPINDEX}]` |
| Archive used space | `faz.adom.archive.used[{#SNMPINDEX}]` |
| Archive utilization | `faz.adom.archive.utilization[{#SNMPINDEX}]` |
| Managed devices | `faz.adom.devices[{#SNMPINDEX}]` |
| Log receiving rate | `faz.adom.log.rate[{#SNMPINDEX}]` |
| Log volume received today | `faz.adom.log.volume.today[{#SNMPINDEX}]` |
| Log volume received yesterday | `faz.adom.log.volume.yesterday[{#SNMPINDEX}]` |
| Weekly average log volume | `faz.adom.log.volume.weekly.avg[{#SNMPINDEX}]` |
| Operation mode | `faz.adom.mode[{#SNMPINDEX}]` |
| Policy packages | `faz.adom.policy.packages[{#SNMPINDEX}]` |
| State | `faz.adom.state[{#SNMPINDEX}]` |

## Managed device discovery

| Item prototype | Key |
|---|---|
| Assigned ADOM | `faz.device.adom[{#SNMPINDEX}]` |
| Archive log used space | `faz.device.archive.used[{#SNMPINDEX}]` |
| Configuration state | `faz.device.configuration.state[{#SNMPINDEX}]` |
| Connection state | `faz.device.connection.state[{#SNMPINDEX}]` |
| Database state | `faz.device.database.state[{#SNMPINDEX}]` |
| HA group | `faz.device.ha.group[{#SNMPINDEX}]` |
| HA mode | `faz.device.ha.mode[{#SNMPINDEX}]` |
| Management IP address | `faz.device.ip[{#SNMPINDEX}]` |
| One-hour log rate average | `faz.device.log.rate.hour[{#SNMPINDEX}]` |
| One-day log rate average | `faz.device.log.rate.day[{#SNMPINDEX}]` |
| Seven-day log rate average | `faz.device.log.rate.week[{#SNMPINDEX}]` |
| Model | `faz.device.model[{#SNMPINDEX}]` |
| Operating system build | `faz.device.os.build[{#SNMPINDEX}]` |
| Operating system minor release | `faz.device.os.release[{#SNMPINDEX}]` |
| Operating system major version | `faz.device.os.version[{#SNMPINDEX}]` |
| Serial number | `faz.device.serial[{#SNMPINDEX}]` |
| Support state | `faz.device.support.state[{#SNMPINDEX}]` |
| VDOM state | `faz.device.vdom.enabled[{#SNMPINDEX}]` |

## Storage discovery

The default discovery filter includes:

- `Compact Flash Disk`
- `Internal Hard Disk`

Physical memory and swap entries are excluded.

| Item prototype | Key |
|---|---|
| Allocation unit | `faz.storage.allocation_unit[{#SNMPINDEX}]` |
| Total allocation units | `faz.storage.size.units[{#SNMPINDEX}]` |
| Used allocation units | `faz.storage.used.units[{#SNMPINDEX}]` |
| Total space | `faz.storage.total[{#SNMPINDEX}]` |
| Used space | `faz.storage.used[{#SNMPINDEX}]` |
| Storage utilization | `faz.storage.util[{#SNMPINDEX}]` |

## Disk I/O discovery

| Item prototype | Key |
|---|---|
| Disk I/O utilization | `faz.disk.io.util[{#SNMPINDEX}]` |