**K3s + MetalLB + NGINX Ingress Lab**  
This project demonstrates how to build an ingress-based application routing setup on a K3s Kubernetes cluster using MetalLB as a load balancer and NGINX Ingress Controller for HTTPS routing.

The lab exposes multiple services through a single ingress controller using path-based routing and TLS termination.

This repository is structured as a step-by-step learning tutorial that can be reproduced in a local lab environment.

**Architecture Overview**  
The cluster runs on a VMware virtual machine using K3s.

MetalLB provides LoadBalancer functionality for bare-metal Kubernetes.  
Traffic flow:  
Client → MetalLB → NGINX Ingress → Backend Services

See the full diagram:  
architecture/architecture-diagram.md

**Technologies Used**   
Kubernetes distribution: **K3s**  
Load balancer: **MetalLB (Layer2 mode)**  
Ingress controller: **NGINX Ingress**
Virtualization: **VMware** 
TLS: **Self-signed wildcard certificate**  
Applications: **Nginx + Httpbin**  

**Project Goals**  
This lab demonstrates:

* Deploying K3s in a VM environment  
* Disabling default K3s networking components  
* Installing MetalLB with Helm  
* Installing NGINX Ingress Controller  
* Path-based routing  
* TLS termination with self-signed certificates  
* Custom error pages  
* Multiple backend services behind one ingress  

**Deployment Steps**
 1. Disable default K3s components  
 2. Install MetalLB  
 3. Configure MetalLB  
 4. Install NGINX Ingress Controller  
 5. Generate TLS certificates  
 6. Deploy sample applications  
 7. Access applications using HTTPS  

##  Table of Contents

*   [Step 1: Disable default K3s Components](k3s/disable-default-components.md)
*   [Step 2: Install & Configure MetalLB](metallb/install-metallb.md)
*   [Step 3: Deploy NGINX Ingress Controller](ingress-nginx/install-ingress-nginx.md)
*   [Step 4: Generate TLS Wildcard Credentials](certs/generate-selfsigned-cert.md)
*   [Step 5: Apply Deployments and Ingress Rules](manifests/ingress-apps/README.md)

**Repository Structure**  
k3s-ingress-metallb-lab  
│  
├── architecture  
├── k3s  
├── metallb  
├── ingress-nginx  
├── manifests  
└── certs  

