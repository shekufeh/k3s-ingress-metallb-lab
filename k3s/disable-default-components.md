# Disable Default K3s Components

## Overview

K3s includes Traefik and ServiceLB by default. Since this project uses **NGINX Ingress Controller** and **MetalLB**, both components must be disabled to prevent conflicts.

## Configuration

Update the K3s service configuration and disable:

* `traefik`
* `servicelb`

Restart the K3s service after saving the changes.

## Why?

* Traefik is replaced by NGINX Ingress Controller.
* ServiceLB is replaced by MetalLB.
* Only one Ingress Controller and one LoadBalancer implementation should manage cluster traffic.

## Verification

Verify that no Traefik or `svclb-*` pods exist:

```bash
kubectl get pods -A
```

The cluster is now ready for MetalLB installation.

