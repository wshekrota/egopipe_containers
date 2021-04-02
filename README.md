## Building containers to run testing for egopipe application

```
* cd to app directory
* docker build . 
```

### Copies necessary files in place and starts app

Test env use a vm to run gitlab so the filebeat shipper is running there. To 
establish a network connection from that vm to the logstash container listening
the following route is needed.
route add -net 172.17.0.0 netmask 255.255.0.0 gw 192.168.1.45
where 172.17 networks are containers 
and 192.168.1.45 is my laptop

### Topography

GItlab/Filebeat(vm) -> logstash/egopipe(container) -> Elasticsearch(container) <- Kibana(container)
