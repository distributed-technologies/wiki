<img src="images/Energinet-logo.png" width="250" style="margin-bottom: 3%">

# Mission statement

The goal of the **SCCP platform** (working name) is to create a standard platform based on open source components that can be used to host critical software systems with a number of plugable core features. 

### Cornerstones
- Declaratively defined
- Cloud agnostic
- Trusted execution


## Declaratively defined

The goal is that everything in a running environment should be defined in code and based on repository as the source of truth. This ensures there is a clear documentation on what is running on the platform, and who has performed changes to the platform.

## Cloud agnostic

The platform must be able to be run both locally and on cloud vendors, and on a broad base of hardware in the case of world events where specific hardware might be unavailable or the platform has to be reinitialized from scratch.

## Trusted execution

There is a clear goal to enable Trusted Execution Environment on the platform, as to ensure that only sanctioned code can be executed, since the validity of data on the platform is of higher importance than the secrecy.

TEE with TPM modules will enable the platform to fuse hardware and software. In its essence, this means that the hardware will not run any software that does not have the correct digital signatures and the software will not run on any hardware that does not have the correct digital signature without it being visible that it is not trusted.



# Architecture
The platform are a stripped down Linux kernel with only the essentials to start a Kubernetes cluster, pre-configured with all relevant settings. If one whishes to update a node in the cluster a new boot image with configuration would be created and signed, and the node would reboot.
To manage Kubernetes a GitOps operator will continually monitor both the environment and the repository to ensure that the environment are as specified.

The environment itself should be defined based on a single repository in the near future, describing the infrastructure provisioning, enabled system services, and referring hosted applications environment repositories.

## Roadmap
There is still a long way to go before all the features required are implemented in its base form.

- [x] Monitoring 
- [x] Ingress 
- [x] Load Balancer 
- [x] Distributed File System 
- [ ] TEE
- [ ] Single repository deployment
- [ ] GitOps based hardware provisioning
- [ ] IPv6 support
- [ ] PKI infrastructure

## Features

The platform will include a large number of base features based on existing open source software and a default configuration to easily and quickly be able to define a secure cluster with all the required support functionality like logging, metrics, tracing and so on.

A platform team should be able to manage this with minimal support, and enable application owners to each exists on a cluster as their own tenant with the underlying utilities.



## Current features
All technologies that are used to build the SCCP are open source.

### GitOps Operator - [ArgoCD](https://github.com/argoproj/argo-cd/) 
ArgoCD is used as the GitOps tool that continuously delivers changes to the platform based on pull request changes.

### Logging - [Loki](https://github.com/grafana/loki)
Loki is used for log aggregation.

### Metrics - [Prometheus](https://github.com/prometheus/prometheus)
Prometheus is used as the monitoring time-series database, that continuously scrapes metrics from all containers that expose them.

### Long term metrics - [Thanos](https://thanos.io/)
Thanos enables long term storage of the metrics collected by prometheus.

### Distributed file system - Ceph
Ceph is used through an [open-source Rook operator](https://github.com/rook/rook) as a distributed persistent storage, handling jobs like replication to avoid data loss at machine failure. 

### Visualization - [Grafana](https://github.com/grafana/grafana)
Grafana is used as the monitoring visualization tool, where dashboards provide insights into the metrics.

### LoadBalancer - [Metallb](https://github.com/metallb/metallb)
MetalLB is used as the software load balancer delegating IPs to services that need a static IP. 

### Ingress controller - [Traefik](https://github.com/traefik/traefik)
Traefik is used as an ingress controller handling ingress events to route communication.
