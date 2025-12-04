# add decoder
Events are only generated if they are covered by a decoder. Go to the decoder configuration and create a new decoder file `0600-qlik_decoders.xml`and fill with the contents of [/rules/0600-qlik_decoders.xml](/rules/0600-qlik_decoders.xml)

# add rules
Events only generate alerts if they are matched by a rule. Go to the rules configuration and create a new rules file `0660-qlik_rules.xml` and fill it with the contents of [/rules/0645-qlik_rules.xml](/rules/0645-qlik_rules.xml).

Restart the server for the changes to take effect, for example using the `Restart cluster` button in the `Server Management` > `Status` menu.

# change agent ossec.conf
Add the logfile configuration to the `C:\Program Files (x86)\ossec-agent\ossec.conf` of the agent running on the Qlik Sense server, to ensure that the logfile is analyzed by Wazuh.

```
<localfile>
  <log_format>syslog</log_format>
  <location>C:\ProgramData\Qlik\Sense\Log\Repository\Audit\XXXXXXX_AuditSecurity_Repository.txt</location>
  <only-future-events>yes</only-future-events>
</localfile>
```

> [!NOTE]  
> The above is an example; do not forget to adapt the path name to your installation.


Restart the agent for the changes to take effect.

## using CMD
```
NET STOP WazuhSvc
NET START WazuhSvc
```

## using Powershell
```
Restart-Service WazuhSvc
```
 

You should start seeing new events show up in the Threat hunting module. You can filter for `decoder.name: qlik-sense-audit` to make it easier to see.

![screenshot of Qlik Security Audit events in Wazuh](/doc/qlik%20screenshot.png)
