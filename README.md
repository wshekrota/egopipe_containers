## Building containers to run testing for egopipe application

---
* cd to app directory
* docker build . 
---

### Copies necessary files in place and starts app

Test env for me uses a vm to run gitlab, the filebeat shipper is running there also. To 
establish a network connection from that vm to the logstash container listening
the following route is needed.

#### route add -net 172.17.0.0 netmask 255.255.0.0 gw 192.168.1.45

where 172.17 networks are containers 
This network is the norm for containers but you can check using 'docker inspect' command.
In my case I started them in order elastic/logstash/kibana so I would know the ips are 0.2 and 0.3 
respectively. You'll know quick enough when you try the api interface

and 192.168.1.45 is my laptop

### Topography

Gitlab/Filebeat(vm) -> logstash/egopipe(container) -> Elasticsearch(container) <- Kibana(container)
