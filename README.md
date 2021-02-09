# Migrate Data From Standalone Redis to Redis Cluster

[Migrate Data From Standalone Redis to Redis Cluster](https://medium.com/better-programming/migrate-from-standalone-redis-to-redis-cluster-f45b219330a3)

## 1_Set Up Redis and Redis Cluster

```bash

docker run -p 6379:6379 redis
docker run -p 7000-7005:7000-7005 grokzen/redis-cluster:latest

```

## 2_Envoy Setup for Migration

[envoy.yaml](envoy.yaml)

[Dockerfile](Dockerfile)

```bash

docker build -t redis-envoy-proxy .
docker run -p 1936:1936 -p 9091:9091 redis-envoy-proxy

```

I ran Redis and Redis cluster before Envoy.
I cannot set value via Envoy following this error.

```bash

127.0.0.1:9091> get a
(error) no upstream host

```
