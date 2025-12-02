# wazuh-qlik

Wazuh decoder and rules that integrate Qlik Sense audit events.

![screenshot of Qlik Security Audit events in Wazuh](/doc/qlik%20screenshot.png)

This integration reads the [Qlik Security Audit Events](https://help.qlik.com/en-US/sense-admin/November2025/Subsystems/DeployAdministerQSE/Content/Sense_DeployAdminister/QSEoW/Deploy_QSEoW/Server-Logging-New-Log-File-Format-Fields-Audit-Security-Log.htm) logfile.

Limitations:
* the `@timestamp` of events is the moment of injection, not the moment of the event, which is stored in `data.qlik.timestamp`

## Installation:
* [install decoder and rules](/doc/install-step-1.md)


## Attribution
This contribution was originally developed by [bzhkem](https://github.com/bzhkem) and uploaded with his permission.

