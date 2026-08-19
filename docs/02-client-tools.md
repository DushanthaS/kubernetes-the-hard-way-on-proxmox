# Installing the Client Tools

In this lab you will install the command line utilities required to complete this tutorial: [cfssl](https://github.com/cloudflare/cfssl), [cfssljson](https://github.com/cloudflare/cfssl), and [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl).

## Install CFSSL

The `cfssl` and `cfssljson` command line utilities will be used to provision a [PKI Infrastructure](https://en.wikipedia.org/wiki/Public_key_infrastructure) and generate TLS certificates.

On the **gateway-01** VM, download and install `cfssl` and `cfssljson`:

```bash
  wget -q --show-progress --https-only --timestamping https://github.com/cloudflare/cfssl/releases/download/v1.6.5/cfssl_1.6.5_linux_amd64 -O cfssl
  wget -q --show-progress --https-only --timestamping https://github.com/cloudflare/cfssl/releases/download/v1.6.5/cfssljson_1.6.5_linux_amd64  -O cfssljson
```

```bash
chmod +x cfssl cfssljson
```

```bash
sudo mv cfssl cfssljson /usr/local/bin/
```

### Verification

Verify `cfssl` and `cfssljson` version 1.3.4 or higher is installed:

```bash
cfssl version
```

> Output:

```bash
Version: 1.3.4
Revision: dev
Runtime: go1.13
```

```bash
cfssljson --version
```

> Output:

```bash
Version: 1.3.4
Revision: dev
Runtime: go1.13
```

## Install kubectl

The `kubectl` command line utility is used to interact with the Kubernetes API Server. On the **gateway-01** VM, download and install `kubectl` from the official release binaries:

```bash
wget https://dl.k8s.io/release/v1.36.3/bin/linux/amd64/kubectl
```

```bash
chmod +x kubectl
```

```bash
sudo mv kubectl /usr/local/bin/
```

### Verification install

Verify `kubectl` version 1.15.3 or higher is installed:

```bash
kubectl version --client
```

> Output:

```bash
Client Version: v1.36.3
Kustomize Version: v5.8.1

```

Next: [Provisioning Compute Resources](03-compute-resources.md)
