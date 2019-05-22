# zabbix_get_jmx

### Install
```
yum install python34 jq -y
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
### Example zabbix_get_jmx
Test discovery Garbage collector **
```
zabbix_get_jmx --java-gateway-host HOST_WITH_INSTALLED_GW --java-gateway-port 10052 --jmx-server MONITORED_HOST --jmx-port 4447 --jmx-user USER --jmx-pass ZABBIX --new-protocol --key 'jmx.discovery[beans,"*:type=GarbageCollector,name=*"]' | jq '.data[0].value | fromjson | .data'
```
Output:
```
[
  {
    "{#JMXDOMAIN}": "java.lang",
    "{#JMXTYPE}": "GarbageCollector",
    "{#JMXOBJ}": "java.lang:type=GarbageCollector,name=PS MarkSweep",
    "{#JMXNAME}": "PS MarkSweep"
  },
  {
    "{#JMXDOMAIN}": "java.lang",
    "{#JMXTYPE}": "GarbageCollector",
    "{#JMXOBJ}": "java.lang:type=GarbageCollector,name=PS Scavenge",
    "{#JMXNAME}": "PS Scavenge"
  }
]
```

### Usage simple script
Test discovery Garbage collector
```
./zabbix_get_jmx.sh 'jmx.discovery[beans,"*:type=GarbageCollector,name=*"]'
```
Output:
```
[
  {
    "{#JMXDOMAIN}": "java.lang",
    "{#JMXTYPE}": "GarbageCollector",
    "{#JMXOBJ}": "java.lang:type=GarbageCollector,name=PS MarkSweep",
    "{#JMXNAME}": "PS MarkSweep"
  },
  {
    "{#JMXDOMAIN}": "java.lang",
    "{#JMXTYPE}": "GarbageCollector",
    "{#JMXOBJ}": "java.lang:type=GarbageCollector,name=PS Scavenge",
    "{#JMXNAME}": "PS Scavenge"
  }
]
```
[![paypal](https://www.paypalobjects.com/en_US/i/btn/btn_donateCC_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=GEH7YJEBWTFWE&currency_code=USD&source=url)
