# Notebook

## Environment enablement

Start Docker desktop on Mac

```bash
open -a Docker
```

Starting minikube

```bash
minikube start
```

## Setup Docker dummies

### Dummy A

### Dummy B

Build image

```bash
docker build --tag woto/dummies/dummy-b "./dummies/DotnetDummies/Dummies.DummyB"
```

Run image

```bash
docker run -d -p 127.0.0.1:8101:80 --restart=unless-stopped woto/dummies/dummy-b
```

### Dummy C

```bash
docker build --tag woto/dummies/dummy-c "./dummies/DotnetDummies/Dummies.DummyC"
```

Run image

```bash
docker run -d -p 127.0.0.1:8103:80 --restart=unless-stopped woto/dummies/dummy-c
```

https://localhost:49153/weatherforecast
