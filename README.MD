# RUN Application

```bash
# Terminal-1 
cd infrastructure/docker-compose
docker compose -f postgres.yml up
```
```bash
cd infrastructure/docker-compose
docker compose -f common.yml -f zookeeper.yml up
```
```bash
cd infrastructure/docker-compose
echo ruok | nc localhost 2181
# Terminal-2
docker compose -f common.yml -f kafka_cluster.yml up
```
```bash
cd infrastructure/docker-compose
# Terminal-3
docker compose -f common.yml -f init_kafka.yml up
# http://localhost:9000/clusters
# add cluster: food-ordering-system-cluster
# Cluster Zookeeper Hosts: zookeeper:2181
```
```bash
# Run Customer service and order service
# Postman
#POST http://localhost:8181/orders 
kcat -C -b localhost:19092 -t payment-request
```