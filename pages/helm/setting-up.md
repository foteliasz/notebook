# Setting up Kubernetes on Raspberry Pi

## Selected technologies

Selected technologies for this project

| Area         | Selection                       |
|--------------|---------------------------------|
| Hardware     | [Raspberry Pi 4][RASP]          |
| OS           | [Ubuntu Server for ARM][UBUNTU] |
| K8s platform | [minikube][MINIKUBE]            |

## Prepare Raspberry Pi

1. Install Ubuntu Server on Raspberry Pi. Instructions can be found in [official Ubuntu documentation][UBU-ON-RASP].

2. Connect to Ubuntu server.

    ```bash
    ssh [username]@[host]
    ```

## Install Docker

Detailed instructions can be found in [official Docker documentation][DOCKER-INST]. <br> **TL;DR** version below.

1. Download Docker installation script.

    | Option | Reason |
    |--------|--------|
    | -f, --fail | (HTTP) Fail fast with no output at all on server errors. <br> This is useful to enable scripts and users to better deal with failed attempts. |
    | -s, --silent | Silent or quiet mode. Do not show progress meter or error messages. <br> Makes Curl mute. It will still output the data you ask for, <br> potentially even to the terminal/stdout unless you redirect it. |
    | -S, --show-error | When used with -s, --silent, it makes curl show an error message if it fails. |
    | -L, --location | (HTTP) If the server reports that the requested page has moved to <br> a different location (indicated with a Location: header and a 3xx response code), <br> this option will make curl redo the request on the new place. |
    | -o, --output [file] | Write output to [file] instead of stdout. |
  
    ```bash
    curl -fsSL https://get.docker.com -o get-docker.sh
    ```

2. Execute downloaded script

    ```bash
    sudo sh get-docker.sh
    ```

## Install minikube

1. Download minikube

    | Option | Reason |
    |--------|--------|
    | -L, --location | (HTTP) If the server reports that the requested page has moved to <br> a different location (indicated with a Location: header and a 3xx response code), <br> this option will make curl redo the request on the new place. |
    | -O, --remote-name | Write output to a local file named like the remote file we get. |

    ```bash
    curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-arm64
    ```

2. Install minikube

    ```bash
    sudo install minikube-linux-arm64 /usr/local/bin/minikube
    ```

3. Add current user to docker group

    | Option | Reason |
    |--------|--------|
    | -a, --append | Add the user to the supplementary group(s). Use only with the -G option. |
    | -G, --groups | A list of supplementary groups which the user is also a member of. |

    ```bash
    sudo usermod -aG docker $USER && newgrp docker
    ```

4. Start minikube

    ```bash
    minikube start
    ```

5. Create an alias for convenience

    ```bash
    alias kubectl="minikube kubectl --"
    ```


[RASP]: https://www.raspberrypi.com/products/raspberry-pi-4-model-b/?variant=raspberry-pi-4-model-b-8gb
[UBUNTU]: https://ubuntu.com/download/server/arm
[MINIKUBE]: https://minikube.sigs.k8s.io/docs/start/
[UBU-ON-RASP]: https://ubuntu.com/tutorials/how-to-install-ubuntu-on-your-raspberry-pi
[DOCKER-INST]: https://docs.docker.com/engine/install/ubuntu/#install-using-the-convenience-script
