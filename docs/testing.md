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

## Current status

The current items and discovery rules have been tested against the environment listed above.

Triggers are intentionally excluded until operational thresholds and baselines are validated.

HA peer discovery requires additional testing against an active FortiAnalyzer HA cluster.