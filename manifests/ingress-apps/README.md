# Deploy Sample Applications

## Overview

This directory contains the Kubernetes manifests used to demonstrate Ingress routing.

Resources include:

* Deployments
* Services
* Ingress
* TLS configuration

## Request Flow

```
Browser
   │
NGINX Ingress
   │
Service
   │
Pod
```

Host-based routing directs traffic to different applications based on the requested hostname.

The local `/etc/hosts` file maps hostnames to the external IP assigned by MetalLB, allowing the applications to be accessed locally over HTTPS.

Deploy all manifests:

```bash
kubectl apply -f .
```

Verify the applications by opening the configured hostnames in your browser.

