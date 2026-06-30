# Generate Self-Signed Wildcard Certificate

## Overview

This project secures Ingress resources using a self-signed TLS certificate.

The certificate is stored as a Kubernetes TLS Secret and referenced by the Ingress resource.

## Why?

HTTPS encrypts communication between clients and applications.

Although self-signed certificates are not trusted by browsers, they are ideal for learning and local lab environments.

After creating the certificate, create the TLS Secret before deploying the Ingress resources.

###steps

openssl req -x509 -nodes -days 365 \
-newkey rsa:2048 \
-keyout tls.key \
-out tls.crt \
-subj "/CN=*.lab.local/O=lab"

kubectl create secret tls lab-wildcard-tls \
--key tls.key \
--cert tls.crt \
-n ingress-app
