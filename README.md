# Learning notebook

## Helm

1. [Instructions](./pages/helm/setting-up.md) for setting up Kubernetes
2. Create simple HTTP application

```json
{ "name": "dummy", "version": "1.0.0" }
```

```bash
docker pull ubuntu:22.04

docker run -dt --name dev-box ubuntu:22.04

docker exec -it dev-box /bin/bash

mkdir /www
cd /www
echo '{ "name": "dummy", "version": "1.0.0" }'

```
