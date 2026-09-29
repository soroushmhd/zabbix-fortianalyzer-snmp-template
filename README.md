# Zabbix FortiAnalyzer SNMP Template

A modern Zabbix template for monitoring Fortinet FortiAnalyzer appliances through SNMP.

The template uses numeric OIDs, so installing Fortinet MIB files on the Zabbix server is not required.


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
| Fortinet MIB required | No |

## Features

The template currently provides monitoring for the following areas.

### System monitoring

- System name
- System object identifier
- System uptime
- Firmware version
- CPU utilization
- Memory capacity
- Memory usage
- Memory utilization
- Disk capacity
- Disk usage
- Device uptime

### FortiAnalyzer log processing

- Log receiving rate
- Average log receiving rate
- Log indexing rate
- Log indexing lag
- Log database usage
- Archive storage usage
- Analytics storage usage

### ADOM monitoring

Low-level discovery is used to detect and monitor administrative domains.

Collected ADOM information includes:

- ADOM name
- ADOM state
- ADOM operation mode
- Number of managed devices
- Number of policy packages
- Archive log usage
- Analytics log usage
- Log receiving statistics
- Log indexing statistics

ADOMs without managed devices can be excluded by the discovery filter.

### Managed device monitoring

Low-level discovery is used to identify Fortinet devices managed by FortiAnalyzer.

Collected device information includes:

- Device name
- Serial number
- Model
- Management IP address
- Assigned ADOM
- Operating system major version
- Operating system minor version
- Operating system build number
- Connection state
- Configuration state
- Database state
- Support contract state
- HA state
- VDOM state
- Number of VDOMs
- Log receiving rate
- Archive storage usage

### Storage monitoring

Storage resources are discovered dynamically using SNMP low-level discovery.

The template can monitor:

- Storage name
- Storage type
- Allocation unit
- Total capacity
- Used capacity
- Storage utilization percentage
- Vendor-specific disk I/O utilization

The discovery filters are designed to include FortiAnalyzer disk resources such as:

- `Compact Flash Disk`
- `Internal Hard Disk`

Memory and swap entries are excluded from disk discovery.

### High availability monitoring

The current template collects the following FortiAnalyzer HA information:

- HA mode
- HA cluster ID
- HA peer count

HA scalar metrics can be collected on both standalone and clustered appliances.

HA peer discovery is planned for a future update after validation against an active FortiAnalyzer HA environment.

## Requirements

- Zabbix 7.0 or later
- FortiAnalyzer with SNMP enabled
- Network connectivity from the Zabbix server or proxy to the FortiAnalyzer SNMP interface
- A configured SNMP interface on the Zabbix host

The template does not contain SNMP usernames, authentication passwords, privacy passwords, community strings, management addresses, or other environment-specific credentials.

## Installation

1. Download the following template file:

   ```text
   templates/template_fortianalyzer_snmp.yaml
   ```

2. Sign in to the Zabbix frontend.

3. Open:

   ```text
   Data collection → Templates
   ```

4. Select **Import**.

5. Select `template_fortianalyzer_snmp.yaml`.

6. Review the import options and complete the import.

7. Create or open the FortiAnalyzer host.

8. Add an SNMP interface using the FortiAnalyzer management address.

9. Configure the required SNMP credentials on the host interface.

10. Link the imported template to the FortiAnalyzer host.

11. Wait for the first polling and discovery cycles.

12. Review the collected values under:

    ```text
    Monitoring → Latest data
    ```

For additional information, see the [installation guide](docs/installation.md).

## SNMP configuration

The tested configuration uses SNMPv3 with the following security settings:

```text
Security level: authPriv
Authentication protocol: SHA
Privacy protocol: AES
```

SNMP credentials must be configured on the Zabbix host SNMP interface and must never be stored inside the template export or committed to the repository.

## Template design

This template follows these design principles:

- Numeric OIDs are used to avoid a runtime dependency on external MIB files.
- Low-level discovery is used for dynamic resources such as ADOMs, managed devices, and storage.
- Calculated items are used where percentage values must be derived from capacity and usage metrics.
- Environment-specific values and credentials are kept outside the exported template.
- Item keys are designed to remain unique and predictable.
- Discovery rules and item prototypes are separated by monitored resource type.
- Unsupported VM-specific hardware branches are not included without validation.
- Triggers are deferred until reliable baselines and thresholds have been established.


## Documentation

| Document | Description |
|---|---|
| [Installation guide](docs/installation.md) | Template import and host configuration |
| [Metrics reference](docs/metrics.md) | Items, discovery rules, prototypes, and OIDs |
| [Testing notes](docs/testing.md) | Tested versions, validation process, and known limitations |
| `screenshots/` | Zabbix configuration and monitoring screenshots |
| `templates/` | Importable Zabbix template files |



## License

This project is licensed under the [MIT License](LICENSE).

## Author

**Soroush Mehmandoust**

- GitHub: [soroushmhd](https://github.com/soroushmhd)