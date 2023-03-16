# Learning notebook

## Helm

1. [Instructions](./pages/helm/a-setting-up.md) for setting up Kubernetes.
2. [Instructions](./pages/helm/b-docker-hub-apps.md) for creating simple HTTP application in two versions.

Create a resource group

```PowerShell
az group create `
    --name helm-evaluation `
    --location westeurope
```

Create an AKS cluster

```PowerShell
az aks create `
    --resource-group helm-evaluation `
    --name helm-evaluation-aks `
    --enable-managed-identity `
    --node-count 1 `
    --enable-addons monitoring `
    --enable-msi-auth-for-monitoring `
    --generate-ssh-keys
```
