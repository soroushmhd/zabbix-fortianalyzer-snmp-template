# Testing

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

## Validated functionality

The following functionality has been validated against the tested environment:

- SNMP data collection
- System CPU and memory monitoring
- FortiAnalyzer log processing metrics
- ADOM discovery
- Managed device discovery
- Storage discovery
- FortiAnalyzer disk I/O discovery
- Calculated memory and storage utilization
- Dashboard widgets
- Graphs and graph prototypes
- Trigger expressions and dependencies

## Known limitations

- HA peer discovery is not included.
- HA-related trigger behavior has not been validated against an active FortiAnalyzer HA cluster.
- Hardware-specific sensors are not included because testing was performed on a FortiAnalyzer VM64 appliance.
- The template has currently been validated only against FortiAnalyzer v7.6.7 build 3737.