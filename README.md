# zabbix_get_jmx

### Install
```
yum install python34
```
```
wget https://raw.githubusercontent.com/hermanekt/zabbix_get_jmx/master/zabbix_get_jmx -P /usr/bin/
```
```
chmod +x /usr/bin/zabbix_get_jmx
```

### Usage
```
zabbix_get_jmx --help
```
```
usage: zabbix_get_jmx [-h] [--java-gateway-host JAVA_GATEWAY_HOST]
                      [--java-gateway-port JAVA_GATEWAY_PORT]
                      [--jmx-server JMX_SERVER] [--jmx-port JMX_PORT]
                      [--key KEY] [--jmx-user JMX_USER] [--jmx-pass JMX_PASS]
                      [--new-protocol]

optional arguments:
  -h, --help            show this help message and exit
  --java-gateway-host JAVA_GATEWAY_HOST
  --java-gateway-port JAVA_GATEWAY_PORT
  --jmx-server JMX_SERVER
  --jmx-port JMX_PORT
  --key KEY
  --jmx-user JMX_USER
  --jmx-pass JMX_PASS
  --new-protocol
```

### Usage easy script
** Test discovery Garbage collector **
./zabbix_get_jmx.sh 'jmx.discovery[beans,"*:type=GarbageCollector,name=*"]'

