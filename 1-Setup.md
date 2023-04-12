# Project Setup on LKE (Managed Kubernetes on Akamai Linode)

##0 - Prerequisites

- Linode account
- Domain name (to point to Linode DNS)
- Local CLI tools for k8s cluster management (kubectl, helm)

##1 - LKE Setup

Create a Kubernetes cluster in Linode with latest Kubernetes version (1.25 at the time of writing) with a single shared Linode 2GB node. This configuration will suffice for this test setup.