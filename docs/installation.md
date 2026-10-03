# Zabbix FortiAnalyzer SNMP Template

[![Zabbix](https://img.shields.io/badge/Zabbix-7.0-D40000?logo=zabbix&logoColor=white)](https://www.zabbix.com/)
[![FortiAnalyzer](https://img.shields.io/badge/FortiAnalyzer-v7.6.7-EE3124?logo=fortinet&logoColor=white)](https://www.fortinet.com/products/management/fortianalyzer)
[![SNMP](https://img.shields.io/badge/SNMP-v3-0A466A)](https://datatracker.ietf.org/doc/html/rfc3414)
[![License](https://img.shields.io/badge/License-MIT-2E7D32.svg)](LICENSE)

A Zabbix template for monitoring Fortinet FortiAnalyzer appliances through SNMP.

The template uses numeric OIDs, so Fortinet MIB files are not required on the Zabbix server or proxy.

## Tested environment

| Component | Version or configuration |
|---|---|
| Zabbix Server | 7.0.31 |
| FortiAnalyzer platform | VM64 |
| FortiAnalyzer version | v7.6.7 build 3737 |
| SNMP version | SNMPv3 |
| Security level | `authPriv` |
| Authentication protocol | SHA |
| Privacy protocol | AES |
| OID format | Numeric |

## Features

### System monitoring

- System name, object ID, serial number, and firmware
- System uptime
- CPU utilization
- Memory capacity, usage, and utilization

### Log processing

- Log receiving and indexing rates
- Log indexing lag
- Daily and seven-day log volume statistics

### Low-level discovery

The template uses SNMP low-level discovery for:

- ADOMs
- Managed devices
- Storage resources
- FortiAnalyzer disks

Discovered metrics include ADOM log storage, managed device identity and state, storage capacity and utilization, and disk I/O utilization.

ADOMs without managed devices are excluded by default. Storage discovery includes `Compact Flash Disk` and `Internal Hard Disk` while excluding memory and swap entries.

### High availability

The following HA metrics are collected:

- HA mode
- HA cluster ID
- HA peer count

HA peer discovery is not included because it has not been validated against an active FortiAnalyzer HA cluster.

### Triggers and graphs

The template includes configurable triggers for:

- CPU and memory utilization
- Storage and disk I/O utilization
- ADOM archive and analytics utilization
- Log indexing lag
- SNMP availability
- FortiAnalyzer restart
- Managed device connection and configuration state
- HA peer availability

Warning thresholds depend on their corresponding critical thresholds to prevent duplicate problems.

Graphs are included for system resources, log processing, log volume, ADOM utilization, storage utilization, and disk I/O.

## Dashboard

![FortiAnalyzer overview dashboard](screenshots/dashboard.png)

## Requirements

- Zabbix 7.0 or later
- FortiAnalyzer with SNMP enabled
- Network connectivity from the Zabbix server or proxy
- An SNMP interface configured on the Zabbix host

SNMP credentials and environment-specific addresses are not stored in the template.

## Installation

1. Download:

   ```text
   templates/template_fortianalyzer_snmp.yaml
   ```

2. In the Zabbix frontend, open:

   ```text
   Data collection → Templates → Import
   ```

3. Select the YAML file and complete the import.
4. Create or open the FortiAnalyzer host.
5. Add and configure an SNMP interface.
6. Link the `FortiAnalyzer by SNMP` template to the host.
7. Wait for the first polling and discovery cycles.
8. Review the results under **Monitoring → Latest data**.

## Configuration

The tested SNMP configuration is:

```text
Security level: authPriv
Authentication protocol: SHA
Privacy protocol: AES
```

Trigger thresholds can be customized through the template macros.

SNMP credentials must be configured on the host interface and must not be stored in the template or committed to the repository.

## Known limitations

- Currently validated only against FortiAnalyzer VM64 v7.6.7 build 3737.
- HA behavior has not been validated against an active FortiAnalyzer HA cluster.
- Hardware-specific sensors are not included because testing was performed on a virtual appliance.

## Documentation

| Document | Description |
|---|---|
| [Metrics reference](docs/metrics.md) | Monitored resources and discovery rules |
| [Testing notes](docs/testing.md) | Tested environment and known limitations |
| `screenshots/` | Dashboard and monitoring screenshots |
| `templates/` | Importable Zabbix template files |

## License

This project is licensed under the [MIT License](LICENSE).

## Author

**Soroush Mehmandoust**

- GitHub: [soroushmhd](https://github.com/soroushmhd)