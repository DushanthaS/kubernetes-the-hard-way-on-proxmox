# Installing the Client Tools

In this lab you will install the command line utilities required to complete this tutorial: [cfssl](https://github.com/cloudflare/cfssl), [cfssljson](https://github.com/cloudflare/cfssl), and [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl).

## Install CFSSL

The `cfssl` and `cfssljson` command line utilities will be used to provision a [PKI Infrastructure](https://en.wikipedia.org/wiki/Public_key_infrastructure) and generate TLS certificates.

On the **gateway-01** VM, download and install `cfssl` and `cfssljson`:

```bash
  wget -q --show-progress --https-only --timestamping \
    https://github.com/cloudflare/cfssl/releases/download/v1.6.5/cfssl_1.6.5_linux_amd64 \
    https://github.com/cloudflare/cfssl/releases/download/v1.6.5/cfssljson_1.6.5_linux_amd64 \
    https://github.com/cloudflare/cfssl/releases/download/v1.6.5/cfssl_1.6.5_checksums.txt
```

These binaries generate the cluster CA, so verify them before installing:

```bash
sha256sum -c --ignore-missing cfssl_1.6.5_checksums.txt
```

> Output:

```bash
cfssl_1.6.5_linux_amd64: OK
cfssljson_1.6.5_linux_amd64: OK
```

```bash
chmod +x cfssl_1.6.5_linux_amd64 cfssljson_1.6.5_linux_amd64
```

```bash
sudo mv cfssl_1.6.5_linux_amd64 /usr/local/bin/cfssl
sudo mv cfssljson_1.6.5_linux_amd64 /usr/local/bin/cfssljson
```

### Verification

Verify `cfssl` and `cfssljson` version 1.6.5 or higher is installed:

```bash
cfssl version
```

> Output:

```bash
Version: 1.6.5
Runtime: go1.22.0
```

```bash
cfssljson --version
```

> Output:

```bash
Version: 1.6.5
Runtime: go1.22.0
```

## Install kubectl

The `kubectl` command line utility is used to interact with the Kubernetes API Server. On the **gateway-01** VM, download and install `kubectl` from the official release binaries:

```bash
wget https://dl.k8s.io/release/v1.36.3/bin/linux/amd64/kubectl
wget https://dl.k8s.io/release/v1.36.3/bin/linux/amd64/kubectl.sha256
```

This binary administers the cluster, so verify it before installing:

```bash
echo "$(cat kubectl.sha256)  kubectl" | sha256sum -c -
```

> Output:

```bash
kubectl: OK
```

```bash
chmod +x kubectl
```

```bash
sudo mv kubectl /usr/local/bin/
```

### Verification install

Verify `kubectl` version 1.36.3 or higher is installed:

```bash
kubectl version --client
```

> Output:

```bash
Client Version: v1.36.3
Kustomize Version: v5.8.1

```

Next: [Provisioning Compute Resources](03-compute-resources.md)
