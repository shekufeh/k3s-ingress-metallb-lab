# Install NGINX Ingress Controller

## Overview

The NGINX Ingress Controller manages incoming HTTP and HTTPS traffic and routes requests to the appropriate Kubernetes Services.

## Installation

Deploy the controller using Helm with the provided `values.yaml`.

The controller Service is configured as `LoadBalancer`, allowing MetalLB to assign an external IP.

## Why a LoadBalancer Service?

The LoadBalancer Service acts as the cluster's entry point. MetalLB assigns an external IP, enabling clients outside the cluster to reach the Ingress Controller.

Verify the installation:

```bash
kubectl get svc -n ingress-nginx
```

The Service should receive an external IP from MetalLB.

