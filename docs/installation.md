# Installation

## Import the template

1. Download `templates/template_fortianalyzer_snmp.yaml`.
2. Open the Zabbix frontend.
3. Navigate to **Data collection → Templates**.
4. Select **Import**.
5. Select the template YAML file and complete the import.

## Configure the host

1. Create or open the FortiAnalyzer host.
2. Add an SNMP interface using the FortiAnalyzer management address.
3. Configure the required SNMP credentials on the host interface.
4. Link the `FortiAnalyzer by SNMP` template to the host.
5. Review the collected values under **Monitoring → Latest data**.

SNMP credentials must not be stored in the template.