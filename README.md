# ElasticStack
Run syslog-ng, filebeat, logstash, elasticsearch and kibana


SYSLOG_NG:

1- Run below command which within syslog-ng directory to create docker container:

docker-compose up -d --build

2- Modify syslog-ng.conf file under /syslog-ng/config/ to specify Source and Destination:
## we are saving syslogs to a Log file which will be consumed by filebeat, logstash, elasticsearch and kibana.


