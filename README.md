# Zabbix FortiAnalyzer SNMP Template

[![Zabbix](https://img.shields.io/badge/Zabbix-7.0-D40000?logo=zabbix&logoColor=white)](https://www.zabbix.com/)
[![FortiAnalyzer](https://img.shields.io/badge/FortiAnalyzer-v7.6.7-EE3124?logo=fortinet&logoColor=white)](https://www.fortinet.com/products/management/fortianalyzer)
[![SNMP](https://img.shields.io/badge/SNMP-v3-0A466A)](https://datatracker.ietf.org/doc/html/rfc3414)
[![Security](https://img.shields.io/badge/Security-authPriv-0275B8)](https://datatracker.ietf.org/doc/html/rfc3414)
[![License](https://img.shields.io/badge/License-MIT-2E7D32.svg)](LICENSE)

A Zabbix template for monitoring Fortinet FortiAnalyzer appliances through SNMP.

The template uses numeric OIDs, so Fortinet MIB files are not required on the Zabbix server or proxy.

## Official community release

This template has been accepted into the official Zabbix Community Templates repository:

- [FortiAnalyzer by SNMP for Zabbix 7.0](https://github.com/zabbix/community-templates/tree/main/Network_Devices/Fortigate/template_fortianalyzer_by_snmp/7.0)

- [Merged pull request #849](https://github.com/zabbix/community-templates/pull/849)

## Tested environment

| Component | Version or configuration |
|---|---|
| Zabbix Server | 7.0.31 |
| FortiAnalyzer platform | VM64 |
| FortiAnalyzer version | v7.6.7 build 3737 |
| SNMP version | SNMPv3 |
| Security level | `authPriv` |
| Authentication protocol | SHA1 |
| Privacy protocol | AES128 |
| OID format | Numeric |
| Fortinet MIB required | No |

## Monitored metrics

### System monitoring

| Item | Key |
|---|---|
| System name | `faz.system.name` |
| System object ID | `faz.system.object_id` |
| Serial number | `faz.system.serial` |
| Firmware version | `faz.system.firmware` |
| Uptime | `faz.system.uptime` |
| CPU utilization | `faz.system.cpu.util` |
| Memory total | `faz.system.memory.total` |
| Memory used | `faz.system.memory.used` |
| Memory utilization | `faz.system.memory.util` |

### Log processing

| Item | Key |
|---|---|
| Log receiving rate | `faz.log.rate` |
| Log receiving rate average | `faz.log.rate.average` |
| Log indexing rate | `faz.log.indexing.rate` |
| Log indexing lag | `faz.log.indexing.lag` |
| Log volume received today | `faz.log.volume.today` |
| Log volume received yesterday | `faz.log.volume.yesterday` |
| Daily average log volume over seven days | `faz.log.volume.week.average` |

### ADOM summary

| Item | Key |
|---|---|
| ADOM enabled state | `faz.adom.enabled` |
| Configured domain count | `faz.adom.count` |
| Maximum supported domains | `faz.adom.max` |

### Managed resource summary

| Item | Key |
|---|---|
| Total managed devices | `faz.device.count` |
| Total managed VDOMs | `faz.vdom.count` |

### High availability

| Item | Key |
|---|---|
| HA mode | `faz.ha.mode` |
| HA cluster identifier | `faz.ha.cluster.id` |
| HA peer count | `faz.ha.peer.count` |

HA scalar metrics have been validated on a standalone FortiAnalyzer appliance. HA peer discovery and HA-related trigger behavior have not been validated against an active FortiAnalyzer HA cluster.

## Low-level discovery

| Discovery rule | Key | Default interval |
|---|---|---:|
| ADOM discovery | `faz.adom.discovery` | 1h |
| Managed device discovery | `faz.device.discovery` | 1h |
| FortiAnalyzer disk I/O discovery | `faz.disk.io.discovery` | 1h |
| Storage discovery | `faz.storage.discovery` | 1h |

### ADOM discovery

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

### Managed device discovery

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

### Storage discovery

The default discovery filter includes FortiAnalyzer disk resources and excludes memory-related entries.

| Included resources | Excluded resources |
|---|---|
| `Compact Flash Disk` | `Physical Memory` |
| `Internal Hard Disk` | `Swap Memory` |

| Item prototype | Key |
|---|---|
| Allocation unit | `faz.storage.allocation_unit[{#SNMPINDEX}]` |
| Total allocation units | `faz.storage.size.units[{#SNMPINDEX}]` |
| Used allocation units | `faz.storage.used.units[{#SNMPINDEX}]` |
| Total space | `faz.storage.total[{#SNMPINDEX}]` |
| Used space | `faz.storage.used[{#SNMPINDEX}]` |
| Storage utilization | `faz.storage.util[{#SNMPINDEX}]` |

### Disk I/O discovery

| Item prototype | Key |
|---|---|
| Disk I/O utilization | `faz.disk.io.util[{#SNMPINDEX}]` |

## Triggers

| Category | Included triggers |
|---|---|
| CPU | High and critically high CPU utilization |
| Memory | High and critically high memory utilization |
| Storage | High and critically high storage utilization |
| Disk I/O | High and critically high disk I/O utilization |
| ADOM archive | High and critically high archive utilization |
| ADOM analytics | High and critically high analytics utilization |
| Log indexing | High and critically high indexing lag |
| Availability | SNMP data collection failure and restart detection |
| Managed devices | Connection failure and configuration synchronization failure |
| High availability | HA enabled without an available peer |

Trigger thresholds can be customized through template macros. Warning triggers depend on their corresponding critical triggers to prevent duplicate problems.

## Template macros

| Macro | Default | Description |
|---|---:|---|
| `{$FAZ.ADOM.LOG.UTIL.WARN}` | 80 | Warning threshold for ADOM archive and analytics log utilization, in percent |
| `{$FAZ.ADOM.LOG.UTIL.CRIT}` | 90 | Critical threshold for ADOM archive and analytics log utilization, in percent |
| `{$FAZ.CPU.UTIL.WARN}` | 80 | Warning threshold for CPU utilization, in percent |
| `{$FAZ.CPU.UTIL.CRIT}` | 90 | Critical threshold for CPU utilization, in percent |
| `{$FAZ.DISK.IO.UTIL.WARN}` | 80 | Warning threshold for disk I/O utilization, in percent |
| `{$FAZ.DISK.IO.UTIL.CRIT}` | 90 | Critical threshold for disk I/O utilization, in percent |
| `{$FAZ.DISK.UTIL.WARN}` | 80 | Warning threshold for storage utilization, in percent |
| `{$FAZ.DISK.UTIL.CRIT}` | 90 | Critical threshold for storage utilization, in percent |
| `{$FAZ.LOG.INDEXING.LAG.WARN}` | 300 | Warning threshold for log indexing lag, in seconds |
| `{$FAZ.LOG.INDEXING.LAG.CRIT}` | 900 | Critical threshold for log indexing lag, in seconds |
| `{$FAZ.MEMORY.UTIL.WARN}` | 80 | Warning threshold for memory utilization, in percent |
| `{$FAZ.MEMORY.UTIL.CRIT}` | 90 | Critical threshold for memory utilization, in percent |
| `{$FAZ.SNMP.NODATA.TIME}` | 10m | Maximum interval without SNMP data before an availability problem is generated |

## Graphs

| Graph | Scope |
|---|---|
| System resource utilization | CPU and memory utilization |
| Log processing rates | Log receiving and indexing rates |
| Log indexing performance | Log indexing lag |
| Log volume | Current and historical log volume |
| ADOM log utilization | Archive and analytics utilization per ADOM |
| Storage utilization | Utilization per discovered storage resource |
| Disk I/O utilization | I/O utilization per discovered disk |

## Dashboard

The template includes a dashboard providing a consolidated view of system resources, log processing, ADOMs, managed devices, HA status, and active problems.

![FortiAnalyzer overview dashboard](screenshots/dashboard.png)

## Requirements

| Requirement | Details |
|---|---|
| Zabbix | Version 7.0 or later |
| FortiAnalyzer | SNMP must be enabled |
| Connectivity | The Zabbix server or proxy must be able to reach the FortiAnalyzer SNMP interface |
| Host configuration | An SNMP interface must be configured on the Zabbix host |
| Credentials | SNMPv2c or SNMPv3 credentials supported by the target FortiAnalyzer configuration |

The tested environment uses SNMPv3 with `authPriv`. The template does not contain SNMP credentials, community strings, management addresses, or other environment-specific values.

## Recommended SNMPv3 credential configuration

To keep SNMPv3 credentials outside the template, define them as host-level macros on each FortiAnalyzer host.

Open the host, select **Macros**, and create the following macros:

| Host macro | Type | Value |
|---|---|---|
| `{$SECURITY_NAME}` | Text | SNMPv3 security name |
| `{$AUTH_PASSPHRASE}` | Secret text | SNMPv3 authentication passphrase |
| `{$PRIVACY_PASSPHRASE}` | Secret text | SNMPv3 privacy passphrase |

The authentication and privacy passphrases should be stored as **Secret text**. Do not define these credentials in the template or commit their values to a repository.

![FortiAnalyzer host SNMPv3 macros](screenshots/snmp_setup1.png)

Configure the host SNMP interface with the following values:

| SNMP interface field | Value |
|---|---|
| SNMP version | SNMPv3 |
| Security name | `{$SECURITY_NAME}` |
| Security level | `authPriv` |
| Authentication protocol | SHA1 |
| Authentication passphrase | `{$AUTH_PASSPHRASE}` |
| Privacy protocol | AES128 |
| Privacy passphrase | `{$PRIVACY_PASSPHRASE}` |

![FortiAnalyzer host SNMPv3 interface](screenshots/snmp_setup2.png)

This approach allows the same template to be linked to multiple FortiAnalyzer hosts while each host keeps its own SNMPv3 identity and secrets.

## Installation

1. Download [`templates/template_fortianalyzer_by_snmp.yaml`](templates/template_fortianalyzer_by_snmp.yaml).
2. In the Zabbix frontend, open **Data collection → Templates**.
3. Select **Import**, choose the YAML file, and complete the import.
4. Create or open the FortiAnalyzer host.
5. Add an SNMP interface using the FortiAnalyzer management address.
6. Configure the required SNMP credentials on the host interface.
7. Link the `FortiAnalyzer by SNMP` template to the host.
8. Wait for the initial polling and low-level discovery cycles.
9. Review the results under **Monitoring → Latest data**.

SNMP credentials must be configured on the host interface and must never be stored inside the template export or committed to the repository.

## Testing and validation

| Validated area | Status |
|---|---|
| SNMP data collection | Validated |
| System CPU and memory monitoring | Validated |
| FortiAnalyzer log processing metrics | Validated |
| ADOM discovery | Validated |
| Managed device discovery | Validated |
| Storage discovery | Validated |
| FortiAnalyzer disk I/O discovery | Validated |
| Calculated memory and storage metrics | Validated |
| Value mappings | Validated |
| Trigger expressions and dependencies | Validated |
| Graphs and graph prototypes | Validated |
| Dashboard widgets | Validated |
| Active FortiAnalyzer HA cluster | Not yet validated |

## Known limitations

| Limitation | Details |
|---|---|
| Tested FortiAnalyzer version | Currently validated only against FortiAnalyzer VM64 v7.6.7 build 3737 |
| HA validation | HA-related trigger behavior has not been validated against an active HA cluster |
| HA discovery | HA peer discovery is not currently included |
| Hardware sensors | Hardware-specific sensors are not included because testing was performed on a virtual appliance |

## Repository contents

| Path | Description |
|---|---|
| [Screenshots](screenshots/) | Dashboard and monitoring screenshots |
| [Templates](templates/) | Importable Zabbix template files |

## License

This project is licensed under the [MIT License](LICENSE).

## Author

**Soroush Mehmandoust**

- GitHub: [soroushmhd](https://github.com/soroushmhd)