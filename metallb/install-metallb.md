# Install MetalLB

## Overview

MetalLB provides LoadBalancer functionality for bare-metal Kubernetes clusters. Unlike cloud providers, bare-metal environments do not automatically assign external IP addresses to Services.

## Installation

Install MetalLB using Helm in the `metallb-system` namespace.

After installation, verify that the controller and speaker pods are running.

## Why MetalLB?

MetalLB:

* Assigns external IP addresses
* Supports Layer 2 networking
* Enables LoadBalancer Services on bare-metal clusters

Without MetalLB, Services of type `LoadBalancer` remain in the `Pending` state.

The next step is configuring the IP address pool.
