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

Detailed instructions can be found in [official Docker documentation][DOCKER-INST].\
**TL;DR** version below.

1. Download Docker installation script.

    <details>
    <summary>Used curl options explained</summary>

    | Option | Reason |
    |--------|--------|
    | -f, --fail | (HTTP) Fail fast with no output at all on server errors. This is useful to enable scripts and users to better deal with failed attempts. |
    | -s, --silent | Silent or quiet mode. Do not show progress meter or error messages. Makes Curl mute. It will still output the data you ask for, potentially even to the terminal/stdout unless you redirect it. |
    | -S, --show-error | When used with -s, --silent, it makes curl show an error message if it fails. |
    | -L, --location | (HTTP) If the server reports that the requested page has moved to a different location (indicated with a Location: header and a 3xx response code), this option will make curl redo the request on the new place. |
    | -o, --output [file] | Write output to [file] instead of stdout. |

    </details> 

    ```bash
    curl -fsSL https://get.docker.com -o get-docker.sh
    ```

2. Execute downloaded script

    ```bash
    sudo sh get-docker.sh
    ```

## Install minikube

1. Download minikube

    <details>
    <summary>Used curl options explained</summary>

    | Option | Reason |
    |--------|--------|
    | -L, --location | (HTTP) If the server reports that the requested page has moved to a different location (indicated with a Location: header and a 3xx response code), this option will make curl redo the request on the new place. |
    | -O, --remote-name | Write output to a local file named like the remote file we get. |

    </details> 

    ```bash
    curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-arm64
    ```

2. Install minikube

    ```bash
    sudo install minikube-linux-arm64 /usr/local/bin/minikube
    ```

3. Add current user to docker group

    <details>
    <summary>Used usermod options explained</summary>

    | Option | Reason |
    |--------|--------|
    | -a, --append | Add the user to the supplementary group(s). Use only with the -G option. |
    | -G, --groups | A list of supplementary groups which the user is also a member of. |

    </details> 

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

## Install helm

Detailed instructions can be found in [official Helm documentation][HELM-INST].\
**TL;DR** version below.

1. Download Helm

    ```bash
    wget https://get.helm.sh/helm-v3.11.1-linux-arm64.tar.gz
    ```

2. Untar it

    <details>
    <summary>Used tar options explained</summary>

    | Option | Reason |
    |--------|--------|
    | -z, --gzip, --gunzip | This option tells tar to read or write archives through gzip, allowing tar to directly operate on several kinds of compressed archives transparently. This option should be used, for example, when operating on files with the extension .tar.gz. |
    | -x, --extract, --get | Extract files from an archive. |
    | -v, --verbose | Operate verbosely. |
    | -f, --file | Use archive file (or device) ARCHIVE. |

    </details> 

    ```bash
    tar -zxvf helm-v3.11.1-linux-arm64.tar.gz
    ```

3. Move unpacked binary to its desired destination

    ```bash
    sudo mv linux-arm64/helm /usr/local/bin/helm
    ```

[RASP]: https://www.raspberrypi.com/products/raspberry-pi-4-model-b/?variant=raspberry-pi-4-model-b-8gb
[UBUNTU]: https://ubuntu.com/download/server/arm
[MINIKUBE]: https://minikube.sigs.k8s.io/docs/start/
[UBU-ON-RASP]: https://ubuntu.com/tutorials/how-to-install-ubuntu-on-your-raspberry-pi
[DOCKER-INST]: https://docs.docker.com/engine/install/ubuntu/#install-using-the-convenience-script
[HELM-INST]: https://helm.sh/docs/intro/install/
