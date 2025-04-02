# check_apcenvmgr
nagios check for ambient temperature on SNMP-enabled APC AP9340 Environmental Manager

Refer to embedded documentation in script for usage details

# Requirements
perl, snmpget on nagios server

# Configuration
You will need a section in the services.cfg file on the nagios server that looks similar to the following.
```
      # Define a service to check the APC UPS
      # Parameters are SNMP community name
      define service {
              use                             generic-service
              hostgroup_name                  all_apcenvmgr
              service_description             APC Env Mgr
              check_command                   check_apcenvmgr!public
              }
```

You will also need a command definition similar to the following in commands.cfg on the nagios server
```
      # 'check_apcenvmgr' command definition
      # parameters are -H hostname -C snmp_community
      define command{
              command_name    check_apcenvmgr
              command_line    $USER1$/check_apcenvmgr -H $HOSTADDRESS$ -C $ARG1$
              }
```

# Sample Output 
```
APC EnvMgr OK - sensor 1 (front of rack) temperature 19.2C, sensor 2 (rear of rack) temperature 19.3C
```

