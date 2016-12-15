# node-exporter-with-consul

This project is based on [node-exporter](https://github.com/prometheus/node_exporter) and [consul](https://github.com/hashicorp/consul).


## What I've done
When node-exporter started, it would register to consul on local machine.

```
service_id: ip
service_name: nodes
service_port: 9100
```

You can change it at [here](https://github.com/liujiawinds/node-exporter-with-consul/blob/master/node_exporter.go#L213).


## tips

1. deregister service
    curl http://localhost:8500/v1/agent/service/deregister/SERVICEID

2. query services registed on local agent
    curl http://localhost:8500/v1/agent/services?pretty

3. query all services in cluster
    curl http://localhost:8500/v1/catalog/services?pretty

4. start consul agent as a server role and join a cluster
    consul agent -server --data-dir=/services/data/consul/ --join CLUSTER_MEMBER_IP&
